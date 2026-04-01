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
        
- **Dynamics Blindness (Reactive Cascades):**
    
    - _Issue:_ Scaling only the sensory precision (`py_i`) while leaving the dynamics precision (`pu_i`) at 1 dropped the relative ratio of the predictive matrices (`O_slow_dyn` and `O_u_form`) to near-zero. High-precision neurons became blind to the physical inertia of the system, acting as reactive, non-predictive controllers that overshot the target.
        
    - _Test:_ Linked `pu_i` to scale in tandem with `py_i` to preserve the neuron's awareness of the target trajectory and system dynamics.
        

### Current Status

The local tracking mechanisms (noise, voltage, refractory period, and dynamics) have been mathematically balanced against the row-scaling precision updates. These patches yielded improvements in the MSE. However, the system still exhibits a significantly higher burst frequency than the mathematically symmetric baseline `SFEC`.