### Objective

To identify why the `SFEC_Precision` controller loses the natural burst-recovery dynamics of the baseline `SFEC`, and to implement strictly local mechanisms to restore stability without relying on a non-local hard reset.

### 1. The Refractory Imbalance (`r_adapt`)

- **Mechanism Discovered:** Precision learning exponentially scales the base threshold (`self.Thr[i]`). Because the spike-frequency adaptation term (`self.r_adapt`) remained a fixed +1 penalty per spike, it lost its mathematical authority over high-precision neurons, effectively deleting their refractory period.
    
- **Test/Implementation:** Introduced `self.adapt_scale = (py_i + pu_i) / base_scale` to perfectly maintain the ratio between the base threshold and the refractory penalty.
    
- **Result:** This successfully eliminated the _infinite, permanent_ burst states (allowing the controller to survive the full 80,000 steps), but the system still exhibited frequent, synchronous burst cascades and a high Mean-Squared Error (MSE) compared to the baseline.
    

### 2. The Row-Scaling Geometry & Perfect Cancellation

- **Mechanism Discovered:** Precision was applied locally by scaling individual rows of the fast recurrent matrix (`O_fast[i, :]`), creating an asymmetric inhibition matrix.
    
- **Mathematical Proof Established:** Evaluating the local threshold geometry proved that the precision multiplier (pyi​+pui​) mathematically cancels out of the neuron's decision-making process:
    
    Ti​Δvi​​=(pyi​+pui​)⋅DtD[i,i](pyi​+pui​)⋅DtD[i,j]​=DtD[i,i]DtD[i,j]​
    
    Because the ratio of incoming inhibition to the local threshold remains mathematically identical, the geometric proportions of the bounding box are perfectly preserved from the perspective of the receiving neuron.
    
- **Resulting Consequence:** Because the precision factors out of the deterministic geometry, high-precision neurons do not gain disproportionate authority over the network's state estimate (μ=Dr). The core control logic remains largely unaffected by the precision weights.
    

### 3. Unscaled Elements and Numerical Artifacts

With the deterministic geometry perfectly balanced, the bursts were isolated to the specific variables that were _not_ scaled by the precision updates.

- **Erased Noise (Synchronous Bursts):**
    
    - _Issue:_ The static voltage noise (`self.sig2`) became mathematically negligible against massively scaled high-precision thresholds, erasing the random tie-breaker required to maintain sparsity. Multiple neurons would hit threshold simultaneously.
        
    - _Test:_ Scaled the noise array by the local precision factor to maintain the noise-to-threshold ratio.
        
- **Trapped Voltage (Drainage Bursts):**
    
    - _Issue:_ When a neuron's precision dropped, its threshold and inhibitory capacity shrank, but its previously accumulated raw voltage (`self.v[i]`) remained massive. The neuron was forced to fire dozens of consecutive spikes just to empty the "ghost" voltage.
        
    - _Test:_ Added an instantaneous voltage rescaling step `self.v[i] = self.v[i] * (self.Thr[i] / old_thr)` during matrix rebuilding to preserve the proportional state of the accumulator.

		I don't think this is a problem, when the lambdas are stable the frecuent burst occur too.
        
- **Dynamics Blindness (Reactive Cascades):**
    
    - _Issue:_ Scaling only the sensory precision (`py_i`) while leaving the dynamics precision (`pu_i`) at 1 dropped the relative ratio of the predictive matrices (`O_slow_dyn` and `O_u_form`) to near-zero. High-precision neurons became blind to the physical inertia of the system, acting as reactive, non-predictive controllers that overshot the target.
        
    - _Test:_ Linked `pu_i` to scale in tandem with `py_i` to preserve the neuron's awareness of the target trajectory and system dynamics.


		This helps the MSE but doesn't solve the problem of the frecuent bursts
        

### Current Status

The local tracking mechanisms (noise, voltage, refractory period, and dynamics) have been mathematically balanced against the row-scaling precision updates. These patches yielded improvements in the MSE. However, the system still exhibits a significantly higher burst frequency than the mathematically symmetric baseline `SFEC`.


It has been seen also how changing the initialization of the Matrix D we can get much less spikes, this happens without r_adaptive proportional to py too

D = np.zeros([size, self.N])

for i in range(self.mu_k):

D[i, 2*i] = 1

D[i, 2*i+1] = -1

for i in range(2*self.mu_k, self.N):

D[:, i] = rng.normal(0, 1, self.mu_k)

shuffled_indices = np.random.permutation(self.N)

self.D = a * D[:, shuffled_indices]/(0.1*self.N)

putting a value of a lower than 1 we can get much lesser spikes but if its too low the MSE starts growing, there is a sweet point though, but it depends on the noise.

If we decide to not relate r_adaptative with py and we multiply the r_adaptative with some value, we get much lesser spikes without modifying the MSE too, but the value depends on the noise too. 

In both cases i feel the burst is happening but it just has much less neurons affected, and therefore we get less spikes but the spikes are not sparse, are always of the same neurons, but its okay because are high precision neurons, but its bad because its always the same ones i think, i don't know if its good or not actually. 


Things done:

Check if with the r_adaptive scaled by py but without pu_i linked to py the highest precision neurons fire more.

No, it didn't make them fire more, it was the  same as without scaling but with more MSE.


## Why fixing `rebuild_row` eliminated the burst problem

The SFEC network represents its state estimate in the variable `v[i]`. The key invariant is that `v[i] = exp(λᵢ) * ṽ[i]`, where `ṽ[i]` is the "SFEC-equivalent" voltage — the value a baseline SFEC neuron would have. Every operator row i is scaled by `exp(λᵢ)`, so `ṽ` dynamics are exactly SFEC regardless of what λᵢ is. The network is stable as long as this invariant holds.

The invariant breaks at the moment of a precision update. When λᵢ increases (the normal case — a quiet period was detected), `exp(λᵢ)` grows, so the threshold `Thr[i]` jumps up proportionally. But the old code left `v[i]` unchanged. In ṽ-space this looks like `ṽ[i]` suddenly shrank — the neuron now under-represents its contribution to `μ = D@r`. To compensate, it needs to fire more to push `r[i]` back up, which drives other neurons above threshold, which cascades into a burst.

The fix is simply to rescale `v[i]` by the same factor the threshold changed — `exp(λ_new - λ_old)` — so that `ṽ[i]` is continuous across the update. `r_adapt[i]` is divided by the same factor because it contributes to the threshold as `r_adapt[i] * adapt_scale[i]`, and `adapt_scale[i]` just grew by that factor, so the product must stay constant.

In short: **the precision update was changing the ruler without moving the measurement, so the neuron saw a phantom error and bursted to correct it. Rescaling `v[i]` keeps the measurement consistent with the new ruler.**


Current Status:

Frequent Burst solved, but now there is no difference between SFEC and SFEC_Precision behaviors so we did nothing, now its like the neuron knows how noisy it is but it use it for nothing. The next step is deriving from Active Inference framework, how to use this knowledge in order to make a better controller. 


Things to do: 

know why with r_adaptative and pmu following 100% py the controller doesn't behave exactly like SFEC, and it keep having frecuent burst, even though is recovering.

Explore if we can get some astrocytes to regulate the high potassium concetration on high spiking neurons, i don't know if that approach could help us, maybe instead of an instant lowering voltage from O_fast something that is more long term, not as long term as the precision updating but some lowering.

Explore if we can get lambdas related to sensory obs with it being local

