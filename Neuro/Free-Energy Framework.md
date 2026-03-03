## Part 1: Perception as Probabilistic Inference

The framework begins with the premise that the sensory cortex acts as an "inference machine". Its job is to figure out the most likely properties of the world based on ambiguous, noisy sensory inputs.


### 1.1 The Generative Model

To understand how the brain infers the world, we first have to define how the brain thinks the world works. This is called a **Generative Model**. Bogacz uses a simple example: an organism trying to infer the size of a food item (v) based on observed light intensity (u).


- **The Likelihood:** The animal knows that light intensity is related to size by a non-linear function g(v), but this process is noisy. This is represented as a normal distribution:
    
    p(u∣v)=f(u;g(v),Σu​)
    
    Where g(v) is the expected light (the "prediction") and Σu​ is the variance or "noise" of the receptor.
    
    
- **The Prior:** The animal also has "street smarts"—prior knowledge of how big food usually is:
    
    p(v)=f(v;vp​,Σp​)
    
    Where vp​ is the expected size and Σp​ is the uncertainty of that expectation.

    

### 1.2 The Computational "Wall"

The goal of perception is to find the **Posterior Distribution**, p(v∣u), which tells the animal how likely different sizes are given the light it just saw. We find this using **Bayes' Theorem**:

p(v∣u)=p(u)p(v)p(u∣v)​

While this looks simple, it is mathematically "expensive" for a biological system for two reasons:

1. **Complexity:** If g(v) is non-linear, the resulting distribution can have a complex, non-standard shape that is hard to represent with simple neurons.
    
2. **The Normalization Problem:** The denominator p(u) requires an integral:
    
    p(u)=∫p(v)p(u∣v)dv
    
    Calculating this integral involves summing over every possible value of v. For a simple organism—or even a human—calculating these high-dimensional integrals in real-time is biologically implausible.
    


---

## The Argument for Approximation

Bogacz argues that the brain doesn't actually try to solve the full Bayesian equation. Instead, it uses a trick: it looks only for the **most likely** value of a feature (the maximum of the distribution), which we denote as ϕ.



Remarkably, by shifting from "calculating a distribution" to "finding a maximum," the complex math of Bayes turns into a simple **gradient ascent** that can be performed by a network of neurons.





## Part 2: Minimizing Surprise via Gradient Ascent

Since we established that calculating the full posterior distribution p(v∣u) is too hard for neurons , the brain instead seeks the value ϕ that maximizes the numerator of Bayes' theorem. This is equivalent to maximizing the logarithm of that numerator, which we define as F:


F=lnp(ϕ)+lnp(u∣ϕ)

### 2.1 Deriving the Objective Function F

By substituting the normal distributions for the prior and the likelihood into the equation above, we get a mathematical expression for our "best guess":


F=21​(−lnΣp​−Σp​(ϕ−vp​)2​−lnΣu​−Σu​(u−g(ϕ))2​)+C



In this equation:

- Σp​(ϕ−vp​)2​ represents how far our guess ϕ is from our prior vp​, weighted by the prior's uncertainty Σp​.
    

    
- Σu​(u−g(ϕ))2​ represents how far the sensory input u is from our predicted input g(ϕ), weighted by the sensory noise Σu​.
    


### 2.2 The Gradient Ascent Rule

To find the peak of this function (the most likely ϕ), the brain uses **gradient ascent**. It changes ϕ over time in the direction that increases F. The rate of change ϕ˙​ is the derivative of F with respect to ϕ:


ϕ˙​=∂ϕ∂F​=Σp​vp​−ϕ​+Σu​u−g(ϕ)​g′(ϕ)


### 2.3 The Birth of Prediction Errors

The genius of this framework is that this messy equation can be simplified by defining two new variables called **prediction errors**:

1. **Prior Prediction Error (ϵp​):** ϵp​=Σp​ϕ−vp​​
    
2. **Sensory Prediction Error (ϵu​):** ϵu​=Σu​u−g(ϕ)​
    

With these definitions, the update rule for our perception becomes elegant and intuitive:

ϕ˙​=ϵu​g′(ϕ)−ϵp​

This means your "perception" (ϕ) is constantly being pushed and pulled by two forces:

- **Sensory input** (ϵu​) tries to pull your guess toward what you are actually seeing.
    
- **Prior knowledge** (ϵp​) tries to pull your guess toward what you expected to see.
    

## 2.4 A Biologically Plausible Circuit

Bogacz proposes that these equations are implemented by specific neural "nodes":

- **State Nodes (ϕ):** These neurons represent the content of your perception.
    
- **Error Nodes (ϵ):** These neurons calculate the difference between predictions and reality.
    

Instead of one neuron doing all the math, the error nodes have their own internal dynamics that naturally converge to the correct values:



- ϵp​˙​=ϕ−vp​−Σp​ϵp​
    
- ϵu​˙​=u−g(ϕ)−Σu​ϵu​
    

---

**Argument Summary:** Perception is not a passive reception of data, but an active dynamical process where state neurons and error neurons engage in a "tug-of-war" until prediction error is minimized.


## Part 3: The Free-Energy Principle and Scaling

The term "Free-Energy" comes from statistical physics and information theory. In this framework, it serves as a mathematical proxy for **surprise**. Since an organism cannot calculate its total "surprise" (the probability of sensory input p(u)) directly due to the normalization integral , it instead minimizes an upper bound called **Variational Free-Energy**.

+4

### 3.1 The "Free" in Free-Energy

Mathematically, the negative free-energy F is defined as the integral of an approximate distribution q(v) against the joint probability of senses and features:

F=∫q(v)lnq(v)p(u,v)​dv

- **The Bound:** By maximizing F, the brain is simultaneously making its internal guess q(v) as close as possible to the true posterior p(v∣u) and maximizing a lower bound on the evidence for its model of the world.
    
    +1
    
- **The Delta Assumption:** To simplify this for neurons, Bogacz assumes q(v) is a **delta distribution**—a single point ϕ. This reduces the complex integral back to the simple objective function we used in Part 2: F=lnp(u,ϕ)+C1​.
    
    +2
    

### 3.2 Scaling Up: Hierarchies and Matrices

The brain doesn't just infer one variable; it infers thousands. To handle this, the math transitions into **Linear Algebra**:

+1

- **Multivariate Inputs:** Instead of single numbers, we use vectors uˉ and ϕˉ​.
    
    +1
    
- **Covariance (Σ):** The uncertainty is no longer a single value but a **Covariance Matrix**, which tracks how different features relate to each other (e.g., how the color of one pixel relates to its neighbor).
    
    +1
    
- **Hierarchy:** The model mirrors the neocortex by stacking these layers. A "prediction" from a higher layer (Area i+1) becomes the "prior" for the layer below (Area i).
    
    +3
    

### 3.3 Learning the Model Parameters

While **perception** is the fast optimization of ϕ, **learning** is the slow optimization of the parameters that define the world's structure: vp​, Σp​, and Σu​.

+1

The brain updates these parameters using the same gradient ascent logic. By taking the derivative of F with respect to the parameters, we find:

- **Prior Mean (vp​):** ∂vp​∂F​=ϵp​. This is **Hebbian**: the connection changes based on the activity of the error node.
    
    +2
    
- **Variance (Σ):** ∂Σp​∂F​=21​(ϵp2​−Σp−1​). This adjusts the "gain" or weight given to certain errors based on how often they occur.
    
    +2
    

---

## The Argument for Attention

This math provides a profound explanation for **Attention**. In this framework, "attending" to a stimulus isn't just looking at it; it is the act of **decreasing the expected variance** (Σ) of that feature. By lowering Σ, the brain mathematically "cranks up" the prediction error, giving that specific sensory input more power to change the activity of the rest of the network.

+4

**In the final part, we will tackle the most difficult hurdle: Local Plasticity. We will see how Bogacz solves the "biological impossibility" of matrix inversion and summarizes why this framework might be the "Grand Unified Theory" of the brain.**



## Part 4: Local Plasticity and the Biological Reality

The "computational wall" in the original Friston model involves how synaptic weights—the connections between neurons—are updated.

### 4.1 The Problem of Non-Locality

In the scaled-up version of the model (Section 4), the rule for updating the covariance matrix Σ (which tracks uncertainty) requires a **matrix inverse** (Σ−1).

- **The Biological Conflict:** Calculating an entry in a matrix inverse requires knowledge of every other entry in that matrix.
    
    +2
    
- **Local Plasticity Violation:** In a real brain, a synapse (the connection weight) only has access to "local" information: the activity of the pre-synaptic neuron and the post-synaptic neuron. It cannot "know" what is happening at a synapse on the other side of the network.
    
    +3
    

### 4.2 The Solution: The Inhibitory Inter-neuron

Bogacz solves this by extending the predictive coding architecture. He introduces a new type of neuron to the circuit: **the inhibitory inter-neuron (ei​)**.

Instead of a single error node trying to do complex division, the computation is split:

+3

1. **Prediction Error Node (ϵi​):** Now simply calculates the difference between the state and the prediction.
    
2. **Inter-neuron (ei​):** Receives input from the error node, weighted by the variance Σi​.
    
    +1
    
3. **Dynamics:** These two nodes engage in a fast-paced feedback loop.
    

**The Result:** At the steady-state (fixed point) of this mini-network, the activity of the error node ϵi​ mathematically converges to exactly the value required by the Free-Energy Principle: the error divided by the variance.

+3

### 4.3 Local Hebbian Learning

By adding this inter-neuron, the learning rule for the synaptic weight Σ becomes strictly **Hebbian**:

+2

ΔΣi​=α(ϵi​ei​−1)

The change in weight now depends _only_ on the activity of the error node (ϵi​) and the inter-neuron (ei​) it is connected to. The brain no longer needs to calculate a matrix inverse; the physics of the neural dynamics "calculate" it automatically through the feedback loop.

+3

---

## Summary of the Arguments

1. **Perception is Optimization:** What we "see" is the result of state nodes (ϕ) and error nodes (ϵ) minimizing a cost function (Free-Energy).
    
    +1
    
2. **Precision Weighting:** The brain doesn't treat all errors equally; it weights them by their reliability (Σ), allowing us to ignore noise and focus on what matters.
    
    +1
    
3. **Hierarchical Prediction:** The cortex is organized so that higher areas predict the activity of lower areas, and lower areas send back "error signals" to refine those predictions.
    
    +2
    
4. **Biological Plausibility:** Through specific micro-circuits (like inhibitory inter-neurons), the brain can implement complex Bayesian mathematics using only simple, local synaptic rules.
    
    +2
    

### Final Insight

The Free-Energy Principle suggests that the very structure of our cortex—its layers, its feedback connections, and its inhibitory neurons—exists specifically to satisfy these mathematical requirements for minimizing surprise