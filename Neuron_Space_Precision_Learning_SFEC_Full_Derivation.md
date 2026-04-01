# Neuron-Space Precision Learning in SFEC

## A Local, Biologically Plausible Extension with Guaranteed Stability

**Extension of:** Urbano, Lanillos & Keemink (2026) — *Efficient and robust control with spikes that constrain free energy*

---

## 1. Starting Point: The SFEC Framework

The Spiking Free Energy Constrainer (SFEC) is a spiking neural network that implements Active Inference by directly constraining the variational free energy. We briefly review the elements relevant to this extension.

### 1.1 The Dynamical System

We control a linear time-invariant system with state **x** ∈ ℝ^K:

    ẋ = Ax + Bu + dw
    y = Cx + dη

where A, B, C are the dynamics, input, and observation matrices, dw and dη are process and observation noise. The controller receives noisy observations y and must produce control signal u to drive the system toward a target z.

### 1.2 The Free Energy

Under the Free Energy Principle, the controller minimizes:

    F = εᵧᵀ Pᵧ εᵧ  +  εᵤᵀ Pᵤ εᵤ  +  rᵀr  +  K

where:

- εᵧ = y⁺ − C⁺μ is the sensory prediction error,
- εᵤ = Mμ − μ is the dynamics prediction error,
- Pᵧ and Pᵤ are precision matrices (inverse variances),
- rᵀr is the sparsity penalty,
- K = −ln|Pᵧ| − ln|Pᵤ| is the log-normalizer, constant when precisions are fixed.

Stacking the errors into ε = [εᵧ, εᵤ] ∈ ℝ^{4K} and defining the block matrix H = [C⁺; I] ∈ ℝ^{4K×2K}, we can write:

    ε = a − Hμ

where a = [y⁺, Mμ] ∈ ℝ^{4K}, and the free energy becomes:

    F = εᵀ P ε + rᵀr + K

with P = diag(Pᵧ I, Pᵤ I) the full block-diagonal precision matrix.

### 1.3 The Network

The network maintains N integrate-and-fire neurons. The internal state estimate is decoded from filtered spike trains:

    μ = Dr,    ṙ = −λr + s

where D ∈ ℝ^{K×N} is the decoder, r ∈ ℝ^N the firing rates, s ∈ ℝ^N the binary spike vector. Voltage dynamics are:

    v̇ = Wᵧ ẏ⁺ + Ω_slow r + Ω_fast s

with weight matrices:

    Wᵧ     = Dᵀ Hᵀ P 𝟙ᵧ
    Ω_slow = Dᵀ Hᵀ P (𝟙ᵤ A_target + λH) D
    Ω_fast = −Dᵀ Hᵀ P H D

Neuron i fires when its voltage vᵢ exceeds its adaptive threshold Tᵢ, which is guaranteed to reduce the free energy. The control output is:

    u = Uμ = B⁻¹ A_target μ

---

## 2. Why Observation-Space Precision Cannot Be Local

A natural approach to adaptive precision would be to maintain one precision parameter λᵢ per observation channel i, adapting it online based on prediction errors εᵧ,ᵢ. We show here that this is fundamentally incompatible with the locality constraint of spiking neural networks.

### 2.1 What Observation-Space Precision Requires

To compute the prediction error for channel i, a neuron would need:

- **yᵢ:** the raw observation for channel i. This is a global sensory input, broadcast to all neurons. ✓ Available locally.
- **(Cμ)ᵢ = Σⱼ Cᵢⱼ μⱼ = Σⱼ Cᵢⱼ Σₖ Dⱼₖ rₖ:** the network's prediction of observation i. This requires summing over all neurons k, weighted by decoder D and observation matrix C. ✗ Not locally available.

The second requirement is fatal to locality. No single neuron has access to the full population firing rates rₖ of all other neurons except through weighted spike-based recurrent connections, which already encode a different quantity.

### 2.2 Why Recurrent Spikes Do Not Help

The recurrent input to neuron i carries:

    (Ω_slow)ᵢ r + (Ω_fast)ᵢ s = Dᵢᵀ Hᵀ P H D r + ...

This is a precision-weighted projection of the total error onto neuron i's decoder direction. It mixes all observation channels simultaneously and cannot be decomposed back into individual εᵧ,ᵢ components without global knowledge of D, H, and P.

### 2.3 Conclusion

Keeping precision in observation space while maintaining full locality is impossible within the SFEC architecture. Any neuron computing εᵧ,ᵢ requires a global population readout μ = Dr, which is not available through local spike-based communication alone. This forces precision into neuron space.

---

## 3. Neuron-Space Precision: The Local Alternative

### 3.1 Core Idea

Instead of assigning one precision parameter per observation channel, we assign one log-precision scalar λᵢ per neuron i. This parameter modulates the overall gain of neuron i's input weights. The key insight is that neuron i's voltage vᵢ is already a locally available, precision-weighted measure of total surprise experienced by that neuron. We use vᵢ as the error signal for adapting λᵢ.

### 3.2 What vᵢ Encodes

From the SFEC derivation, neuron i's voltage satisfies:

    vᵢ = Dᵢᵀ Hᵀ P ε

where ε = [εᵧ, εᵤ] ∈ ℝ^{4K} is the full stacked prediction error vector. Thus vᵢ is a weighted projection of all prediction errors onto neuron i's decoder direction Dᵢ. A neuron with large |vᵢ| is experiencing high surprise in its preferred encoding direction. This is the natural, locally available analog of a per-channel prediction error.

> **Locality check:** vᵢ is computed entirely from quantities local to neuron i — its own membrane potential, which integrates inputs already arriving at its dendrites. No other neuron's state is needed. ✓

### 3.3 The Exponential Parameterization

We parameterize each neuron's precision as:

    Πᵢ = Pₛ · exp(λᵢ)

where Pₛ > 0 is a fixed design-time scale factor shared across all neurons, and λᵢ ∈ ℝ is the learnable log-precision of neuron i. This parameterization has three critical properties:

- **Positivity guaranteed:** exp(λᵢ) > 0 for all λᵢ ∈ ℝ, so Πᵢ > 0 always. No constraints are needed during optimization.
- **Full range:** λᵢ → +∞ gives Πᵢ → +∞ (high trust); λᵢ → −∞ gives Πᵢ → 0 (no trust). The entire positive real line is reachable.
- **Tractable gradients:** the log-determinant −ln(Πᵢ) = −λᵢ − ln(Pₛ) is linear in λᵢ, making the anti-collapse term algebraically simple.

> **Locality check:** λᵢ is a scalar stored locally at neuron i. No communication with other neurons is required to read or update it. ✓

### 3.4 Effect on Weight Matrices

The weight matrices of SFEC depend on the precision matrix P. With neuron-space precision, each neuron i has its own effective precision Πᵢ, which modulates its row of the weight matrices:

    (Wᵧ)ᵢ     = Πᵢ · Dᵢᵀ Hᵀ 𝟙ᵧ
    (Ω_fast)ᵢ = −Πᵢ · Dᵢᵀ Hᵀ H D
    (Ω_slow)ᵢ = Πᵢ · Dᵢᵀ Hᵀ (𝟙ᵤ A_target + λH) D

Each row is scaled independently by that neuron's Πᵢ. Neurons with high λᵢ have stronger synaptic weights and fire more reactively to errors in their encoding direction. Neurons with low λᵢ are effectively downweighted and contribute less to the population code.

**Critical structural observation.** Because every term in the voltage equation for neuron i is proportional to Πᵢ, the voltage factorizes as:

    vᵢ(t) = Πᵢ · ẽᵢ(t)

where ẽᵢ(t) := Dᵢᵀ Hᵀ ε(t) is the **precision-stripped error projection** — the raw surprise in neuron i's preferred direction, independent of that neuron's precision setting. This factorization is central to the correct derivation of the learning rule (see Section 6).

> **Locality check:** row i of each weight matrix depends only on λᵢ, Dᵢ, and shared fixed matrices H, 𝟙ᵧ, A_target. Updating λᵢ only requires recomputing row i, with no effect on any other neuron's weights. ✓

### 3.5 Relationship to the Global Free Energy (Approximate Spiking Guarantee)

In the original SFEC, the spiking rule is derived from the global inequality F(spike) < F(silent) with a well-defined error-space precision matrix P. When we replace P with per-neuron scalars Πᵢ, the effective precision in error space becomes:

    P̃ = Σⱼ Πⱼ (H Dⱼ)(H Dⱼ)ᵀ

This is a rank-N matrix constructed from the decoder columns, which in general differs from the original hand-designed block-diagonal P. Therefore, the neuron-space modification is an **approximation** to the true free energy constraint.

**Approximation quality.** The approximation error depends on how well the set of outer products {(H Dⱼ)(H Dⱼ)ᵀ} spans the space of symmetric positive-definite matrices:

- When D columns are orthogonal in the Hᵀ H metric, the approximation is exact up to a per-direction scaling.
- When N ≫ K with random decoders (the typical SFEC regime), concentration of measure ensures that P̃ ≈ (N · average Πᵢ / K) · Hᵀ H, which is close to the original P if Hᵀ H ∝ P (often true by construction).
- The error is bounded by ||P̃ − P||_op / ||P||_op, which decreases as O(1/√N) for random decoders.

For practical network sizes (N ≥ 32), this approximation is tight. We state this explicitly as an approximation with an O(1/√N) bound, rather than claiming an exact guarantee.

---

## 4. Two-Timescale Architecture

The complete system operates on two strictly separated timescales. This separation is not merely a computational convenience — it is mathematically necessary for the precision estimate to reflect genuine noise statistics rather than transient estimation errors.

### 4.1 Fast Timescale: Spiking Control (unchanged form)

The fast loop runs at every simulation timestep Δt ~ 1ms:

    v̇ᵢ = (Wᵧ)ᵢ ẏ⁺ + (Ω_slow)ᵢ r + (Ω_fast)ᵢ s

Neuron i fires when vᵢ ≥ Tᵢ, updating rᵢ and driving μ toward the target. The control output u = Uμ is generated continuously.

**Important clarification:** The *form* of the voltage equation is identical to the original SFEC. However, the *numerical values* of the weight matrices differ from the original because they now depend on per-neuron Πᵢ rather than a fixed global P. This means the network's dynamics, convergence rate, and steady-state behavior all depend on the current precision settings. When a precision update fires and rebuilds row i, the fast loop experiences a discontinuous parameter change in that row. The timescale separation (Section 4.3) ensures this discontinuity is small and the fast loop re-converges quickly.

### 4.2 Slow Timescale: Precision-Stripped Accumulation

In parallel with the fast loop, each neuron i runs a leaky accumulator of its own **precision-stripped** squared voltage:

    ã̇ᵢ = −γ ãᵢ + (vᵢ / Πᵢ)²

where γ ≪ λ is a slow decay constant. The division by Πᵢ is the critical correction that removes the precision dependence from the accumulated quantity, ensuring the Free Action gradient is computed correctly (see Section 6 for detailed justification).

**Why precision-stripping is essential.** Since vᵢ = Πᵢ · ẽᵢ (Section 3.4), the raw squared voltage v²ᵢ = Π²ᵢ · ẽ²ᵢ contains a hidden Π²ᵢ factor. If we accumulated v²ᵢ directly and then differentiated the Free Action treating the accumulator as constant with respect to λᵢ, we would obtain a *wrong* gradient — the actual dependence of the accumulator on λᵢ through Π²ᵢ would be silently ignored, leading to an incorrect fixed point and invalid update rule. By accumulating (vᵢ/Πᵢ)² = ẽ²ᵢ instead, the accumulator is genuinely independent of Πᵢ, and the gradient calculation is exact.

**Biological implementation.** The precision-stripped quantity vᵢ/Πᵢ = vᵢ · exp(−λᵢ)/Pₛ is a gain-normalized membrane potential. Divisive normalization is one of the most well-documented neuronal computations, observed across cortical circuits. The accumulator ãᵢ can be implemented as a slow dendritic calcium concentration that integrates the gain-normalized squared activity.

Equivalently, at each timestep the accumulator is updated as:

    ãᵢ ← ãᵢ + (vᵢ / Πᵢ)² · Δt

and resets to zero after each precision update.

> **Locality check:** ãᵢ depends only on vᵢ and Πᵢ, both of which are local to neuron i. No information from any other neuron is required. ✓

### 4.3 The Adiabatic Approximation

The reason for strict timescale separation is the following. The voltage vᵢ(t) has two components:

- **Noise-driven:** fluctuations caused by actual input noise η, which we want to measure to set λᵢ.
- **Belief-driven:** fluctuations caused by μ(t) not yet having converged to its optimal value after a target change. These are transient and would bias the noise estimate upward if included.

If T_slow ≫ 1/λ_leak (the network's convergence time), then by the time the precision update fires, μ(t) has settled to its steady state and vᵢ(t) reflects only genuine noise. This is the adiabatic approximation: λᵢ changes so slowly that the fast network can be assumed to have already reached its optimal μ*(λ) at every point.

---

## 5. Local Stabilization Criterion

The precision update must only fire when the network has stabilized — i.e. when the adiabatic approximation holds. In the global formulation, this could be checked as ||μ̇(t)|| < ε, but this requires a global population readout and is therefore not local.

### 5.1 Local Proxy for Stabilization

We use neuron i's own firing rate as a local proxy for network stability, combined with a minimum waiting time after the last observed target change:

**Trigger condition for neuron i:**

    rᵢ(t) < ε_stable  for duration Δt_min    AND    t − t_last_change > T_guard

where:

- rᵢ is the filtered spike train of neuron i (computed locally as ṙᵢ = −λrᵢ + sᵢ),
- ε_stable is a small threshold,
- Δt_min is the required quiescence duration,
- t_last_change is the time of the most recent target change (globally broadcast),
- T_guard is a minimum waiting period, set to several multiples of the network's convergence time 1/λ_leak.

The firing-rate condition works because:

- When the network is transitioning (high free energy), neurons fire frequently to correct errors. rᵢ is high.
- When μ has converged to the target (low free energy), spikes are rare. rᵢ drops close to zero.
- The sparse activity of SFEC means that rᵢ ≈ 0 during steady state is a reliable signal.

**Why the guard time is needed.** The firing-rate criterion alone has a blind spot: if neuron i's decoder direction Dᵢ is nearly orthogonal to the current residual error, neuron i will be quiet even while the network is still converging along other directions. In overcomplete decoders (N ≫ K), many neurons will have directions nearly orthogonal to any given error. The guard time T_guard prevents such premature triggers by ensuring sufficient time has elapsed since the last major perturbation.

Crucially, each neuron triggers its own precision update at its own time Tᵢ (subject to the global guard). There is no global clock for the per-neuron updates. Neurons that stabilize faster update sooner. This is more biologically plausible than a shared global trigger.

> **Locality check:** rᵢ is the filtered spike train of neuron i, computed locally as ṙᵢ = −λrᵢ + sᵢ. The guard time t_last_change is a single globally broadcast scalar (akin to a neuromodulatory signal marking environmental changes). ✓

---

## 6. The Free Action: Stability Guarantee

### 6.1 Why Not Update Instantaneously

One might ask: why not update λᵢ at every timestep using the instantaneous gradient ∂F/∂λᵢ? Two reasons make this unstable:

- **Bias:** instantaneous vᵢ² includes belief-driven transients that inflate the noise estimate.
- **Variance:** vᵢ(t) fluctuates rapidly due to spikes. A single sample gives a very noisy gradient estimate.

The correct objective is the time-integral of the free energy over the slow window, keeping only λ-dependent terms. This is called the Free Action.

### 6.2 Derivation of the Free Action

Since λᵢ is constant over the window [0, T_slow], we integrate F over the window keeping only λᵢ-dependent terms. The free energy contains two λᵢ-dependent terms for neuron i:

- **Error term:** Πᵢ ẽ²ᵢ(t), which is the precision times the precision-stripped squared voltage. This penalizes large errors weighted by the current precision.
- **Log-determinant term:** −λᵢ, the anti-collapse regulator that prevents precision from diverging to infinity.

**Careful accounting of the Πᵢ dependence.** The raw voltage satisfies vᵢ = Πᵢ · ẽᵢ(t), so the error contribution to the free energy from neuron i's direction is:

    Πᵢ · ẽ²ᵢ(t)  =  Πᵢ · (vᵢ(t) / Πᵢ)²  =  v²ᵢ(t) / Πᵢ

Alternatively and equivalently, writing Πᵢ = Pₛ exp(λᵢ):

    Πᵢ · ẽ²ᵢ(t)  =  Pₛ exp(λᵢ) · ẽ²ᵢ(t)

The key point is that ẽᵢ(t) is independent of λᵢ — it is the precision-stripped projection of the error vector, which depends only on the external noise and the network's state estimate, not on neuron i's precision. Under the adiabatic approximation, the state estimate μ has converged and ẽᵢ(t) reflects only genuine noise.

Integrating over the window:

    Āᵢ(λᵢ) = ∫₀ᵀ [ Pₛ exp(λᵢ) · ẽ²ᵢ(t) − λᵢ ] dt

           = Pₛ exp(λᵢ) · ∫₀ᵀ ẽ²ᵢ(t) dt  −  λᵢ T

           = Pₛ exp(λᵢ) · ãᵢ  −  λᵢ T

where we define the **precision-stripped accumulated surprise:**

    ãᵢ  :=  ∫₀ᵀ ẽ²ᵢ(t) dt  =  ∫₀ᵀ (vᵢ(t) / Πᵢ)² dt  ≈  Σₜ (vᵢ(t) / Πᵢ)² · Δt

This ãᵢ is the quantity accumulated at the slow timescale (Section 4.2). Because ẽᵢ does not depend on λᵢ, ãᵢ is genuinely constant with respect to λᵢ within the window, and the gradient computation below is exact.

### 6.3 Why Precision-Stripping Fixes the Circularity

**The error in the naive approach.** Suppose we had instead accumulated the raw squared voltage:

    aᵢ_raw = ∫₀ᵀ v²ᵢ(t) dt = Π²ᵢ · ãᵢ = P²ₛ exp(2λᵢ) · ãᵢ

and written the Free Action as Āᵢ = Pₛ exp(λᵢ) · aᵢ_raw − λᵢ T, treating aᵢ_raw as constant. This would give:

    Āᵢ_wrong = Pₛ exp(λᵢ) · P²ₛ exp(2λᵢ) · ãᵢ − λᵢ T = P³ₛ exp(3λᵢ) · ãᵢ − λᵢ T

with gradient 3P³ₛ exp(3λᵢ) ãᵢ − T and fixed point Πᵢ* = (T/(3P²ₛ ãᵢ))^{1/3}. This is the wrong answer — the elegant 1/σ² interpretation is lost, and the update rule is derived from an inconsistent gradient.

**The correct approach.** By accumulating ẽ²ᵢ = (vᵢ/Πᵢ)² instead, the λᵢ-dependence is isolated in the explicit Pₛ exp(λᵢ) factor:

    Āᵢ_correct = Pₛ exp(λᵢ) · ãᵢ − λᵢ T

with gradient Pₛ exp(λᵢ) ãᵢ − T and fixed point Πᵢ* = T/ãᵢ. The physical meaning is recovered: the optimal precision is the inverse of the time-averaged precision-stripped surprise.

### 6.4 The Anti-Collapse Term is Essential

Without the −λᵢ T term (which comes from the log-determinant of the precision matrix), the Free Action would be:

    Āᵢ = Pₛ exp(λᵢ) · ãᵢ

which is minimized by λᵢ → −∞, driving Πᵢ → 0. The network would assign zero precision to all inputs and produce zero control. The log-determinant term provides the balancing force:

- When Pₛ exp(λᵢ) ãᵢ > T: gradient is positive, λᵢ decreases, precision decreases (errors too large, trust less)
- When Pₛ exp(λᵢ) ãᵢ < T: gradient is negative, λᵢ increases, precision increases (errors small, trust more)
- At equilibrium: Pₛ exp(λ*ᵢ) ãᵢ = T, a unique stable fixed point

### 6.5 Strict Convexity

The Free Action per neuron is:

    fᵢ(λᵢ) = Pₛ exp(λᵢ) · ãᵢ − λᵢ T

Its second derivative with respect to λᵢ:

    ∂²fᵢ / ∂λ²ᵢ = Pₛ exp(λᵢ) · ãᵢ > 0

strictly positive whenever ãᵢ > 0 (i.e. whenever the neuron experienced any nonzero precision-stripped voltage during the window). Therefore fᵢ is strictly convex in λᵢ, guaranteeing a unique global minimum with no saddle points or local minima.

Furthermore, since each neuron's Free Action fᵢ(λᵢ) depends only on its own λᵢ and ãᵢ, there is zero coupling between neurons **in the precision update step**. Each λᵢ is optimized independently within a single window.

**Important caveat: effective inter-neuron coupling.** While the single-window optimization is separable, the dynamics across windows are coupled. When neuron i updates its Πᵢ, it changes its row of the weight matrices, which alters the fast-loop dynamics, which in turn affects the voltage trajectories (and hence ãⱼ) of all other neurons j in subsequent windows. This effective coupling, mediated through the fast loop, means that the multi-window system is *not* fully decoupled. However, under the adiabatic regime, this coupling is weak: each Πᵢ update is small, the fast loop re-converges quickly, and the perturbation to other neurons' ãⱼ values is second-order. The cross-window convergence analysis in Section 8 addresses this explicitly.

---

## 7. The Precision Update Rule

### 7.1 Gradient and M-Step

The gradient of the Free Action with respect to λᵢ is:

    ∂Āᵢ / ∂λᵢ = Pₛ exp(λᵢ) · ãᵢ − T

Gradient descent on the Free Action gives the M-step update rule, triggered when neuron i detects local stabilization (Section 5):

    λᵢ ← clip( λᵢ + kλ · (T − Pₛ exp(λᵢ) · ãᵢ),  λ_min,  λ_max )

where kλ > 0 is the gradient step size and [λ_min, λ_max] are hard clamps preventing numerical overflow. After the update, the weight rows are rebuilt:

    (Wᵧ)ᵢ     ←  Pₛ exp(λᵢ) · Dᵢᵀ Hᵀ 𝟙ᵧ
    (Ω_fast)ᵢ ← −Pₛ exp(λᵢ) · Dᵢᵀ Hᵀ H D
    (Ω_slow)ᵢ ←  Pₛ exp(λᵢ) · Dᵢᵀ Hᵀ (𝟙ᵤ A_target + λH) D

Only row i is modified. All other neurons are completely unaffected within this timestep.

> **Locality check:** the update of λᵢ and the reconstruction of row i of the weight matrices requires only λᵢ, ãᵢ, Dᵢ, and shared fixed matrices. No other neuron's state or parameters are needed. ✓

### 7.2 Accept/Reject Safeguard with Backtracking

Because kλ is fixed and the curvature Pₛ exp(λᵢ) ãᵢ varies between windows, a gradient step can occasionally overshoot and increase the Free Action. We implement a backtracking line search:

**Algorithm (per neuron i):**

    1. Propose: λᵢ_new = λᵢ + kλ · (T − Πᵢ · ãᵢ)
    2. Evaluate: Āᵢ(λᵢ_new) = Pₛ exp(λᵢ_new) · ãᵢ − λᵢ_new · T
    3. If Āᵢ(λᵢ_new) < Āᵢ(λᵢ): accept.
    4. Else: halve kλ and go to step 1.
    5. Repeat up to M_max times; if all fail, keep λᵢ unchanged.

This guarantees monotonic descent of the Free Action at every window. Combined with strict convexity, this guarantees convergence to the unique within-window minimum regardless of the curvature. The cost is O(1) per neuron per rejected step (a single exponential and multiply).

**Note on what the safeguard evaluates.** The accept/reject decision compares Free Action values using the *same* ãᵢ (accumulated under the old Πᵢ). This is a counterfactual evaluation — "what would the Free Action have been if precision were λ_new during the window that was actually run with λ_old?" This is only an accurate proxy if the precision change is small, which the backtracking line search ensures by shrinking the step until acceptance. For large curvature mismatches, the backtracking naturally produces smaller, more conservative steps.

> **Locality check:** the accept/reject decision for neuron i requires only λᵢ, ãᵢ, kλ, Pₛ, and T — all locally stored. ✓

### 7.3 The Fixed Point and its Physical Meaning

The update stops when δλᵢ = 0, giving the fixed-point condition:

    Pₛ exp(λ*ᵢ) · ãᵢ = T

    ⟹  Π*ᵢ = Pₛ exp(λ*ᵢ) = T / ãᵢ

Under the adiabatic approximation, once μ has converged, ẽᵢ(t) = Dᵢᵀ Hᵀ ε(t) reflects only genuine noise in neuron i's encoding direction. Therefore:

    ãᵢ / T = (1/T) ∫₀ᵀ ẽ²ᵢ(t) dt ≈ σ̃²ᵢ

where σ̃²ᵢ is the mean squared precision-stripped voltage of neuron i at steady state. The optimal precision is:

    Π*ᵢ ≈ 1 / σ̃²ᵢ

Each neuron's precision converges to the inverse of its own steady-state mean squared precision-stripped surprise — its characteristic level of noise in its preferred encoding direction.

**Caveat: discretization bias.** At steady state, ẽᵢ(t) reflects both genuine input noise *and* the residual "bounding box" error intrinsic to SFEC's spiking discretization. This discretization error is systematic, not random. Consequently, σ̃²ᵢ slightly overestimates the true noise variance, and Π*ᵢ slightly underestimates the noise-optimal precision. The bias scales inversely with the bounding box diameter, which is controlled by the threshold Tᵢ. For practical network sizes, this bias is small but nonzero. If higher precision accuracy is needed, one can subtract an estimate of the discretization variance (computable from the threshold and decoder geometry) from ãᵢ before the update.

---

## 8. Cross-Window Convergence Guarantee

The within-window convexity (Section 6.5) guarantees a unique optimum for a single window's data. But across successive windows, λᵢ changes, which changes the weights, which changes the fast-loop dynamics, which changes future ãᵢ values. We need the iterated map to converge.

### 8.1 The Iterated Map

With precision-stripped accumulation, the update across windows is:

    λᵢ^{(n+1)} = λᵢ^{(n)} + kλ · (T − Πᵢ^{(n)} · ãᵢ^{(n)})

where ãᵢ^{(n)} is the precision-stripped accumulator from window n, and Πᵢ^{(n)} = Pₛ exp(λᵢ^{(n)}).

### 8.2 Contraction Under the Adiabatic Regime

For convergence, we need the map to be a contraction near the fixed point. The Jacobian of the map is:

    ∂λᵢ^{(n+1)} / ∂λᵢ^{(n)} = 1 − kλ · ∂/∂λᵢ [Πᵢ · ãᵢ(Πᵢ)]

Under the adiabatic approximation, once μ has converged, the residual error ε(t) at steady state is driven purely by noise. The precision-stripped projection ẽᵢ(t) = Dᵢᵀ Hᵀ ε(t) then reflects only noise projected onto neuron i's direction, which is independent of Πᵢ. This gives:

    ∂ãᵢ / ∂λᵢ ≈ 0    (adiabatic regime)

Therefore:

    ∂(Πᵢ · ãᵢ) / ∂λᵢ ≈ Πᵢ · ãᵢ

At the fixed point, Πᵢ · ãᵢ = T, so:

    ∂λᵢ^{(n+1)} / ∂λᵢ^{(n)} |_{fixed point} = 1 − kλ · T

The contraction condition |1 − kλ T| < 1 gives:

    **0 < kλ < 2/T**

This is an explicit, checkable bound. The convergence rate is |1 − kλ T|, so the optimal choice is **kλ = 1/T**, which gives exact convergence in a single step (the iteration Jacobian is zero — effectively Newton's method, since the exponential parameterization makes the single-window curvature match the cross-window iteration exactly).

### 8.3 Beyond the Adiabatic Regime

If timescale separation is imperfect, ãᵢ does depend on Πᵢ through the bounding box size. Higher Πᵢ → larger thresholds → larger bounding box → larger residual error. This makes ∂ãᵢ/∂Πᵢ > 0, which gives:

    ∂(Πᵢ · ãᵢ) / ∂λᵢ > Πᵢ · ãᵢ = T    (at fixed point)

So the effective Jacobian |1 − kλ · (T + δ)| requires a smaller kλ than the adiabatic bound. The correction δ can be estimated from the SFEC threshold expression:

    Tᵢ = (Πᵢ/2) ||H Dᵢ||² + rᵢ + 1/2

The bounding box diameter in neuron i's direction scales as ~Tᵢ/Πᵢ, and the residual discretization variance scales as O(||H Dᵢ||⁴). This gives:

    δ ~ O(Πᵢ · ||H Dᵢ||⁴ / Πᵢ²) = O(||H Dᵢ||⁴ / Πᵢ)

which is bounded and decreasing in Πᵢ. For practical precision values, δ ≪ T.

### 8.4 Unconditional Guarantee via Backtracking

For a fully robust guarantee regardless of the adiabatic approximation's quality, the backtracking line search (Section 7.2) ensures monotonic descent at every window. Combined with strict convexity and the fact that the Free Action is bounded below (since Pₛ exp(λᵢ) ãᵢ ≥ 0 and −λᵢ T → −∞ only if λᵢ → +∞, which makes the first term dominate), the sequence {Āᵢ^{(n)}} is monotonically decreasing and bounded below, hence convergent. By strict convexity, convergence of the Free Action implies convergence of λᵢ.

---

## 9. Two-Parameter Variant: Separating Sensory and Dynamics Precision

### 9.1 Motivation

The single-parameter formulation (Sections 3–8) assigns one precision Πᵢ per neuron, which jointly modulates sensitivity to both sensory errors εᵧ and dynamics errors εᵤ. This collapses the original SFEC's ability to differentially weight sensory vs. dynamics trust (P_y vs. P_μ) into a single number per neuron.

In many control scenarios, sensory noise and dynamics model error have very different magnitudes. A noisy sensor (high εᵧ) paired with a reliable dynamics model (low εᵤ) calls for low sensory precision and high dynamics precision. The single-parameter variant cannot express this per-neuron.

The two-parameter variant restores this expressivity while maintaining full locality.

### 9.2 Architecture

Each neuron i maintains two log-precisions:

    λᵢ^(y) ∈ ℝ    (sensory log-precision)
    λᵢ^(μ) ∈ ℝ    (dynamics log-precision)

with corresponding precisions:

    Πᵢ^(y) = Pₛ exp(λᵢ^(y))
    Πᵢ^(μ) = Pₛ exp(λᵢ^(μ))

The per-neuron effective precision becomes a 2×2 block structure (in the original error-space partition [sensory | dynamics]):

    Pᵢ = diag( Πᵢ^(y) I_{2K},  Πᵢ^(μ) I_{2K} )

### 9.3 Modified Weight Matrices

Recall that the full error-space precision enters the SFEC weight matrices through the combination Dᵀ Hᵀ P (...). With the two-parameter block structure, we partition H = [C⁺; I] and the identity selectors 𝟙ᵧ, 𝟙ᵤ:

    Hᵀ Pᵢ = [ C⁺ᵀ Πᵢ^(y),  Πᵢ^(μ) ]

Substituting into each weight matrix row for neuron i:

**Input weights (sensory pathway):**

    (Wᵧ)ᵢ = Dᵢᵀ Hᵀ Pᵢ 𝟙ᵧ = Πᵢ^(y) · Dᵢᵀ C⁺ᵀ

This depends only on the sensory precision. Sensory inputs are gated by Πᵢ^(y).

**Fast recurrent weights (maintenance):**

    (Ω_fast)ᵢ = −Dᵢᵀ Hᵀ Pᵢ H D
              = −Dᵢᵀ ( C⁺ᵀ Πᵢ^(y) C⁺ + Πᵢ^(μ) I ) D

This is a mixture of sensory and dynamics precisions.

**Slow recurrent weights (dynamics + leak):**

    (Ω_slow)ᵢ = Dᵢᵀ Hᵀ Pᵢ (𝟙ᵤ A_target + λH) D
              = Dᵢᵀ ( Πᵢ^(μ) A_target + λ (C⁺ᵀ Πᵢ^(y) C⁺ + Πᵢ^(μ) I) ) D

> **Locality check:** Row i depends only on λᵢ^(y), λᵢ^(μ), Dᵢ, and fixed shared matrices. No other neuron's parameters appear. ✓

### 9.4 Voltage Decomposition: Two Dendritic Compartments

The voltage dynamics decompose as:

    v̇ᵢ = [Πᵢ^(y) · Dᵢᵀ C⁺ᵀ] ẏ⁺  +  [Πᵢ^(μ) · Dᵢᵀ A_target D] r  +  maintenance terms

The first term is the **sensory drive** — it arrives via feedforward synapses and is gated by sensory precision. The second term is the **dynamics drive** — it arrives via recurrent synapses encoding the target dynamics and is gated by dynamics precision. The maintenance terms (leak correction, fast recurrent) involve both precisions and keep the representation bounded.

**The key insight for separation:** The sensory and dynamics drives arrive through architecturally distinct pathways. This maps naturally onto cortical pyramidal neurons, where:

- **Basal / proximal dendrites** receive feedforward sensory input → sensory drive
- **Apical / distal dendrites** receive top-down recurrent input → dynamics drive

Independent calcium signals in each dendritic compartment can serve as separate accumulators.

### 9.5 Two Precision-Stripped Accumulators

Each neuron runs two slow accumulators on the precision-stripped dendritic currents:

**Sensory accumulator (basal dendrite):**

    ãᵢ^(y) = ∫₀ᵀ [ Dᵢᵀ C⁺ᵀ ẏ⁺ ]² dt

This accumulates the squared raw sensory current *before* precision scaling. It is independent of both Πᵢ^(y) and Πᵢ^(μ).

> Note: We accumulate the squared sensory current Dᵢᵀ C⁺ᵀ ẏ⁺, which is the derivative of the sensory input projected onto neuron i's direction. In the SFEC, this quantity arrives at the neuron as the feedforward input term, but before multiplication by Πᵢ^(y). The precision-stripping is achieved by measuring the current at the dendritic input *before* gain modulation.

**Dynamics accumulator (apical dendrite):**

    ãᵢ^(μ) = ∫₀ᵀ [ Dᵢᵀ A_target D r ]² dt

This accumulates the squared raw dynamics current before precision scaling. It is independent of both precisions.

> **Locality check:** The sensory accumulator uses only the input current arriving at the "sensory dendrite" — a quantity local to neuron i. The dynamics accumulator uses only the target-dynamics recurrent current at the "dynamics dendrite" — also local. No global readout needed. ✓

### 9.6 Two Free Actions, Two Updates

Each parameter has its own Free Action, derived by integrating only the corresponding precision-dependent terms:

**Sensory Free Action:**

    Āᵢ^(y)(λᵢ^(y)) = Pₛ exp(λᵢ^(y)) · ãᵢ^(y) − λᵢ^(y) · T

**Dynamics Free Action:**

    Āᵢ^(μ)(λᵢ^(μ)) = Pₛ exp(λᵢ^(μ)) · ãᵢ^(μ) − λᵢ^(μ) · T

Both are independently strictly convex (identical proof as Section 6.5). The gradients are:

    ∂Āᵢ^(y) / ∂λᵢ^(y) = Pₛ exp(λᵢ^(y)) · ãᵢ^(y) − T

    ∂Āᵢ^(μ) / ∂λᵢ^(μ) = Pₛ exp(λᵢ^(μ)) · ãᵢ^(μ) − T

**Update rules** (both triggered by the same stabilization criterion):

    λᵢ^(y) ← clip( λᵢ^(y) + kλ · (T − Πᵢ^(y) · ãᵢ^(y)),  λ_min,  λ_max )

    λᵢ^(μ) ← clip( λᵢ^(μ) + kλ · (T − Πᵢ^(μ) · ãᵢ^(μ)),  λ_min,  λ_max )

After both updates, rebuild the three weight subexpressions for row i using both new precisions.

### 9.7 Fixed Points and Physical Meaning

At convergence:

    Πᵢ^(y)* = T / ãᵢ^(y) ≈ 1 / σ̃²_{i,sensory}

    Πᵢ^(μ)* = T / ãᵢ^(μ) ≈ 1 / σ̃²_{i,dynamics}

where σ̃²_{i,sensory} is the mean squared sensory current in neuron i's direction and σ̃²_{i,dynamics} is the mean squared dynamics current.

**What this achieves:** A neuron encoding a direction with a noisy sensory channel but reliable dynamics will converge to low Πᵢ^(y) and high Πᵢ^(μ) — it distrusts its observations but trusts its dynamics model. Conversely, a neuron in a clean sensory channel with noisy dynamics will converge to the opposite. This is exactly the behavior that the original SFEC's fixed Pᵧ vs Pᵤ was hand-tuned to achieve, but now it is **learned per-neuron and per-channel**.

### 9.8 Cross-Window Convergence for Two Parameters

The cross-window analysis of Section 8 applies independently to each parameter. Under the adiabatic regime:

- ãᵢ^(y) is independent of both λᵢ^(y) and λᵢ^(μ) (it depends only on the noise-driven sensory input).
- ãᵢ^(μ) is independent of both parameters (it depends only on the noise-driven dynamics residual).

Therefore the Jacobian of the two-parameter iterated map is diagonal:

    J = diag( 1 − kλ T,  1 − kλ T )

and both eigenvalues have magnitude |1 − kλ T| < 1 when 0 < kλ < 2/T. The two parameters converge independently at the same rate, with no cross-coupling in the adiabatic regime.

Beyond the adiabatic regime, the cross-coupling is mediated through the fast loop (changing Πᵢ^(y) affects the voltage trajectory, which affects ãᵢ^(μ) and vice versa). But this coupling is second-order and suppressed by the timescale separation, exactly as in the single-parameter case (Section 8.3).

### 9.9 Biological Plausibility Assessment

The two-compartment model maps onto known cortical architecture:

- **Pyramidal neurons** receive feedforward sensory input on basal/proximal dendrites and top-down/recurrent input on apical dendrites. This compartmentalization is well-documented anatomically and functionally.
- **Independent calcium signals** in each compartment could serve as the accumulators. Dendritic calcium imaging has shown that basal and apical compartments can independently integrate and maintain calcium transients on slow timescales.
- **Gain modulation** of each compartment (via neuromodulators such as acetylcholine for sensory gating, or local inhibitory circuits via somatostatin interneurons for dynamics gating) implements the precision scaling. Different neuromodulatory systems differentially target dendritic compartments.
- **Two learning rates** (one per compartment) mediated by compartment-specific plasticity mechanisms (e.g., NMDA receptor subtypes with different calcium sensitivity in basal vs. apical dendrites).

The two-parameter variant is thus arguably *more* biologically plausible than the single-parameter version, because it respects the known functional segregation of dendritic compartments rather than collapsing them.

---

## 10. Summary of the Complete Algorithm

### 10.1 Initialization

For each neuron i = 1, ..., N:

    λᵢ^(y) = λ₀,    λᵢ^(μ) = λ₀    (initial log-precisions, e.g. λ₀ = 0)
    Πᵢ^(y) = Pₛ exp(λᵢ^(y)),    Πᵢ^(μ) = Pₛ exp(λᵢ^(μ))

Compute initial weight matrices using the formulas in Section 9.3.

### 10.2 Fast Loop (every Δt ~ 1ms)

    1. Receive observations y and target z.
    2. Update voltage: v̇ᵢ = (Wᵧ)ᵢ ẏ⁺ + (Ω_slow)ᵢ r + (Ω_fast)ᵢ s
    3. Fire neuron i if vᵢ ≥ Tᵢ.
    4. Update rates: ṙ = −λr + s.
    5. Decode: μ = Dr.
    6. Compute control: u = B⁻¹ A_target μ.
    7. Accumulate sensory surprise:  ãᵢ^(y) += [Dᵢᵀ C⁺ᵀ ẏ⁺]² · Δt
    8. Accumulate dynamics surprise: ãᵢ^(μ) += [Dᵢᵀ A_target D r]² · Δt

### 10.3 Slow Loop (per neuron, self-triggered)

For each neuron i, when the stabilization criterion is met (rᵢ < ε_stable for Δt_min AND t − t_last_change > T_guard):

    1. Compute proposed updates:
       λᵢ^(y)_new = clip(λᵢ^(y) + kλ · (T − Πᵢ^(y) · ãᵢ^(y)),  λ_min, λ_max)
       λᵢ^(μ)_new = clip(λᵢ^(μ) + kλ · (T − Πᵢ^(μ) · ãᵢ^(μ)),  λ_min, λ_max)

    2. Accept/reject with backtracking (independently for each parameter):
       If Āᵢ^(y)(λ_new) < Āᵢ^(y)(λ_old): accept sensory update.
       If Āᵢ^(μ)(λ_new) < Āᵢ^(μ)(λ_old): accept dynamics update.

    3. Update precisions: Πᵢ^(y) = Pₛ exp(λᵢ^(y)), Πᵢ^(μ) = Pₛ exp(λᵢ^(μ))

    4. Rebuild weight matrices for row i only (Section 9.3).

    5. Reset accumulators: ãᵢ^(y) = 0, ãᵢ^(μ) = 0.

### 10.4 Hyperparameters

| Symbol         | Meaning                                      | Recommended Value       |
|----------------|----------------------------------------------|-------------------------|
| Pₛ             | Base precision scale                         | Design-dependent        |
| kλ             | Gradient step size                           | 1/T (optimal) or < 2/T |
| [λ_min, λ_max] | Hard clamps                                 | [−10, 10]               |
| ε_stable       | Quiescence threshold                         | ~ 0.01                  |
| Δt_min         | Required quiescence duration                 | ~ 10/λ_leak             |
| T_guard        | Minimum wait after target change             | ~ 5/λ_leak              |
| T (= T_slow)   | Accumulation window length                  | ≫ 1/λ_leak              |
| γ              | Accumulator leak (if using leaky version)    | ≪ λ_leak                |

---

## 11. Formal Guarantees and Their Scope

We summarize the guarantees and their conditions.

### 11.1 Within-Window Guarantees (exact)

- **Strict convexity:** Each single-window Free Action fᵢ(λᵢ^(y)) and fᵢ(λᵢ^(μ)) is strictly convex whenever the corresponding accumulator is positive. Unique global minimum, no local minima or saddle points.
- **Monotonic descent:** The backtracking line search ensures Ā^{(n+1)} ≤ Ā^{(n)} at every window.

### 11.2 Cross-Window Guarantees (conditional)

- **Convergence under adiabatic regime:** If T_slow ≫ 1/λ_leak and 0 < kλ < 2/T, the iterated precision map is a contraction with rate |1 − kλ T|. At kλ = 1/T, convergence is in a single step.
- **Convergence with backtracking (unconditional):** The Free Action sequence is monotonically decreasing and bounded below, hence convergent. By strict convexity, this implies λᵢ convergence.

### 11.3 Approximate Guarantees

- **Spiking rule:** The modified spiking rule (with per-neuron precisions) approximately implements F(spike) < F(silent) for an effective error-space precision P̃ = Σⱼ Πⱼ (H Dⱼ)(H Dⱼ)ᵀ. The approximation quality is O(1/√N) for random decoders.
- **Fixed-point interpretation:** Π*ᵢ ≈ 1/σ̃²ᵢ holds up to a discretization bias that scales inversely with network size.

### 11.4 What is NOT Guaranteed

- **Global optimality of the spiking rule:** The per-neuron precision modifies the effective free energy surface. The spiking rule still reduces *a* free energy, but not necessarily the same one that the original SFEC was derived from. The discrepancy is small for overcomplete decoders.
- **Convergence rate beyond adiabatic:** When timescale separation is imperfect, the convergence rate depends on the implicit coupling between λᵢ and ãᵢ through the fast loop. The backtracking line search guarantees convergence but does not bound the rate.
- **Stability during weight discontinuities:** When a precision update fires and rebuilds row i, the fast loop experiences a sudden parameter change. Re-convergence of the fast loop is empirically rapid but not formally bounded for large precision jumps. The hard clamps [λ_min, λ_max] limit the maximum jump size.

---

## Appendix A: Notation Summary

| Symbol | Definition | Dimension |
|--------|-----------|-----------|
| x | System state | K |
| y | Observations | K |
| z | Target state | K |
| μ | Internal state estimate | 2K |
| D | Decoder matrix | K × N |
| Dᵢ | Column i of D | K |
| r | Firing rates | N |
| s | Spike vector | N |
| vᵢ | Voltage of neuron i | scalar |
| ε | Stacked prediction error | 4K |
| ẽᵢ | Precision-stripped error projection: Dᵢᵀ Hᵀ ε | scalar |
| H | Stacking matrix [C⁺; I] | 4K × 2K |
| P | Block-diagonal precision matrix | 4K × 4K |
| λᵢ^(y) | Sensory log-precision of neuron i | scalar |
| λᵢ^(μ) | Dynamics log-precision of neuron i | scalar |
| Πᵢ^(y) | Sensory precision: Pₛ exp(λᵢ^(y)) | scalar |
| Πᵢ^(μ) | Dynamics precision: Pₛ exp(λᵢ^(μ)) | scalar |
| Pₛ | Base precision scale | scalar |
| ãᵢ^(y) | Sensory precision-stripped accumulator | scalar |
| ãᵢ^(μ) | Dynamics precision-stripped accumulator | scalar |
| Āᵢ | Free Action for neuron i | scalar |
| kλ | Gradient step size | scalar |
| T | Accumulation window length | scalar |
| T_guard | Minimum wait after target change | scalar |
| λ_leak | Firing rate leak constant | scalar |

## Appendix B: Derivation Summary (Two-Parameter Variant)

**Step 1: Define per-neuron block precision.**

    Pᵢ = diag( Πᵢ^(y) I,  Πᵢ^(μ) I )

**Step 2: Substitute into SFEC weight matrices (row i only).**

    (Wᵧ)ᵢ     = Πᵢ^(y) · Dᵢᵀ C⁺ᵀ
    (Ω_fast)ᵢ = −Dᵢᵀ ( C⁺ᵀ Πᵢ^(y) C⁺ + Πᵢ^(μ) I ) D
    (Ω_slow)ᵢ = Dᵢᵀ ( Πᵢ^(μ) A_target + λ (C⁺ᵀ Πᵢ^(y) C⁺ + Πᵢ^(μ) I) ) D

**Step 3: Identify precision-stripped currents.**

    sensory current (before gain):   ẽᵢ^(y)(t) = Dᵢᵀ C⁺ᵀ ẏ⁺
    dynamics current (before gain):  ẽᵢ^(μ)(t) = Dᵢᵀ A_target D r

**Step 4: Accumulate precision-stripped squared currents.**

    ãᵢ^(y) = ∫₀ᵀ [ẽᵢ^(y)(t)]² dt
    ãᵢ^(μ) = ∫₀ᵀ [ẽᵢ^(μ)(t)]² dt

**Step 5: Write the Free Actions.**

    Āᵢ^(y) = Pₛ exp(λᵢ^(y)) · ãᵢ^(y) − λᵢ^(y) · T
    Āᵢ^(μ) = Pₛ exp(λᵢ^(μ)) · ãᵢ^(μ) − λᵢ^(μ) · T

**Step 6: Compute gradients.**

    ∂Āᵢ^(y) / ∂λᵢ^(y) = Pₛ exp(λᵢ^(y)) · ãᵢ^(y) − T
    ∂Āᵢ^(μ) / ∂λᵢ^(μ) = Pₛ exp(λᵢ^(μ)) · ãᵢ^(μ) − T

**Step 7: Update.**

    λᵢ^(y) ← λᵢ^(y) + kλ · (T − Πᵢ^(y) · ãᵢ^(y))
    λᵢ^(μ) ← λᵢ^(μ) + kλ · (T − Πᵢ^(μ) · ãᵢ^(μ))

**Step 8: Verify convexity.**

    ∂²Āᵢ^(y) / ∂(λᵢ^(y))² = Pₛ exp(λᵢ^(y)) · ãᵢ^(y) > 0  ✓
    ∂²Āᵢ^(μ) / ∂(λᵢ^(μ))² = Pₛ exp(λᵢ^(μ)) · ãᵢ^(μ) > 0  ✓

**Step 9: Fixed points.**

    Πᵢ^(y)* = T / ãᵢ^(y) ≈ 1 / σ̃²_{i,sensory}
    Πᵢ^(μ)* = T / ãᵢ^(μ) ≈ 1 / σ̃²_{i,dynamics}

**Step 10: Cross-window convergence.**

    Contraction condition: 0 < kλ < 2/T for both parameters independently.

---

*End of derivation.*
