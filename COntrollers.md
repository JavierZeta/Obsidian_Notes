"""Bio_AUSFEC_v2: corrected bio-plausible AU-SFEC.

  

This version fixes the instability in the first Bio_AUSFEC draft.

  

Main fixes

----------

1. Old SFEC interpreted tau as a decay RATE:

r = (1 - dt*tau) r + s_delay

The broken draft interpreted tau as a time constant:

r = exp(-dt/tau) r

That was much too leaky for tau=0.1.

  

2. Old SFEC used threshold ~= diag(O), not 0.5*diag(O):

Thr = diag(O_fast)/2

Thr *= 2

So this version defaults to threshold_curvature=1.0.

  

3. The first update no longer injects a huge artificial input current from

b_prev=0 to b_now. The first bias is latched, so db=0 on the first step.

  

4. Parallel spikes are capped by default in the runner. This module supports both

capped and uncapped parallel thresholding.

  

This is more bio-plausible than the precise spiking solver because voltages are

causal dynamical states, spikes are delayed, and resets are recurrent currents.

It is intentionally less exact than greedy posterior matching.

"""

  

from __future__ import annotations

  

import numpy as np

  
  

# ---------------------------------------------------------------------

# Helpers

# ---------------------------------------------------------------------

  
  

def as_precision(x, dim: int) -> np.ndarray:

x = np.asarray(x, dtype=float)

if x.ndim == 0:

return float(x) * np.eye(dim)

if x.ndim == 1:

if x.size != dim:

raise ValueError(f"Diagonal precision has length {x.size}, expected {dim}.")

return np.diag(x)

if x.shape != (dim, dim):

raise ValueError(f"Precision has shape {x.shape}, expected {(dim, dim)}.")

return x

  
  

def diag(P: np.ndarray) -> np.ndarray:

return np.diag(P).copy()

  
  

def coerce_matrix(M, rows: int | None = None, cols: int | None = None) -> np.ndarray:

M = np.asarray(M, dtype=float)

if M.ndim == 1:

M = M[:, None]

if rows is not None and M.shape[0] != rows:

raise ValueError(f"Matrix has {M.shape[0]} rows, expected {rows}.")

if cols is not None and M.shape[1] != cols:

raise ValueError(f"Matrix has {M.shape[1]} cols, expected {cols}.")

return M

  
  

def balanced_decoder(

dim: int,

N: int | None = None,

scale: float = 4.0,

rng: np.random.Generator | None = None,

random_std: float = 1.0,

shuffle: bool = True,

) -> np.ndarray:

if rng is None:

rng = np.random.default_rng()

if N is None:

N = max(16 * dim, 64)

N = int(N)

if N < 2 * dim:

raise ValueError("Need at least 2*dim neurons.")

  

D = np.zeros((dim, N), dtype=float)

for k in range(dim):

D[k, 2 * k] = 1.0

D[k, 2 * k + 1] = -1.0

if N > 2 * dim:

D[:, 2 * dim :] = rng.normal(0.0, random_std, size=(dim, N - 2 * dim))

if shuffle:

D = D[:, rng.permutation(N)]

return (scale / float(N)) * D

  
  

def rk4_discrete_linear(A: np.ndarray, B: np.ndarray, dt: float):

n = A.shape[0]

I = np.eye(n)

dt = float(dt)

A2 = A @ A

A3 = A2 @ A

A4 = A3 @ A

Phi = I + dt * A + (dt**2 / 2.0) * A2 + (dt**3 / 6.0) * A3 + (dt**4 / 24.0) * A4

Gamma = dt * B + (dt**2 / 2.0) * (A @ B) + (dt**3 / 6.0) * (A2 @ B) + (dt**4 / 24.0) * (A3 @ B)

return Phi, Gamma

  
  

# ---------------------------------------------------------------------

# Bio quadratic population

# ---------------------------------------------------------------------

  
  

class BioQuadraticPopulation:

"""Old-SFEC-style recurrent spiking population for a quadratic factor.

  

Represents mu = D r and tracks a quadratic posterior with bias b and curvature M.

  

Voltage dynamics:

s_delay = delayed spikes

r = (1 - dt*tau_r) r + s_delay

v = leak_v*v + D.T@(b_t - b_{t-1})

+ dt*slow_gain*D.T@(b_t - M mu)

- reset_gain*(D.T M D)@s_delay

+ noise

s_i = 1 if v_i > threshold_i

  

Threshold:

threshold_i = threshold_curvature * O_ii + beta*(r_i+0.5) + adaptation_i

  

For exact SFEC coordinate descent, threshold_curvature would be 0.5. Your old

working SFEC effectively used 1.0, which is less trigger-happy and more stable

for parallel spikes.

"""

  

def __init__(

self,

D: np.ndarray,

beta: float = 0.0,

tau_r: float = 0.1,

rate_decay: bool = True,

lambda_adapt: float = 0.0,

voltage_noise: float = 0.0,

voltage_leak: float = 0.0,

slow_current_gain: float = 1.0,

reset_gain: float = 1.0,

threshold_curvature: float = 1.0,

max_parallel_spikes: int | None = 16,

spike_delay_steps: int = 1,

v_clip: float | None = None,

rng: np.random.Generator | None = None,

):

self.D = np.asarray(D, dtype=float)

if self.D.ndim != 2:

raise ValueError("D must be 2D.")

self.dim, self.N = self.D.shape

  

self.beta = float(beta)

self.tau_r = float(tau_r)

self.rate_decay = bool(rate_decay)

self.lambda_adapt = float(lambda_adapt)

self.voltage_noise = float(voltage_noise)

self.voltage_leak = float(voltage_leak)

self.slow_current_gain = float(slow_current_gain)

self.reset_gain = float(reset_gain)

self.threshold_curvature = float(threshold_curvature)

self.max_parallel_spikes = max_parallel_spikes

self.spike_delay_steps = max(1, int(spike_delay_steps))

self.v_clip = v_clip

self.rng = np.random.default_rng() if rng is None else rng

  

self.r = np.zeros(self.N)

self.v = np.zeros(self.N)

self.s = np.zeros(self.N)

self.r_adapt = np.zeros(self.N)

self.alive = np.ones(self.N)

self.mu = np.zeros(self.dim)

self.s_list = [np.zeros(self.N) for _ in range(self.spike_delay_steps)]

  

self.b = np.zeros(self.dim)

self.b_prev = np.zeros(self.dim)

self.M = np.eye(self.dim)

self.O_fast = np.zeros((self.N, self.N))

self.O_diag = np.zeros(self.N)

self.threshold = np.zeros(self.N)

self.b_initialized = False

self.last_spike_count = 0

self.last_above_count = 0

self.last_v_max = 0.0

  

def reset(self, mu0: np.ndarray | None = None, r0: np.ndarray | None = None):

if r0 is not None:

self.r = np.asarray(r0, dtype=float).reshape(self.N)

elif mu0 is not None:

self.r = np.linalg.pinv(self.D) @ np.asarray(mu0, dtype=float).reshape(self.dim)

else:

self.r.fill(0.0)

self.v.fill(0.0)

self.s.fill(0.0)

self.r_adapt.fill(0.0)

self.mu = self.D @ self.r

self.s_list = [np.zeros(self.N) for _ in range(self.spike_delay_steps)]

self.b.fill(0.0)

self.b_prev.fill(0.0)

self.b_initialized = False

self.last_spike_count = 0

self.last_above_count = 0

self.last_v_max = 0.0

  

def kill_fraction(self, fraction: float = 0.25):

fraction = float(np.clip(fraction, 0.0, 1.0))

self.alive[:] = 1.0

self.alive[: int(round(fraction * self.N))] = 0.0

  

def set_voltage_noise(self, noise: float):

self.voltage_noise = float(noise)

  

def _rate_update(self, s_delay: np.ndarray, dt: float):

if self.rate_decay:

# Match old SFEC: r = (1 - dt*tau) r + s_delay.

leak = max(0.0, 1.0 - float(dt) * self.tau_r)

self.r *= leak

self.r += s_delay

self.mu = self.D @ self.r

  

def _adapt_update(self):

if self.lambda_adapt > 0.0:

self.r_adapt = (1.0 - self.lambda_adapt) * self.r_adapt + self.s

else:

self.r_adapt.fill(0.0)

  

def update(self, b: np.ndarray, M: np.ndarray, dt: float):

b = np.asarray(b, dtype=float).reshape(self.dim)

M = np.asarray(M, dtype=float).reshape(self.dim, self.dim)

dt = float(dt)

  

s_delay = self.s_list.pop(0)

self._rate_update(s_delay, dt)

  

# Latch first bias to avoid a non-biological huge transient current from b_prev=0.

if not self.b_initialized:

self.b = b.copy()

self.b_prev = b.copy()

self.b_initialized = True

else:

self.b_prev = self.b.copy()

self.b = b.copy()

  

self.M = M

self.O_fast = self.D.T @ self.M @ self.D

self.O_diag = np.diag(self.O_fast).copy()

  

db = self.b - self.b_prev

input_current = self.D.T @ db

gradient_current = self.D.T @ (self.b - self.M @ self.mu)

  

if self.voltage_leak > 0.0:

self.v *= max(0.0, 1.0 - dt * self.voltage_leak)

  

self.v = (

self.v

+ input_current

+ dt * self.slow_current_gain * gradient_current

- self.reset_gain * (self.O_fast @ s_delay)

)

  

if self.voltage_noise > 0.0 and dt > 0.0:

self.v += self.voltage_noise * self.rng.normal(0.0, 1.0, self.N) * np.sqrt(dt)

  

if self.v_clip is not None:

self.v = np.clip(self.v, -float(self.v_clip), float(self.v_clip))

  

self.v *= self.alive

self.last_v_max = float(np.max(self.v)) if self.v.size else 0.0

  

self.threshold = self.threshold_curvature * self.O_diag + self.beta * (self.r + 0.5) + self.r_adapt

  

above = np.where((self.v > self.threshold) & (self.alive > 0.0))[0]

self.last_above_count = int(above.size)

  

if above.size and self.max_parallel_spikes is not None and above.size > int(self.max_parallel_spikes):

margins = self.v[above] - self.threshold[above]

above = above[np.argsort(margins)[-int(self.max_parallel_spikes) :]]

  

self.s = np.zeros(self.N)

if above.size:

self.s[above] = 1.0

  

self._adapt_update()

self.s_list.append(self.s.copy())

self.last_spike_count = int(np.sum(self.s))

return self.mu.copy()

  

def exact_star(self):

return np.linalg.solve(self.M, self.b)

  

def diagnostics(self):

return {

"mu": self.mu.copy(),

"r": self.r.copy(),

"v": self.v.copy(),

"s": self.s.copy(),

"threshold": self.threshold.copy(),

"r_adapt": self.r_adapt.copy(),

"spike_count": int(self.last_spike_count),

"above_count": int(self.last_above_count),

"v_max": float(self.last_v_max),

}

  
  

# ---------------------------------------------------------------------

# Estimator

# ---------------------------------------------------------------------

  
  

class BioEstimatorPopulation:

def __init__(

self,

plant,

D_E=None,

N_E=None,

decoder_scale=4.0,

pi_y=1.0,

pi_w=1.0,

beta_E=0.0,

tau_E=0.1,

rate_decay_E=True,

lambda_adapt_E=0.0,

voltage_noise_E=0.0,

voltage_leak_E=0.0,

slow_current_gain_E=1.0,

reset_gain_E=1.0,

threshold_curvature_E=1.0,

max_parallel_spikes_E=16,

spike_delay_steps_E=1,

v_clip_E=None,

use_rk4_prior=True,

rng=None,

):

self.plant = plant

self.n = int(plant.x_k)

self.m = int(plant.y_k)

self.n_u = int(plant.u_k)

self.A = np.asarray(plant.A_lin, dtype=float)

self.B = coerce_matrix(plant.B_lin, rows=self.n)

self.C = np.asarray(plant.C, dtype=float).reshape(self.m, self.n)

self.use_rk4_prior = bool(use_rk4_prior)

self.rng = np.random.default_rng() if rng is None else rng

  

if D_E is None:

D_E = balanced_decoder(self.n, N=N_E, scale=decoder_scale, rng=self.rng)

self.population = BioQuadraticPopulation(

D=D_E,

beta=beta_E,

tau_r=tau_E,

rate_decay=rate_decay_E,

lambda_adapt=lambda_adapt_E,

voltage_noise=voltage_noise_E,

voltage_leak=voltage_leak_E,

slow_current_gain=slow_current_gain_E,

reset_gain=reset_gain_E,

threshold_curvature=threshold_curvature_E,

max_parallel_spikes=max_parallel_spikes_E,

spike_delay_steps=spike_delay_steps_E,

v_clip=v_clip_E,

rng=self.rng,

)

  

self.pi_y = as_precision(pi_y, self.m)

self.pi_w = as_precision(pi_w, self.n)

self.Phi = np.eye(self.n)

self.Gamma = np.zeros((self.n, self.n_u))

self.mu_E = np.zeros(self.n)

self.mu_prior = np.zeros(self.n)

self.initialized = False

self._reset_diagnostics()

  

def _reset_diagnostics(self):

self.y = np.zeros(self.m)

self.y_hat = np.zeros(self.m)

self.nu_y = np.zeros(self.m)

self.e_y = np.zeros(self.m)

self.e_w = np.zeros(self.n)

self.F_E = 0.0

self.posterior_precision = np.eye(self.n)

self.mu_E_star = np.zeros(self.n)

  

def setup(self, y0=None, mu0=None):

if mu0 is None:

if y0 is None:

mu0 = np.asarray(self.plant.x0_lin, dtype=float).reshape(self.n)

else:

mu0 = np.linalg.lstsq(self.C, np.asarray(y0, dtype=float).reshape(self.m), rcond=None)[0]

self.population.reset(mu0=mu0)

self.mu_E = self.population.mu.copy()

self.mu_prior = self.mu_E.copy()

self.initialized = True

  

def set_precisions(self, pi_y=None, pi_w=None):

if pi_y is not None:

self.pi_y = as_precision(pi_y, self.m)

if pi_w is not None:

self.pi_w = as_precision(pi_w, self.n)

  

def predict_prior(self, dt, u_prev):

u_prev = np.asarray(u_prev, dtype=float).reshape(self.n_u)

if self.use_rk4_prior:

self.Phi, self.Gamma = rk4_discrete_linear(self.A, self.B, dt)

else:

self.Phi = np.eye(self.n) + float(dt) * self.A

self.Gamma = float(dt) * self.B

self.mu_prior = self.Phi @ self.mu_E + self.Gamma @ u_prev

return self.mu_prior.copy()

  

def update(self, y, dt, u_prev=None, pi_y=None, pi_w=None):

y = np.asarray(y, dtype=float).reshape(self.m)

self.set_precisions(pi_y=pi_y, pi_w=pi_w)

if not self.initialized:

self.setup(y0=y)

if u_prev is None:

u_prev = np.zeros(self.n_u)

else:

u_prev = np.asarray(u_prev, dtype=float).reshape(self.n_u)

  

self.predict_prior(dt, u_prev)

M = self.C.T @ self.pi_y @ self.C + self.pi_w

b = self.C.T @ self.pi_y @ y + self.pi_w @ self.mu_prior

self.mu_E = self.population.update(b=b, M=M, dt=dt)

self._update_diagnostics(y, M, b)

return self.mu_E.copy()

  

def _update_diagnostics(self, y, M, b):

self.y = y.copy()

self.y_hat = self.C @ self.mu_E

self.nu_y = y - self.C @ self.mu_prior

self.e_y = y - self.y_hat

self.e_w = self.mu_prior - self.mu_E

self.F_E = self.e_y @ self.pi_y @ self.e_y + self.e_w @ self.pi_w @ self.e_w

self.posterior_precision = M.copy()

self.mu_E_star = np.linalg.solve(M, b)

  

def diagnostics(self):

pop = self.population.diagnostics()

return {

"mu_E": self.mu_E.copy(),

"mu_prior": self.mu_prior.copy(),

"y": self.y.copy(),

"y_hat": self.y_hat.copy(),

"nu_y": self.nu_y.copy(),

"e_y": self.e_y.copy(),

"e_w": self.e_w.copy(),

"F_E": float(self.F_E),

"pi_y": diag(self.pi_y),

"pi_w": diag(self.pi_w),

"posterior_precision": self.posterior_precision.copy(),

"mu_E_star": self.mu_E_star.copy(),

"star_error": self.mu_E - self.mu_E_star,

"spike_count_E": pop["spike_count"],

"above_count_E": pop["above_count"],

"v_max_E": pop["v_max"],

"population": pop,

}

  
  

# ---------------------------------------------------------------------

# Controller

# ---------------------------------------------------------------------

  
  

class BioControllerPopulation:

def __init__(

self,

n,

G=None,

D_C=None,

N_C=None,

decoder_scale=4.0,

pi_x=1.0,

pi_z=4.0,

beta_C=0.0,

tau_C=0.1,

rate_decay_C=True,

lambda_adapt_C=0.0,

voltage_noise_C=0.0,

voltage_leak_C=0.0,

slow_current_gain_C=1.0,

reset_gain_C=1.0,

threshold_curvature_C=1.0,

max_parallel_spikes_C=16,

spike_delay_steps_C=1,

v_clip_C=None,

rng=None,

):

self.n = int(n)

self.G = np.eye(self.n) if G is None else np.asarray(G, dtype=float)

if self.G.ndim != 2 or self.G.shape[1] != self.n:

raise ValueError("G must have shape (p, n).")

self.p = self.G.shape[0]

self.rng = np.random.default_rng() if rng is None else rng

  

if D_C is None:

D_C = balanced_decoder(self.n, N=N_C, scale=decoder_scale, rng=self.rng)

self.population = BioQuadraticPopulation(

D=D_C,

beta=beta_C,

tau_r=tau_C,

rate_decay=rate_decay_C,

lambda_adapt=lambda_adapt_C,

voltage_noise=voltage_noise_C,

voltage_leak=voltage_leak_C,

slow_current_gain=slow_current_gain_C,

reset_gain=reset_gain_C,

threshold_curvature=threshold_curvature_C,

max_parallel_spikes=max_parallel_spikes_C,

spike_delay_steps=spike_delay_steps_C,

v_clip=v_clip_C,

rng=self.rng,

)

  

self.pi_x = as_precision(pi_x, self.n)

self.pi_z = as_precision(pi_z, self.p)

self.mu_C = np.zeros(self.n)

self._reset_diagnostics()

  

def _reset_diagnostics(self):

self.z = np.zeros(self.p)

self.e_x = np.zeros(self.n)

self.e_z = np.zeros(self.p)

self.F_C = 0.0

self.posterior_precision = np.eye(self.n)

self.mu_C_star = np.zeros(self.n)

  

def setup(self, mu0=None):

self.population.reset(mu0=np.zeros(self.n) if mu0 is None else mu0)

self.mu_C = self.population.mu.copy()

  

def set_precisions(self, pi_x=None, pi_z=None):

if pi_x is not None:

self.pi_x = as_precision(pi_x, self.n)

if pi_z is not None:

self.pi_z = as_precision(pi_z, self.p)

  

def update(self, mu_E, z, dt, pi_x=None, pi_z=None):

mu_E = np.asarray(mu_E, dtype=float).reshape(self.n)

z = np.asarray(z, dtype=float).reshape(self.p)

self.set_precisions(pi_x=pi_x, pi_z=pi_z)

M = self.pi_x + self.G.T @ self.pi_z @ self.G

b = self.pi_x @ mu_E + self.G.T @ self.pi_z @ z

self.mu_C = self.population.update(b=b, M=M, dt=dt)

self._update_diagnostics(mu_E, z, M, b)

return self.mu_C.copy()

  

def _update_diagnostics(self, mu_E, z, M, b):

self.z = z.copy()

self.e_x = mu_E - self.mu_C

self.e_z = z - self.G @ self.mu_C

self.F_C = self.e_x @ self.pi_x @ self.e_x + self.e_z @ self.pi_z @ self.e_z

self.posterior_precision = M.copy()

self.mu_C_star = np.linalg.solve(M, b)

  

def diagnostics(self):

pop = self.population.diagnostics()

return {

"mu_C": self.mu_C.copy(),

"z": self.z.copy(),

"e_x": self.e_x.copy(),

"e_z": self.e_z.copy(),

"F_C": float(self.F_C),

"pi_x": diag(self.pi_x),

"pi_z": diag(self.pi_z),

"posterior_precision": self.posterior_precision.copy(),

"mu_C_star": self.mu_C_star.copy(),

"star_error": self.mu_C - self.mu_C_star,

"spike_count_C": pop["spike_count"],

"above_count_C": pop["above_count"],

"v_max_C": pop["v_max"],

"population": pop,

}

  
  

# ---------------------------------------------------------------------

# Action

# ---------------------------------------------------------------------

  
  

class BioActionPopulation:

def __init__(

self,

K,

U=None,

D_u=None,

N_u_pop=None,

decoder_scale=4.0,

pi_u=1.0,

beta_u=0.0,

tau_u=0.02,

rate_decay_u=True,

lambda_adapt_u=0.0,

voltage_noise_u=0.0,

voltage_leak_u=0.0,

slow_current_gain_u=1.0,

reset_gain_u=1.0,

threshold_curvature_u=1.0,

max_parallel_spikes_u=8,

spike_delay_steps_u=1,

v_clip_u=None,

u_min=-np.inf,

u_max=np.inf,

rng=None,

):

self.K = np.asarray(K, dtype=float)

if self.K.ndim == 1:

self.K = self.K[None, :]

self.n_u, self.n = self.K.shape

if U is None:

self.U = np.zeros_like(self.K)

else:

self.U = np.asarray(U, dtype=float)

if self.U.ndim == 1:

self.U = self.U[None, :]

if self.U.shape != self.K.shape:

raise ValueError(f"U has shape {self.U.shape}, expected {self.K.shape}.")

self.rng = np.random.default_rng() if rng is None else rng

  

if D_u is None:

D_u = balanced_decoder(self.n_u, N=N_u_pop, scale=decoder_scale, rng=self.rng)

self.population = BioQuadraticPopulation(

D=D_u,

beta=beta_u,

tau_r=tau_u,

rate_decay=rate_decay_u,

lambda_adapt=lambda_adapt_u,

voltage_noise=voltage_noise_u,

voltage_leak=voltage_leak_u,

slow_current_gain=slow_current_gain_u,

reset_gain=reset_gain_u,

threshold_curvature=threshold_curvature_u,

max_parallel_spikes=max_parallel_spikes_u,

spike_delay_steps=spike_delay_steps_u,

v_clip=v_clip_u,

rng=self.rng,

)

  

self.pi_u = as_precision(pi_u, self.n_u)

self.tau_u = float(tau_u)

self.u_min = np.full(self.n_u, u_min) if np.isscalar(u_min) else np.asarray(u_min, dtype=float)

self.u_max = np.full(self.n_u, u_max) if np.isscalar(u_max) else np.asarray(u_max, dtype=float)

self.mu_u = np.zeros(self.n_u)

self._reset_diagnostics()

  

def _reset_diagnostics(self):

self.target_u = np.zeros(self.n_u)

self.relaxed_target_u = np.zeros(self.n_u)

self.u_tonic = np.zeros(self.n_u)

self.u_feedback = np.zeros(self.n_u)

self.alpha_u = np.zeros(self.n_u)

self.e_u = np.zeros(self.n_u)

self.F_u = 0.0

self.mu_u_star = np.zeros(self.n_u)

  

def reset(self, u0=None):

self.population.reset(mu0=np.zeros(self.n_u) if u0 is None else np.asarray(u0, dtype=float).reshape(self.n_u))

self.mu_u = self.population.mu.copy()

  

def set_precision(self, pi_u=None):

if pi_u is not None:

self.pi_u = as_precision(pi_u, self.n_u)

  

def update(self, mu_C, mu_E, dt, pi_u=None):

mu_C = np.asarray(mu_C, dtype=float).reshape(self.n)

mu_E = np.asarray(mu_E, dtype=float).reshape(self.n)

dt = float(dt)

self.set_precision(pi_u=pi_u)

  

self.u_tonic = self.U @ mu_C

self.u_feedback = self.K @ (mu_C - mu_E)

self.target_u = self.u_tonic + self.u_feedback

  

pi_diag = diag(self.pi_u)

if self.tau_u <= 0.0:

self.alpha_u = np.ones(self.n_u)

else:

self.alpha_u = 1.0 - np.exp(-(pi_diag * dt) / self.tau_u)

self.relaxed_target_u = self.mu_u + self.alpha_u * (self.target_u - self.mu_u)

  

M = self.pi_u

b = self.pi_u @ self.relaxed_target_u

self.mu_u = self.population.update(b=b, M=M, dt=dt)

self.mu_u = np.clip(self.mu_u, self.u_min, self.u_max)

self.population.mu = self.mu_u.copy()

self._update_diagnostics()

return self.mu_u.copy()

  

def _update_diagnostics(self):

self.e_u = self.mu_u - self.target_u

self.F_u = self.e_u @ self.pi_u @ self.e_u

self.mu_u_star = self.relaxed_target_u.copy()

  

def diagnostics(self):

pop = self.population.diagnostics()

return {

"mu_u": self.mu_u.copy(),

"target_u": self.target_u.copy(),

"relaxed_target_u": self.relaxed_target_u.copy(),

"u_tonic": self.u_tonic.copy(),

"u_feedback": self.u_feedback.copy(),

"alpha_u": self.alpha_u.copy(),

"e_u": self.e_u.copy(),

"F_u": float(self.F_u),

"pi_u": diag(self.pi_u),

"mu_u_star": self.mu_u_star.copy(),

"star_error": self.mu_u - self.mu_u_star,

"spike_count_u": pop["spike_count"],

"above_count_u": pop["above_count"],

"v_max_u": pop["v_max"],

"population": pop,

}

  
  

# ---------------------------------------------------------------------

# Wrapper

# ---------------------------------------------------------------------

  
  

class Bio_AUSFEC:

def __init__(

self,

plant,

G=None,

K=None,

U=None,

D_E=None,

D_C=None,

D_u=None,

N_E=None,

N_C=None,

N_u_pop=None,

decoder_scale_E=4.0,

decoder_scale_C=4.0,

decoder_scale_u=4.0,

pi_y=1.0,

pi_w=1.0,

pi_x=1.0,

pi_z=4.0,

pi_u=1.0,

beta_E=0.0,

beta_C=0.0,

beta_u=0.0,

tau_E=0.1,

tau_C=0.1,

tau_u=0.02,

rate_decay_E=True,

rate_decay_C=True,

rate_decay_u=True,

lambda_adapt_E=0.0,

lambda_adapt_C=0.0,

lambda_adapt_u=0.0,

voltage_noise_E=0.0,

voltage_noise_C=0.0,

voltage_noise_u=0.0,

voltage_leak_E=0.0,

voltage_leak_C=0.0,

voltage_leak_u=0.0,

slow_current_gain_E=1.0,

slow_current_gain_C=1.0,

slow_current_gain_u=1.0,

reset_gain_E=1.0,

reset_gain_C=1.0,

reset_gain_u=1.0,

threshold_curvature_E=1.0,

threshold_curvature_C=1.0,

threshold_curvature_u=1.0,

max_parallel_spikes_E=16,

max_parallel_spikes_C=16,

max_parallel_spikes_u=8,

spike_delay_steps_E=1,

spike_delay_steps_C=1,

spike_delay_steps_u=1,

v_clip_E=None,

v_clip_C=None,

v_clip_u=None,

use_rk4_prior=True,

u_min=-np.inf,

u_max=np.inf,

rng=None,

):

self.plant = plant

self.n = int(plant.x_k)

self.n_u = int(plant.u_k)

self.rng = np.random.default_rng() if rng is None else rng

  

if K is None:

B = coerce_matrix(plant.B_lin, rows=self.n)

K = np.linalg.pinv(B) @ np.eye(self.n)

  

self.estimator = BioEstimatorPopulation(

plant=plant,

D_E=D_E,

N_E=N_E,

decoder_scale=decoder_scale_E,

pi_y=pi_y,

pi_w=pi_w,

beta_E=beta_E,

tau_E=tau_E,

rate_decay_E=rate_decay_E,

lambda_adapt_E=lambda_adapt_E,

voltage_noise_E=voltage_noise_E,

voltage_leak_E=voltage_leak_E,

slow_current_gain_E=slow_current_gain_E,

reset_gain_E=reset_gain_E,

threshold_curvature_E=threshold_curvature_E,

max_parallel_spikes_E=max_parallel_spikes_E,

spike_delay_steps_E=spike_delay_steps_E,

v_clip_E=v_clip_E,

use_rk4_prior=use_rk4_prior,

rng=self.rng,

)

  

self.controller = BioControllerPopulation(

n=self.n,

G=G,

D_C=D_C,

N_C=N_C,

decoder_scale=decoder_scale_C,

pi_x=pi_x,

pi_z=pi_z,

beta_C=beta_C,

tau_C=tau_C,

rate_decay_C=rate_decay_C,

lambda_adapt_C=lambda_adapt_C,

voltage_noise_C=voltage_noise_C,

voltage_leak_C=voltage_leak_C,

slow_current_gain_C=slow_current_gain_C,

reset_gain_C=reset_gain_C,

threshold_curvature_C=threshold_curvature_C,

max_parallel_spikes_C=max_parallel_spikes_C,

spike_delay_steps_C=spike_delay_steps_C,

v_clip_C=v_clip_C,

rng=self.rng,

)

  

self.action = BioActionPopulation(

K=K,

U=U,

D_u=D_u,

N_u_pop=N_u_pop,

decoder_scale=decoder_scale_u,

pi_u=pi_u,

beta_u=beta_u,

tau_u=tau_u,

rate_decay_u=rate_decay_u,

lambda_adapt_u=lambda_adapt_u,

voltage_noise_u=voltage_noise_u,

voltage_leak_u=voltage_leak_u,

slow_current_gain_u=slow_current_gain_u,

reset_gain_u=reset_gain_u,

threshold_curvature_u=threshold_curvature_u,

max_parallel_spikes_u=max_parallel_spikes_u,

spike_delay_steps_u=spike_delay_steps_u,

v_clip_u=v_clip_u,

u_min=u_min,

u_max=u_max,

rng=self.rng,

)

  

def setup(self, y0=None, mu0=None, u0=None):

self.estimator.setup(y0=y0, mu0=mu0)

self.controller.setup(mu0=self.estimator.mu_E)

self.action.reset(u0=u0)

  

def update(self, y, z, dt, u_prev=None, precisions=None):

if precisions is None:

precisions = {}

mu_E = self.estimator.update(y=y, dt=dt, u_prev=u_prev, pi_y=precisions.get("pi_y"), pi_w=precisions.get("pi_w"))

mu_C = self.controller.update(mu_E=mu_E, z=z, dt=dt, pi_x=precisions.get("pi_x"), pi_z=precisions.get("pi_z"))

mu_u = self.action.update(mu_C=mu_C, mu_E=mu_E, dt=dt, pi_u=precisions.get("pi_u"))

return mu_u.copy()

  

def diagnostics(self):

return {

"estimator": self.estimator.diagnostics(),

"controller": self.controller.diagnostics(),

"action": self.action.diagnostics(),

}

  

def kill_fraction(self, fraction=0.25, factors=("E", "C", "u")):

if "E" in factors:

self.estimator.population.kill_fraction(fraction)

if "C" in factors:

self.controller.population.kill_fraction(fraction)

if "u" in factors:

self.action.population.kill_fraction(fraction)

  

def set_voltage_noise(self, noise, factors=("E", "C", "u")):

if "E" in factors:

self.estimator.population.set_voltage_noise(noise)

if "C" in factors:

self.controller.population.set_voltage_noise(noise)

if "u" in factors:

self.action.population.set_voltage_noise(noise)

  
  

# ---------------------------------------------------------------------

# Convenience functions

# ---------------------------------------------------------------------

  
  

def smd_feedback_gain(m=1.0, omega=2.0, zeta=1.0):

return m * np.array([[omega**2, 2.0 * zeta * omega]], dtype=float)

  
  

def smd_tonic_readout(k=3.0, c=1.0):

return np.array([[k, c]], dtype=float)

  
  

def plant_noise_precisions(plant, dt=None):

V_y = np.asarray(plant.V_d, dtype=float)

V_w = np.asarray(plant.V_n, dtype=float)

if dt is not None:

V_y = float(dt) * V_y

V_w = float(dt) * V_w

return {"pi_y": np.linalg.pinv(V_y), "pi_w": np.linalg.pinv(V_w)}




















































"""Spiking AU-SFEC, separated by posterior factor.

  

This is the spiking counterpart of the analytical implementation:

  

1. SpikingEstimator

owns mu_E = D_E r_E

minimizes F_E with SFEC threshold spikes

  

2. SpikingController

owns mu_C = D_C r_C

minimizes F_C with SFEC threshold spikes

  

3. SpikingActionPosterior

owns mu_u = D_u r_u

minimizes F_u with SFEC threshold spikes

  

4. SpikingAUSFEC

thin wrapper wiring the three factors together

  

Design choice relative to the old monolithic SFEC class:

The old class updates voltage incrementally using precomputed O matrices and

delayed spikes. This version keeps the same computational style—decoder D,

rate vector r, voltage v, threshold T, reset O@s—but separates estimator,

controller, and action factors. For precision, each factor recomputes its

exact quadratic bias and curvature at the beginning of the update, then uses

greedy one-spike-at-a-time SFEC events. This avoids the small cross-term error

that can happen when all above-threshold neurons spike simultaneously.

  

No precision learning is included here. The runner supplies Pi_y, Pi_w, Pi_x,

Pi_z, and Pi_u, exactly as in the analytical implementation.

"""

  

from __future__ import annotations

  

import numpy as np

  
  

# ---------------------------------------------------------------------

# Shared helpers

# ---------------------------------------------------------------------

  
  

def as_precision(x, dim: int) -> np.ndarray:

"""Accept scalar, diagonal vector, or full matrix precision."""

x = np.asarray(x, dtype=float)

  

if x.ndim == 0:

return float(x) * np.eye(dim)

  

if x.ndim == 1:

if x.size != dim:

raise ValueError(f"Diagonal precision has length {x.size}, expected {dim}.")

return np.diag(x)

  

if x.shape != (dim, dim):

raise ValueError(f"Precision has shape {x.shape}, expected {(dim, dim)}.")

  

return x

  
  

def diag(P: np.ndarray) -> np.ndarray:

return np.diag(P).copy()

  
  

def coerce_matrix(M, rows: int | None = None, cols: int | None = None) -> np.ndarray:

M = np.asarray(M, dtype=float)

if M.ndim == 1:

M = M[:, None]

if rows is not None and M.shape[0] != rows:

raise ValueError(f"Matrix has {M.shape[0]} rows, expected {rows}.")

if cols is not None and M.shape[1] != cols:

raise ValueError(f"Matrix has {M.shape[1]} cols, expected {cols}.")

return M

  
  

def balanced_decoder(

dim: int,

N: int | None = None,

scale: float = 1.0,

rng: np.random.Generator | None = None,

random_std: float = 1.0,

shuffle: bool = True,

) -> np.ndarray:

"""Build an old-SFEC-style balanced decoder.

  

The first 2*dim columns are +e_i and -e_i. Remaining columns are random.

Columns are scaled by scale / N, which matches the old code pattern where

D was divided by a constant times N.

"""

if rng is None:

rng = np.random.default_rng()

  

if N is None:

N = max(8 * dim, 32)

N = int(N)

  

if N < 2 * dim:

raise ValueError("Need at least 2*dim neurons for a balanced decoder.")

  

D = np.zeros((dim, N), dtype=float)

for k in range(dim):

D[k, 2 * k] = 1.0

D[k, 2 * k + 1] = -1.0

  

if N > 2 * dim:

D[:, 2 * dim :] = rng.normal(0.0, random_std, size=(dim, N - 2 * dim))

  

if shuffle:

D = D[:, rng.permutation(N)]

  

return (scale / float(N)) * D

  
  

def free_energy_quadratic(mu: np.ndarray, b: np.ndarray, M: np.ndarray, const: float = 0.0) -> float:

"""Return mu^T M mu - 2 b^T mu + const.

  

This is useful for checking monotonicity of spike updates. For the actual

factor diagnostics below, we compute the explicit prediction-error energies.

"""

return float(mu @ M @ mu - 2.0 * b @ mu + const)

  
  

# ---------------------------------------------------------------------

# Core SFEC population

# ---------------------------------------------------------------------

  
  

class QuadraticSpikingPopulation:

"""Generic SFEC population for a quadratic free energy.

  

It minimizes, up to constants,

  

F(r) = (D r)^T M (D r) - 2 b^T (D r) + beta r^T r.

  

Define

  

mu = D r

g = b - M mu

v = D^T g

O = D^T M D

  

If neuron i spikes, r_i <- r_i + 1 and mu <- mu + D_i. The exact change is

  

Delta F_i = -2 v_i + O_ii + beta(2 r_i + 1).

  

So the free-energy-decreasing spike condition is

  

v_i > 0.5 O_ii + beta(r_i + 0.5).

  

This class implements that rule directly. The default greedy mode spikes the

single best neuron, updates v by the local reset O[:, i], and repeats. That

is more precise than simultaneous thresholding. A parallel mode is provided

only to mimic the old code more closely.

"""

  

def __init__(

self,

D: np.ndarray,

beta: float = 0.0,

tau_r: float = 0.1,

lambda_adapt: float = 0.0,

voltage_noise: float = 0.0,

rng: np.random.Generator | None = None,

mode: str = "greedy",

max_spikes: int | None = None,

):

self.D = np.asarray(D, dtype=float)

if self.D.ndim != 2:

raise ValueError("D must be a 2D decoder matrix.")

  

self.dim, self.N = self.D.shape

self.beta = float(beta)

self.tau_r = float(tau_r)

self.lambda_adapt = float(lambda_adapt)

self.voltage_noise = float(voltage_noise)

self.rng = np.random.default_rng() if rng is None else rng

self.mode = str(mode)

self.max_spikes = max_spikes

  

self.r = np.zeros(self.N)

self.v = np.zeros(self.N)

self.s = np.zeros(self.N)

self.r_adapt = np.zeros(self.N)

self.alive = np.ones(self.N)

self.mu = np.zeros(self.dim)

  

self.O = np.zeros((self.N, self.N))

self.O_diag = np.zeros(self.N)

self.T_base = np.zeros(self.N)

self.threshold = np.zeros(self.N)

self.last_spike_count = 0

  

def reset(self, mu0: np.ndarray | None = None, r0: np.ndarray | None = None):

if r0 is not None:

self.r = np.asarray(r0, dtype=float).reshape(self.N)

elif mu0 is not None:

mu0 = np.asarray(mu0, dtype=float).reshape(self.dim)

self.r = np.linalg.pinv(self.D) @ mu0

else:

self.r = np.zeros(self.N)

  

self.v.fill(0.0)

self.s.fill(0.0)

self.r_adapt.fill(0.0)

self.mu = self.D @ self.r

self.last_spike_count = 0

  

def kill_fraction(self, fraction: float = 0.25):

"""Mimic the old kill() helper."""

fraction = float(np.clip(fraction, 0.0, 1.0))

self.alive[:] = 1.0

n_dead = int(round(fraction * self.N))

self.alive[:n_dead] = 0.0

  

def set_voltage_noise(self, noise: float):

self.voltage_noise = float(noise)

  

def _decay_rates(self, dt: float):

if self.tau_r > 0.0:

# Exact exponential decay for filtered spike counts.

self.r *= np.exp(-dt / self.tau_r)

self.mu = self.D @ self.r

  

def _update_adaptation(self):

if self.lambda_adapt > 0.0:

# lambda_adapt is interpreted as old-code discrete retention.

self.r_adapt = (1.0 - self.lambda_adapt) * self.r_adapt + self.s

else:

self.r_adapt.fill(0.0)

  

def _make_threshold(self):

self.threshold = self.T_base + self.beta * (self.r + 0.5) + self.r_adapt

return self.threshold

  

def infer(

self,

b: np.ndarray,

M: np.ndarray,

dt: float,

max_spikes: int | None = None,

mode: str | None = None,

recompute_voltage: bool = True,

) -> np.ndarray:

"""Run SFEC spiking inference for one external time step.

  

Parameters

----------

b:

Bias vector in state/action space.

M:

Positive semidefinite curvature in state/action space.

dt:

External simulation time step. Used for rate decay and voltage noise.

max_spikes:

Event budget for this factor in this update. If None, uses self.max_spikes;

if that is None, uses N. For higher accuracy, increase it.

mode:

"greedy" for exact one-at-a-time thresholding, or "parallel" to mimic

the old code's all-above-threshold update.

recompute_voltage:

If True, set v = D^T(b - M mu). This is the precise mode. If False,

the caller is responsible for maintaining v incrementally.

"""

b = np.asarray(b, dtype=float).reshape(self.dim)

M = np.asarray(M, dtype=float).reshape(self.dim, self.dim)

dt = float(dt)

  

self._decay_rates(dt)

  

self.O = self.D.T @ M @ self.D

self.O_diag = np.diag(self.O).copy()

self.T_base = 0.5 * self.O_diag

  

if recompute_voltage:

self.v = self.D.T @ (b - M @ self.mu)

  

if self.voltage_noise > 0.0 and dt > 0.0:

self.v += self.voltage_noise * self.rng.normal(0.0, 1.0, self.N) * np.sqrt(dt)

  

self.v *= self.alive

self.s.fill(0.0)

  

if max_spikes is None:

max_spikes = self.max_spikes

if max_spikes is None:

max_spikes = self.N

max_spikes = int(max(0, max_spikes))

  

mode = self.mode if mode is None else mode

spike_count = 0

  

if mode == "parallel":

# Closest to old code. Less exact because cross terms among simultaneous

# spikes are ignored by the individual threshold test.

self._make_threshold()

above = np.where((self.v > self.threshold) & (self.alive > 0.0))[0]

if above.size > max_spikes:

margins = self.v[above] - self.threshold[above]

above = above[np.argsort(margins)[-max_spikes:]]

if above.size:

s = np.zeros(self.N)

s[above] = 1.0

self.s = s

self.r += s

self.mu += self.D @ s

self.v -= self.O @ s

spike_count = int(above.size)

  

elif mode == "greedy":

# Exact SFEC event loop: each accepted spike individually lowers F.

for _ in range(max_spikes):

self._make_threshold()

margin = (self.v - self.threshold) * self.alive

i = int(np.argmax(margin))

if margin[i] <= 0.0:

break

  

self.s[i] += 1.0

self.r[i] += 1.0

self.mu += self.D[:, i]

self.v -= self.O[:, i]

spike_count += 1

else:

raise ValueError("mode must be 'greedy' or 'parallel'.")

  

self._update_adaptation()

self.last_spike_count = spike_count

return self.mu.copy()

  

def diagnostics(self) -> dict:

return {

"mu": self.mu.copy(),

"r": self.r.copy(),

"v": self.v.copy(),

"s": self.s.copy(),

"threshold": self.threshold.copy(),

"T_base": self.T_base.copy(),

"r_adapt": self.r_adapt.copy(),

"spike_count": int(self.last_spike_count),

}

  
  

# ---------------------------------------------------------------------

# 1. Estimator posterior: mu_E = D_E r_E

# ---------------------------------------------------------------------

  
  

class SpikingEstimator:

"""Target-free spiking estimator.

  

Math:

mu_prior = Phi mu_E_previous + Gamma u_prev

  

F_E = (y - C mu_E)^T Pi_y (y - C mu_E)

+ (mu_prior - mu_E)^T Pi_w (mu_prior - mu_E)

+ beta_E r_E^T r_E

  

mu_E = D_E r_E

  

b_E = C^T Pi_y y + Pi_w mu_prior

M_E = C^T Pi_y C + Pi_w

v_E = D_E^T (b_E - M_E mu_E)

"""

  

def __init__(

self,

plant,

D_E: np.ndarray | None = None,

N_E: int | None = None,

decoder_scale: float = 1.0,

pi_y=1.0,

pi_w=1.0,

beta_E: float = 0.0,

tau_E: float = 0.1,

lambda_adapt_E: float = 0.0,

voltage_noise_E: float = 0.0,

rng: np.random.Generator | None = None,

mode: str = "greedy",

max_spikes_E: int | None = None,

):

self.plant = plant

self.n = int(plant.x_k)

self.m = int(plant.y_k)

self.n_u = int(plant.u_k)

  

self.A = np.asarray(plant.A_lin, dtype=float)

self.B = coerce_matrix(plant.B_lin, rows=self.n)

self.C = np.asarray(plant.C, dtype=float).reshape(self.m, self.n)

  

self.rng = np.random.default_rng() if rng is None else rng

if D_E is None:

D_E = balanced_decoder(self.n, N=N_E, scale=decoder_scale, rng=self.rng)

self.population = QuadraticSpikingPopulation(

D=D_E,

beta=beta_E,

tau_r=tau_E,

lambda_adapt=lambda_adapt_E,

voltage_noise=voltage_noise_E,

rng=self.rng,

mode=mode,

max_spikes=max_spikes_E,

)

  

self.pi_y = as_precision(pi_y, self.m)

self.pi_w = as_precision(pi_w, self.n)

  

self.mu_E = np.zeros(self.n)

self.mu_prior = np.zeros(self.n)

self.Phi = np.eye(self.n)

self.Gamma = np.zeros((self.n, self.n_u))

self.initialized = False

  

self._reset_diagnostics()

  

@property

def D(self) -> np.ndarray:

return self.population.D

  

@property

def r(self) -> np.ndarray:

return self.population.r

  

@property

def v(self) -> np.ndarray:

return self.population.v

  

@property

def s(self) -> np.ndarray:

return self.population.s

  

def _reset_diagnostics(self):

self.y = np.zeros(self.m)

self.y_hat = np.zeros(self.m)

self.nu_y = np.zeros(self.m)

self.e_y = np.zeros(self.m)

self.e_w = np.zeros(self.n)

self.F_E = 0.0

self.posterior_precision = np.eye(self.n)

self.mu_E_star = np.zeros(self.n)

  

def setup(self, y0=None, mu0=None):

if mu0 is None:

if y0 is None:

mu0 = np.asarray(self.plant.x0_lin, dtype=float).reshape(self.n)

else:

y0 = np.asarray(y0, dtype=float).reshape(self.m)

mu0 = np.linalg.lstsq(self.C, y0, rcond=None)[0]

  

self.population.reset(mu0=mu0)

self.mu_E = self.population.mu.copy()

self.mu_prior = self.mu_E.copy()

self.initialized = True

  

def set_precisions(self, pi_y=None, pi_w=None):

if pi_y is not None:

self.pi_y = as_precision(pi_y, self.m)

if pi_w is not None:

self.pi_w = as_precision(pi_w, self.n)

  

def predict_prior(self, dt: float, u_prev) -> np.ndarray:

u_prev = np.asarray(u_prev, dtype=float).reshape(self.n_u)

self.Phi = np.eye(self.n) + float(dt) * self.A

self.Gamma = float(dt) * self.B

# Important: prior is formed from the previous epistemic belief before

# the current spiking posterior update.

self.mu_prior = self.Phi @ self.mu_E + self.Gamma @ u_prev

return self.mu_prior.copy()

  

def update(self, y, dt: float, u_prev=None, pi_y=None, pi_w=None, max_spikes=None):

y = np.asarray(y, dtype=float).reshape(self.m)

self.set_precisions(pi_y=pi_y, pi_w=pi_w)

  

if not self.initialized:

self.setup(y0=y)

  

if u_prev is None:

u_prev = np.zeros(self.n_u)

else:

u_prev = np.asarray(u_prev, dtype=float).reshape(self.n_u)

  

self.predict_prior(dt, u_prev)

  

M = self.C.T @ self.pi_y @ self.C + self.pi_w

b = self.C.T @ self.pi_y @ y + self.pi_w @ self.mu_prior

  

self.mu_E = self.population.infer(b=b, M=M, dt=dt, max_spikes=max_spikes)

self._update_diagnostics(y, M, b)

return self.mu_E.copy()

  

def _update_diagnostics(self, y, M, b):

self.y = y.copy()

self.y_hat = self.C @ self.mu_E

self.nu_y = y - self.C @ self.mu_prior

self.e_y = y - self.y_hat

self.e_w = self.mu_prior - self.mu_E

self.F_E = self.e_y @ self.pi_y @ self.e_y + self.e_w @ self.pi_w @ self.e_w

self.posterior_precision = M.copy()

self.mu_E_star = np.linalg.solve(M, b)

  

def diagnostics(self) -> dict:

pop = self.population.diagnostics()

return {

"mu_E": self.mu_E.copy(),

"mu_prior": self.mu_prior.copy(),

"y": self.y.copy(),

"y_hat": self.y_hat.copy(),

"nu_y": self.nu_y.copy(),

"e_y": self.e_y.copy(),

"e_w": self.e_w.copy(),

"F_E": float(self.F_E),

"pi_y": diag(self.pi_y),

"pi_w": diag(self.pi_w),

"posterior_precision": self.posterior_precision.copy(),

"mu_E_star": self.mu_E_star.copy(),

"star_error": self.mu_E.copy() - self.mu_E_star.copy(),

"spike_count_E": pop["spike_count"],

"population": pop,

}

  
  

# ---------------------------------------------------------------------

# 2. Controller posterior: mu_C = D_C r_C

# ---------------------------------------------------------------------

  
  

class SpikingController:

"""Target-biased spiking controller belief.

  

Math:

F_C = (mu_E - mu_C)^T Pi_x (mu_E - mu_C)

+ (z - G mu_C)^T Pi_z (z - G mu_C)

+ beta_C r_C^T r_C

  

mu_C = D_C r_C

  

b_C = Pi_x mu_E + G^T Pi_z z

M_C = Pi_x + G^T Pi_z G

v_C = D_C^T (b_C - M_C mu_C)

"""

  

def __init__(

self,

n: int,

G=None,

D_C: np.ndarray | None = None,

N_C: int | None = None,

decoder_scale: float = 1.0,

pi_x=1.0,

pi_z=4.0,

beta_C: float = 0.0,

tau_C: float = 0.1,

lambda_adapt_C: float = 0.0,

voltage_noise_C: float = 0.0,

rng: np.random.Generator | None = None,

mode: str = "greedy",

max_spikes_C: int | None = None,

):

self.n = int(n)

self.G = np.eye(self.n) if G is None else np.asarray(G, dtype=float)

if self.G.ndim != 2 or self.G.shape[1] != self.n:

raise ValueError("G must have shape (p, n).")

self.p = self.G.shape[0]

  

self.rng = np.random.default_rng() if rng is None else rng

if D_C is None:

D_C = balanced_decoder(self.n, N=N_C, scale=decoder_scale, rng=self.rng)

self.population = QuadraticSpikingPopulation(

D=D_C,

beta=beta_C,

tau_r=tau_C,

lambda_adapt=lambda_adapt_C,

voltage_noise=voltage_noise_C,

rng=self.rng,

mode=mode,

max_spikes=max_spikes_C,

)

  

self.pi_x = as_precision(pi_x, self.n)

self.pi_z = as_precision(pi_z, self.p)

  

self.mu_C = np.zeros(self.n)

self._reset_diagnostics()

  

@property

def D(self) -> np.ndarray:

return self.population.D

  

@property

def r(self) -> np.ndarray:

return self.population.r

  

@property

def v(self) -> np.ndarray:

return self.population.v

  

@property

def s(self) -> np.ndarray:

return self.population.s

  

def _reset_diagnostics(self):

self.z = np.zeros(self.p)

self.e_x = np.zeros(self.n)

self.e_z = np.zeros(self.p)

self.F_C = 0.0

self.posterior_precision = np.eye(self.n)

self.mu_C_star = np.zeros(self.n)

  

def setup(self, mu0=None):

self.population.reset(mu0=np.zeros(self.n) if mu0 is None else mu0)

self.mu_C = self.population.mu.copy()

  

def set_precisions(self, pi_x=None, pi_z=None):

if pi_x is not None:

self.pi_x = as_precision(pi_x, self.n)

if pi_z is not None:

self.pi_z = as_precision(pi_z, self.p)

  

def update(self, mu_E, z, pi_x=None, pi_z=None, dt: float = 0.0, max_spikes=None):

mu_E = np.asarray(mu_E, dtype=float).reshape(self.n)

z = np.asarray(z, dtype=float).reshape(self.p)

self.set_precisions(pi_x=pi_x, pi_z=pi_z)

  

M = self.pi_x + self.G.T @ self.pi_z @ self.G

b = self.pi_x @ mu_E + self.G.T @ self.pi_z @ z

  

self.mu_C = self.population.infer(b=b, M=M, dt=dt, max_spikes=max_spikes)

self._update_diagnostics(mu_E, z, M, b)

return self.mu_C.copy()

  

def _update_diagnostics(self, mu_E, z, M, b):

self.z = z.copy()

self.e_x = mu_E - self.mu_C

self.e_z = z - self.G @ self.mu_C

self.F_C = self.e_x @ self.pi_x @ self.e_x + self.e_z @ self.pi_z @ self.e_z

self.posterior_precision = M.copy()

self.mu_C_star = np.linalg.solve(M, b)

  

def diagnostics(self) -> dict:

pop = self.population.diagnostics()

return {

"mu_C": self.mu_C.copy(),

"z": self.z.copy(),

"e_x": self.e_x.copy(),

"e_z": self.e_z.copy(),

"F_C": float(self.F_C),

"pi_x": diag(self.pi_x),

"pi_z": diag(self.pi_z),

"posterior_precision": self.posterior_precision.copy(),

"mu_C_star": self.mu_C_star.copy(),

"star_error": self.mu_C.copy() - self.mu_C_star.copy(),

"spike_count_C": pop["spike_count"],

"population": pop,

}

  
  

# ---------------------------------------------------------------------

# 3. Action posterior: mu_u = D_u r_u

# ---------------------------------------------------------------------

  
  

class SpikingActionPosterior:

"""Spiking action posterior.

  

Pure AU-SFEC action:

target_u = K(mu_C - mu_E)

  

Optional tonic/feedforward action:

target_u = U mu_C + K(mu_C - mu_E)

  

Spiking motor free energy:

F_u = (target_u - mu_u)^T Pi_u (target_u - mu_u)

+ beta_u r_u^T r_u

  

mu_u = D_u r_u

b_u = Pi_u target_u

M_u = Pi_u

v_u = D_u^T (b_u - M_u mu_u)

  

Note:

This is the strict spiking analogue of the continuous action posterior.

The finite settling time is controlled by tau_u and by max_spikes_u.

"""

  

def __init__(

self,

K,

U=None,

D_u: np.ndarray | None = None,

N_u_pop: int | None = None,

decoder_scale: float = 1.0,

pi_u=1.0,

beta_u: float = 0.0,

tau_u: float = 0.02,

lambda_adapt_u: float = 0.0,

voltage_noise_u: float = 0.0,

u_min=-np.inf,

u_max=np.inf,

rng: np.random.Generator | None = None,

mode: str = "greedy",

max_spikes_u: int | None = None,

):

self.K = np.asarray(K, dtype=float)

if self.K.ndim == 1:

self.K = self.K[None, :]

self.n_u, self.n = self.K.shape

  

if U is None:

self.U = np.zeros_like(self.K)

else:

self.U = np.asarray(U, dtype=float)

if self.U.ndim == 1:

self.U = self.U[None, :]

if self.U.shape != self.K.shape:

raise ValueError(f"U has shape {self.U.shape}, expected {self.K.shape}.")

  

self.rng = np.random.default_rng() if rng is None else rng

if D_u is None:

D_u = balanced_decoder(self.n_u, N=N_u_pop, scale=decoder_scale, rng=self.rng)

self.population = QuadraticSpikingPopulation(

D=D_u,

beta=beta_u,

tau_r=tau_u,

lambda_adapt=lambda_adapt_u,

voltage_noise=voltage_noise_u,

rng=self.rng,

mode=mode,

max_spikes=max_spikes_u,

)

  

self.pi_u = as_precision(pi_u, self.n_u)

self.u_min = np.full(self.n_u, u_min) if np.isscalar(u_min) else np.asarray(u_min, dtype=float)

self.u_max = np.full(self.n_u, u_max) if np.isscalar(u_max) else np.asarray(u_max, dtype=float)

  

self.mu_u = np.zeros(self.n_u)

self._reset_diagnostics()

  

@property

def D(self) -> np.ndarray:

return self.population.D

  

@property

def r(self) -> np.ndarray:

return self.population.r

  

@property

def v(self) -> np.ndarray:

return self.population.v

  

@property

def s(self) -> np.ndarray:

return self.population.s

  

def _reset_diagnostics(self):

self.target_u = np.zeros(self.n_u)

self.u_tonic = np.zeros(self.n_u)

self.u_feedback = np.zeros(self.n_u)

self.e_u = np.zeros(self.n_u)

self.F_u = 0.0

self.mu_u_star = np.zeros(self.n_u)

  

def reset(self, u0=None):

if u0 is None:

self.population.reset(mu0=np.zeros(self.n_u))

else:

self.population.reset(mu0=np.asarray(u0, dtype=float).reshape(self.n_u))

self.mu_u = self.population.mu.copy()

  

def set_precision(self, pi_u=None):

if pi_u is not None:

self.pi_u = as_precision(pi_u, self.n_u)

  

def update(self, mu_C, mu_E, dt: float, pi_u=None, max_spikes=None):

mu_C = np.asarray(mu_C, dtype=float).reshape(self.n)

mu_E = np.asarray(mu_E, dtype=float).reshape(self.n)

self.set_precision(pi_u=pi_u)

  

self.u_tonic = self.U @ mu_C

self.u_feedback = self.K @ (mu_C - mu_E)

self.target_u = self.u_tonic + self.u_feedback

  

M = self.pi_u

b = self.pi_u @ self.target_u

  

self.mu_u = self.population.infer(b=b, M=M, dt=dt, max_spikes=max_spikes)

self.mu_u = np.clip(self.mu_u, self.u_min, self.u_max)

  

# If clipped, keep the population's public mean aligned with the actual

# applied command. We do not back-project clipping into r because that is

# a nonlocal constrained operation; logs expose clipping if it occurs.

self.population.mu = self.mu_u.copy()

  

self._update_diagnostics()

return self.mu_u.copy()

  

def _update_diagnostics(self):

self.e_u = self.mu_u - self.target_u

self.F_u = self.e_u @ self.pi_u @ self.e_u

self.mu_u_star = self.target_u.copy()

  

def diagnostics(self) -> dict:

pop = self.population.diagnostics()

return {

"mu_u": self.mu_u.copy(),

"target_u": self.target_u.copy(),

"u_tonic": self.u_tonic.copy(),

"u_feedback": self.u_feedback.copy(),

"e_u": self.e_u.copy(),

"F_u": float(self.F_u),

"pi_u": diag(self.pi_u),

"mu_u_star": self.mu_u_star.copy(),

"star_error": self.mu_u.copy() - self.mu_u_star.copy(),

"spike_count_u": pop["spike_count"],

"population": pop,

}

  
  

# ---------------------------------------------------------------------

# 4. Thin wrapper: full spiking AU-SFEC loop

# ---------------------------------------------------------------------

  
  

class SpikingAUSFEC:

"""Thin wrapper connecting the three spiking posterior factors."""

  

def __init__(

self,

plant,

G=None,

K=None,

U=None,

D_E: np.ndarray | None = None,

D_C: np.ndarray | None = None,

D_u: np.ndarray | None = None,

N_E: int | None = None,

N_C: int | None = None,

N_u_pop: int | None = None,

decoder_scale_E: float = 1.0,

decoder_scale_C: float = 1.0,

decoder_scale_u: float = 1.0,

pi_y=1.0,

pi_w=1.0,

pi_x=1.0,

pi_z=4.0,

pi_u=1.0,

beta_E: float = 0.0,

beta_C: float = 0.0,

beta_u: float = 0.0,

tau_E: float = 0.1,

tau_C: float = 0.1,

tau_u: float = 0.02,

lambda_adapt_E: float = 0.0,

lambda_adapt_C: float = 0.0,

lambda_adapt_u: float = 0.0,

voltage_noise_E: float = 0.0,

voltage_noise_C: float = 0.0,

voltage_noise_u: float = 0.0,

u_min=-np.inf,

u_max=np.inf,

rng: np.random.Generator | None = None,

mode: str = "greedy",

max_spikes_E: int | None = None,

max_spikes_C: int | None = None,

max_spikes_u: int | None = None,

):

self.plant = plant

self.n = int(plant.x_k)

self.n_u = int(plant.u_k)

self.rng = np.random.default_rng() if rng is None else rng

  

if K is None:

B = coerce_matrix(plant.B_lin, rows=self.n)

K = np.linalg.pinv(B) @ np.eye(self.n)

  

self.estimator = SpikingEstimator(

plant=plant,

D_E=D_E,

N_E=N_E,

decoder_scale=decoder_scale_E,

pi_y=pi_y,

pi_w=pi_w,

beta_E=beta_E,

tau_E=tau_E,

lambda_adapt_E=lambda_adapt_E,

voltage_noise_E=voltage_noise_E,

rng=self.rng,

mode=mode,

max_spikes_E=max_spikes_E,

)

  

self.controller = SpikingController(

n=self.n,

G=G,

D_C=D_C,

N_C=N_C,

decoder_scale=decoder_scale_C,

pi_x=pi_x,

pi_z=pi_z,

beta_C=beta_C,

tau_C=tau_C,

lambda_adapt_C=lambda_adapt_C,

voltage_noise_C=voltage_noise_C,

rng=self.rng,

mode=mode,

max_spikes_C=max_spikes_C,

)

  

self.action = SpikingActionPosterior(

K=K,

U=U,

D_u=D_u,

N_u_pop=N_u_pop,

decoder_scale=decoder_scale_u,

pi_u=pi_u,

beta_u=beta_u,

tau_u=tau_u,

lambda_adapt_u=lambda_adapt_u,

voltage_noise_u=voltage_noise_u,

u_min=u_min,

u_max=u_max,

rng=self.rng,

mode=mode,

max_spikes_u=max_spikes_u,

)

  

def setup(self, y0=None, mu0=None, u0=None):

self.estimator.setup(y0=y0, mu0=mu0)

self.controller.setup(mu0=self.estimator.mu_E)

self.action.reset(u0=u0)

  

def update(self, y, z, dt: float, u_prev=None, precisions=None, spike_budgets=None):

if precisions is None:

precisions = {}

if spike_budgets is None:

spike_budgets = {}

  

mu_E = self.estimator.update(

y=y,

dt=dt,

u_prev=u_prev,

pi_y=precisions.get("pi_y"),

pi_w=precisions.get("pi_w"),

max_spikes=spike_budgets.get("E"),

)

  

mu_C = self.controller.update(

mu_E=mu_E,

z=z,

dt=dt,

pi_x=precisions.get("pi_x"),

pi_z=precisions.get("pi_z"),

max_spikes=spike_budgets.get("C"),

)

  

mu_u = self.action.update(

mu_C=mu_C,

mu_E=mu_E,

dt=dt,

pi_u=precisions.get("pi_u"),

max_spikes=spike_budgets.get("u"),

)

  

return mu_u.copy()

  

def diagnostics(self) -> dict:

return {

"estimator": self.estimator.diagnostics(),

"controller": self.controller.diagnostics(),

"action": self.action.diagnostics(),

}

  

def kill_fraction(self, fraction: float = 0.25, factors=("E", "C", "u")):

if "E" in factors:

self.estimator.population.kill_fraction(fraction)

if "C" in factors:

self.controller.population.kill_fraction(fraction)

if "u" in factors:

self.action.population.kill_fraction(fraction)

  

def set_voltage_noise(self, noise: float, factors=("E", "C", "u")):

if "E" in factors:

self.estimator.population.set_voltage_noise(noise)

if "C" in factors:

self.controller.population.set_voltage_noise(noise)

if "u" in factors:

self.action.population.set_voltage_noise(noise)

  
  

# ---------------------------------------------------------------------

# SMD convenience functions

# ---------------------------------------------------------------------

  
  

def smd_feedback_gain(m=1.0, omega=2.0, zeta=1.0):

"""For x = [position, velocity], K = m [omega^2, 2 zeta omega]."""

return m * np.array([[omega**2, 2.0 * zeta * omega]], dtype=float)

  
  

def smd_tonic_readout(k=3.0, c=1.0):

"""For v_dot = -k p - c v + u, tonic action is u = k p_C + c v_C."""

return np.array([[k, c]], dtype=float)

  
  

def plant_noise_precisions(plant, dt=None):

"""Oracle precisions from Plant.V_d and Plant.V_n.

  

If Plant.step uses

x += sqrt(dt) noise with covariance V_n

y += sqrt(dt) noise with covariance V_d

  

then per-step covariance is dt*V, so per-step precision is inv(dt*V).

"""

V_y = np.asarray(plant.V_d, dtype=float)

V_w = np.asarray(plant.V_n, dtype=float)

  

if dt is not None:

V_y = float(dt) * V_y

V_w = float(dt) * V_w

  

return {

"pi_y": np.linalg.pinv(V_y),

"pi_w": np.linalg.pinv(V_w),

}

  
  

# ---------------------------------------------------------------------

# Example usage

# ---------------------------------------------------------------------

  

"""

plant = Plant(system="SMD", v_n=1e-4, v_d=1e-4, seed=0)

dt = 0.001

rng = np.random.default_rng(0)

  

ausfec = SpikingAUSFEC(

plant=plant,

G=np.eye(plant.x_k),

K=smd_feedback_gain(m=1.0, omega=2.0, zeta=1.0),

U=smd_tonic_readout(k=3.0, c=1.0), # set U=None for pure AU-SFEC feedback only

N_E=64,

N_C=64,

N_u_pop=16,

decoder_scale_E=1.0,

decoder_scale_C=1.0,

decoder_scale_u=1.0,

pi_x=np.ones(plant.x_k),

pi_z=4.0 * np.ones(plant.z_k),

pi_u=np.ones(plant.u_k),

beta_E=0.0,

beta_C=0.0,

beta_u=0.0,

tau_E=0.1,

tau_C=0.1,

tau_u=0.02,

u_min=-40.0,

u_max=40.0,

rng=rng,

mode="greedy", # use "parallel" to mimic old all-above-threshold SFEC

max_spikes_E=64, # increase for closer agreement with analytical posterior

max_spikes_C=64,

max_spikes_u=16,

)

  

x = plant.x0.copy()

y = plant.g(x)

z = np.array([0.0, 0.0])

u_prev = np.zeros(plant.u_k)

  

ausfec.setup(y0=y, mu0=x, u0=u_prev)

  

for step in range(5000):

precisions = plant_noise_precisions(plant, dt=dt)

  

u = ausfec.update(

y=y,

z=z,

dt=dt,

u_prev=u_prev,

precisions=precisions,

spike_budgets={"E": 64, "C": 64, "u": 16},

)

  

x, y = plant.step(x, u, dt=dt)

u_prev = u.copy()

  

logs = ausfec.diagnostics()

# Useful precision checks:

# logs["estimator"]["star_error"]

# logs["controller"]["star_error"]

# logs["action"]["star_error"]

"""