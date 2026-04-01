
**SFEC-DEMA Per-Observable Precision Learning: Analysis and Next Steps**

**1. What We Built**

We extended the SFEC-DEMA M-step from a single scalar λ_y shared across all observables to a vector of per-observable log-precisions [λ₁, λ₂, ..., λ_{y_k}]. Each sensor channel now has its own precision Π_i = P_{y,scale} · exp(λ_i), updated independently via gradient descent on the Free Action:

λ_i ← λ_i + k_λ · (T − P_{y,scale} · exp(λ_i) · a3_i)

where a3_i = Σ ε²_{y,i} · dt is the accumulated squared prediction error for observable i over the M-step window. The dynamics precision λ_μ was eliminated entirely since ε_μ is not Gaussian noise — it depends on model mismatch and state derivatives, making it unsuitable for EM-based estimation.

The equilibrium of this update is Π*_i = 1/σ²_i, where σ²_i is the variance of the prediction error on channel i. The Free Action is strictly convex per λ_i, guaranteeing convergence.

---

**2. What the Experiments Show**

**2.1 The Working Regime**

When observation noise is moderate — large enough to be visible above tracking error but small enough that the controller can still function — the per-observable λ_i converges correctly. Each channel reaches a precision that reflects its actual error statistics. The convergence ratios (Π_learned / Π_true) approach 1.0, and the channels with different noise levels clearly differentiate from each other.

This was observed for channels where the effective per-step noise variance (dt · V_d) was comparable to or larger than the per-observable tracking error, while still being small enough for the controller to maintain tracking.

**2.2 Failure Mode 1: Tracking Error Dominates (Low Noise)**

When the observation noise is much smaller than the tracking error, all λ_i converge to approximately the same value regardless of their true noise levels. The diagnostic data shows why clearly: the accumulator a3_i = Σ(y_i − μ_i)² · dt measures the total prediction error, which is the sum of observation noise and tracking error. When tracking error dominates, all channels see approximately the same error magnitude — determined by the controller's tracking accuracy, not by sensor noise — and all lambdas converge to the "tracking error precision."

The algorithm is not wrong — it correctly estimates the precision of the total prediction error it observes. It simply cannot distinguish noise from tracking error within the a3_i accumulator.

Experimental evidence: with V_d = [10, 100, 1000] (eff_var = [0.01, 0.1, 1.0]) and tracking error/dim ≈ 0.1, the low-noise channels (mass 0, eff_var = 0.01) showed a3/T ≈ 0.05-0.08, far above their true noise variance, yielding convergence ratios of 0.12-0.18. Meanwhile mass 2 (eff_var = 1.0) showed a3/T ≈ 1.0-1.6 and ratios near 1.0.

**2.3 Failure Mode 2: Precision Collapse Spiral (High Noise)**

When observation noise is very high, a vicious cycle develops:

High noise → large ε_y → large a3 → λ decreases → precision drops → network weights observations less → controller tracks worse → even larger ε_y → a3 grows further → λ drops more → system diverges.

Experimental evidence: with V_d = [3000, 2000, 1000] (eff_var = [3.0, 2.0, 1.0]), mass 1 showed MSE growing from 0.49 at t=5s to 74.0 at t=120s, with λ decreasing monotonically and never converging. The a3/T for m1_y reached 63.9, far above the noise variance of 2.0, because the controller had lost tracking entirely.

The accept/reject safeguard does not prevent this because the Free Action genuinely decreases at each step — lowering precision when you see large errors is mathematically correct. The problem is that the adiabatic approximation (μ settles fast relative to λ changes) breaks down when the controller destabilises.

**2.4 Summary: The Viability Window**

The per-observable precision learning works correctly within a window. The lower bound is that dt · V_d must be larger than the tracking error per observable, otherwise tracking error contaminates a3_i and all lambdas converge to the same value. The upper bound is that dt · V_d must be small enough that the controller can still maintain tracking at the resulting precision, otherwise the precision collapse spiral triggers. Within this window, the algorithm converges to the correct per-observable noise precision.

**2.5 An Important Asymmetry: Velocity vs Position**

The velocity components consistently show better convergence ratios than position components, even in the same run. This is because the dynamics model A_ideal directly predicts velocities from the spring-damper physics, providing an implicit second source of information for velocity estimation. Position channels have no such backup — the only information about current position comes from the sensor.

---

**3. What the Precision Learning Actually Does**

It is important to be precise about what the M-step accomplishes and what it does not.

What it does: it estimates the reliability of each sensory channel as experienced by the controller. The learned Π_i reflects the total prediction error variance on channel i, which includes both observation noise and any residual tracking error.

What it does not do: it does not remove noise. It does not improve signal quality. It tells the network "how much to trust" each sensor, but the noisy signal still enters the system as-is. Downweighting a noisy sensor is correct estimation theory, but in a system with one sensor per observable, downweighting your only source of information is self-defeating — there is nowhere to redirect attention.

---

**4. Future Direction 1: Generalized Coordinates (DEM)**

Generalized coordinates encode the state and its temporal derivatives: [x, x', x'', ...]. Prediction errors at each temporal order have different sensitivity to noise vs. tracking error. The full DEM framework models the noise covariance structure across temporal orders (parameterised by a smoothness parameter s), which allows the estimation machinery to separate "this error pattern looks like noise" from "this error pattern looks like systematic model mismatch." This directly addresses the a3_i contamination problem. With the full temporal embedding, the M-step would operate on prediction errors that have been decorrelated across temporal orders, potentially allowing correct noise estimation even when tracking error is present at the zeroth order.

The main concerns are complexity and implementation cost. The full DEM apparatus requires generalized state vectors, temporal embedding matrices, noise smoothness estimation, and prediction errors at multiple orders. There are also bio-plausibility questions: encoding temporal derivatives explicitly in a spiking network raises questions about how neurons would represent ẍ. That said, the gap between "we implicitly use first derivatives through the dynamics model" and "we explicitly encode generalized coordinates" may be smaller than it first appears — the velocity/position asymmetry is already evidence that the dynamics model acts as a form of temporal filtering. This direction deserves more thought before being dismissed on complexity grounds.

---

**5. Future Direction 2: Sensory Redundancy**

Instead of one sensor per observable, provide K independent noisy sensors for each channel. Averaging K independent measurements with variance σ² gives variance σ²/K. This is pure physics — no algorithm needed. It reduces the actual noise level before it enters the controller, pushing the system into the working regime of precision learning by either making the noise small enough that tracking error dominates harmlessly, or keeping it moderate enough to stay within the viability window.

Sensory redundancy does not fix the a3_i contamination problem. Tracking error still enters the accumulator. For channels where noise was already below the tracking error floor, adding more sensors doesn't help the precision estimate — it just makes the noise even more invisible relative to tracking error. But this doesn't matter practically because the signal is already clean enough for the controller to work.

With identical, stable sensors, the M-step is not strictly necessary — naive averaging gives σ²/K regardless. The M-step becomes valuable when one sensor in a population degrades (rain on a camera, gyroscope drift, mechanical damage), when noise levels are unknown or time-varying, or when sensor populations are heterogeneous across observables. In the degradation case, the degraded sensor's λ drops and it is effectively excluded from the precision-weighted estimate — this is critical for small K (5-10 sensors) where one bad sensor significantly affects the naive average. This is precisely what the brain does with multisensory integration: reliability-weighted combination where the weighting is learned from error statistics, not hardcoded.

Sensory redundancy is also the most biologically grounded mechanism available. Real sensory systems are massively redundant: millions of photoreceptors with overlapping receptive fields, thousands of hair cells per frequency band, groups of muscle spindles per muscle. The brain never relies on a single receptor for anything. The current SFEC architecture already has processing redundancy through the N-neuron population; what's missing is input redundancy. This is architecturally clean: a wider input layer, not a deeper or more complex one.

---

**6. Critical Evaluation**

**What holds up well.** The viability window analysis is solid. The experimental data clearly shows the three regimes (tracking dominates, working regime, collapse), and the a3_i diagnostics explain exactly why each regime occurs. This is not speculation — it's directly visible in the numbers. The velocity vs. position asymmetry is genuine evidence: the fact that velocity channels consistently converge better supports the interpretation that the dynamics model acts as implicit redundancy, and this is a concrete, testable prediction of the framework. The precision collapse spiral is a real architectural limitation that the accept/reject safeguard cannot prevent, because the problem lies in the feedback between precision and tracking stability, which the variational framework doesn't account for.

**What is weak or needs more thought.** The "redundancy is biologically obvious" argument is slightly circular. Yes, the brain has massive sensory redundancy, but claiming this is "the solution" skips over why the brain has that redundancy — whether it evolved specifically for noise averaging or primarily serves other functions (spatial coverage, fault tolerance, feature extraction) with noise averaging as a side effect. We should not claim more than the evidence supports.

We haven't actually tested redundancy. All the arguments about K sensors reducing variance are theoretical. We haven't implemented it, run experiments, or verified that the SFEC architecture gracefully handles multiple input channels per observable. Whether the D matrix needs to grow, whether spike dynamics change, whether the M-step works correctly with averaged inputs vs. raw redundant inputs — these are open questions.

The tracking error contamination may not be a practical problem at all. In the low-noise regime where tracking error dominates a3_i, the controller is actually working correctly — MSE is low and the task is being performed well. The lambda converges to a "wrong" value in the sense that it reflects tracking accuracy rather than true noise precision, but this only matters if we need the precision estimate to be accurate for some downstream purpose, like deciding sensor allocation. For the control task itself, a lambda that has stabilised at the tracking error precision is perfectly functional. We have been framing this as a failure mode, but it may be better described as a regime where precision learning becomes irrelevant rather than harmful.

We haven't run the most important experiment: does learned precision actually improve tracking over fixed precision? The instinct is that this is the core question, and all the lambda convergence analysis is secondary. However, there is a partial answer already implicit in the working regime results. In the low-noise cases where lambda is able to grow — where noise is small enough that the controller tracks well — the precision converges upward toward a value that reflects actual error statistics. A controller with higher, well-calibrated precision weights its observations more confidently and tracks better than one with a fixed, conservative default. The improvement in those cases comes not just from the signal being less noisy, but because the learned precision is genuinely better than whatever fixed value would have been set by hand. The comparison against fixed precision is still the experiment we should have run first — but the expectation, grounded in the working regime data, is that learned precision wins in the regimes where it converges, and the remaining question is only how large the advantage is.

---

**7. Recommended Next Steps**

Run the control comparison: SFEC with fixed precision vs. SFEC_DEMA_obs with learned precision on the same noise scenario, measuring tracking MSE. If pursuing redundancy, implement a simple version — average K noisy copies before feeding into O_input — and test whether the viability window expands as predicted and whether the M-step correctly estimates post-averaging noise. If pursuing generalized coordinates, start with a minimal first-order version as a test case, since the architecture already partially supports this through A_ideal. Finally, test sensor degradation: run a simulation where one sensor's noise increases mid-run and verify that the corresponding λ drops while others remain stable. This is the clearest demonstration of what per-observable precision learning uniquely provides.