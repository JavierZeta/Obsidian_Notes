
Spiking Free-Energy State Estimator
===================================

Complete derivation from the free-energy principle through precision learning

1\. Motivation and foundational idea
------------------------------------

The free-energy principle holds that a self-organising system minimises a functional called variational free energy — a bound on the surprise of its sensory observations — by adjusting its internal states. In the computational neuroscience formulation this functional takes the form of a precision-weighted sum of prediction errors. When the internal states are represented by a _population of spiking neurons_, each spike must reduce free energy: a neuron fires when and only when doing so drives the free energy down. This is the Spiking Free-Energy Constrainer (SFEC) principle introduced by André et al.

André's original construction couples the estimator to a control target, so the internal dynamics term conflates the quality of the state prediction with the progress toward a behavioural goal. The estimator derived here removes that coupling entirely. There is no target, no control output, and no cost on actions. The only objective is accurate state estimation.

* * *

2\. System setup
----------------

### 2.1 The plant

Consider a continuous-time linear plant with Euler-discretised or ZOH-discretised measurements:

\\\[ \\dot{x} = A\_{\\mathrm{int}}\\,x + d\_w, \\qquad y\_t = C\\,x\_t + d\_\\eta \\\]

where \\(x \\in \\mathbb{R}^{n}\\) is the hidden state, \\(y\_t \\in \\mathbb{R}^{m}\\) is the observation at time \\(t\\), \\(d\_w \\sim \\mathcal{N}(0, Q\_c\\,dt)\\) is process noise, and \\(d\_\\eta \\sim \\mathcal{N}(0, R\_c\\,dt)\\) is observation noise. The matrices \\(Q\_c\\) and \\(R\_c\\) are the true continuous-time noise covariances.

### 2.2 The neural code

The internal state estimate \\(\\boldsymbol{\\mu} \\in \\mathbb{R}^n\\) is represented as a weighted sum of decoder columns:

\\\[ \\boldsymbol{\\mu} = D\\mathbf{r}, \\qquad D \\in \\mathbb{R}^{n \\times N} \\\]

where \\(\\mathbf{r} \\in \\mathbb{R}^N\\) is the vector of filtered spike counts (membrane traces) and \\(D\\) is the fixed decoder matrix. The network is _overcomplete_: \\(N \\gg n\\). Each column \\(D\_i\\) is the preferred decoding direction of neuron \\(i\\).

Spike counts evolve according to leaky integration:

\\\[ \\dot{\\mathbf{r}} = -\\tau\\,\\mathbf{r} + \\mathbf{s} \\\]

where \\(\\tau > 0\\) is the membrane leak constant and \\(\\mathbf{s} \\in \\{0,1\\}^N\\) is the instantaneous spike vector.

### 2.3 The predictive prior

At the start of each timestep, the network forms a _predictive prior_ by propagating the previous posterior estimate through the known discrete dynamics:

\\\[ \\boldsymbol{\\mu}\_t^- = \\Phi\\,\\boldsymbol{\\mu}\_{t-1}, \\qquad \\Phi = e^{A\_{\\mathrm{int}}\\,\\Delta t} \\approx I + \\Delta t\\,A\_{\\mathrm{int}} \\\]

This is the one-step prior mean. It is held constant during the inner spike-relaxation window of the current timestep, so \\(\\dot{\\boldsymbol{\\mu}}^- = 0\\) within a step.

This is the fundamental difference from André's controller. André's dynamics term uses a target \\(z\_t\\) to form \\(A\_{\\mathrm{int}}\\mu - \\mu\_{\\mathrm{target}}\\), mixing estimation with control. Here \\(\\boldsymbol{\\mu}^-\\) comes purely from the state-transition prediction, so the prior precision has a clean Bayesian meaning: how confident is the model in its own state-transition prediction?

* * *

3\. The free-energy functional
------------------------------

The variational free energy for the estimator is a precision-weighted sum of two prediction errors plus an optional spike-cost term:

Estimator free energy

\\\[ \\mathcal{F}(\\boldsymbol{\\mu}, \\mathbf{r}) = \\underbrace{(\\mathbf{y} - C\\boldsymbol{\\mu})^T \\Pi\_y (\\mathbf{y} - C\\boldsymbol{\\mu})}\_{\\text{sensory error}} + \\underbrace{(\\boldsymbol{\\mu} - \\boldsymbol{\\mu}^-)^T \\Pi\_\\mu (\\boldsymbol{\\mu} - \\boldsymbol{\\mu}^-)}\_{\\text{transition prior error}} + \\beta\\,\\mathbf{r}^T\\mathbf{r} \\\]

where \\(\\Pi\_y \\in \\mathbb{R}^{m\\times m}\\) is the observation precision matrix, \\(\\Pi\_\\mu \\in \\mathbb{R}^{n\\times n}\\) is the prior precision matrix, and \\(\\beta \\geq 0\\) is the spike-cost coefficient. The matrices are related to the noise covariances through \\(\\Pi\_y = R\_d^{-1}\\) and \\(\\Pi\_\\mu = (P\_t^-)^{-1}\\) where \\(P\_t^-\\) is the one-step predictive error covariance.

Define the combined precision-weighted measurement matrix:

\\\[ M = C^T \\Pi\_y C + \\Pi\_\\mu \\\]

and the combined precision-weighted target vector (the information-form right-hand side):

\\\[ \\mathbf{q}\_t = C^T \\Pi\_y \\mathbf{y}\_t + \\Pi\_\\mu \\boldsymbol{\\mu}\_t^- \\\]

The exact minimiser of \\(\\mathcal{F}\\) with respect to \\(\\boldsymbol{\\mu}\\) (setting \\(\\beta = 0\\)) is:

\\\[ \\boldsymbol{\\mu}\_t^\\star = M^{-1}\\mathbf{q}\_t = (C^T\\Pi\_y C + \\Pi\_\\mu)^{-1}(C^T\\Pi\_y\\mathbf{y}\_t + \\Pi\_\\mu\\boldsymbol{\\mu}\_t^-) \\\]

This is exactly the information-form Bayesian fusion of measurement and prior — the same computation as one step of a Kalman filter with \\(\\Pi\_y = R\_d^{-1}\\) and \\(\\Pi\_\\mu = (P\_t^-)^{-1}\\).

* * *

4\. Deriving the spike condition
--------------------------------

### 4.1 Single-spike free-energy change

When neuron \\(i\\) fires, the spike count vector changes by one unit: \\(\\mathbf{r} \\to \\mathbf{r} + \\mathbf{e}\_i\\), and so the estimate changes by the \\(i\\)-th decoder column: \\(\\boldsymbol{\\mu} \\to \\boldsymbol{\\mu} + D\_i\\). A spike is beneficial if and only if it strictly decreases the free energy:

\\\[ \\Delta\\mathcal{F}\_i = \\mathcal{F}(\\boldsymbol{\\mu} + D\_i,\\, \\mathbf{r} + \\mathbf{e}\_i) - \\mathcal{F}(\\boldsymbol{\\mu},\\, \\mathbf{r}) < 0 \\\]

### 4.2 Expanding the sensory term

Let \\(\\boldsymbol{\\epsilon}\_y = \\mathbf{y} - C\\boldsymbol{\\mu}\\). After the spike, the sensory error becomes \\(\\boldsymbol{\\epsilon}\_y - CD\_i\\). The change in the sensory term is:

\\\[ (\\boldsymbol{\\epsilon}\_y - CD\_i)^T\\Pi\_y(\\boldsymbol{\\epsilon}\_y - CD\_i) - \\boldsymbol{\\epsilon}\_y^T\\Pi\_y\\boldsymbol{\\epsilon}\_y = -2\\boldsymbol{\\epsilon}\_y^T\\Pi\_y C D\_i + D\_i^T C^T\\Pi\_y C\\,D\_i \\\]

### 4.3 Expanding the prior term

Let \\(\\boldsymbol{\\epsilon}\_\\mu = \\boldsymbol{\\mu} - \\boldsymbol{\\mu}^-\\). After the spike the prior error becomes \\(\\boldsymbol{\\epsilon}\_\\mu + D\_i\\). The change in the prior term is:

\\\[ (\\boldsymbol{\\epsilon}\_\\mu + D\_i)^T\\Pi\_\\mu(\\boldsymbol{\\epsilon}\_\\mu + D\_i) - \\boldsymbol{\\epsilon}\_\\mu^T\\Pi\_\\mu\\boldsymbol{\\epsilon}\_\\mu = 2\\boldsymbol{\\epsilon}\_\\mu^T\\Pi\_\\mu D\_i + D\_i^T\\Pi\_\\mu D\_i \\\]

### 4.4 Expanding the spike-cost term

The spike-cost contribution is:

\\\[ \\beta\\,(\\mathbf{r}+\\mathbf{e}\_i)^T(\\mathbf{r}+\\mathbf{e}\_i) - \\beta\\,\\mathbf{r}^T\\mathbf{r} = \\beta\\,(2r\_i + 1) \\\]

### 4.5 Collecting all terms

Summing the three contributions:

\\\[ \\Delta\\mathcal{F}\_i = -2D\_i^T\\!\\left\[C^T\\Pi\_y(\\mathbf{y} - C\\boldsymbol{\\mu}) - \\Pi\_\\mu(\\boldsymbol{\\mu} - \\boldsymbol{\\mu}^-)\\right\] + D\_i^T M D\_i + \\beta(2r\_i+1) \\\]

Now simplify the bracket. Expanding the two inner terms:

\\\[ C^T\\Pi\_y(\\mathbf{y} - C\\boldsymbol{\\mu}) - \\Pi\_\\mu(\\boldsymbol{\\mu} - \\boldsymbol{\\mu}^-) = C^T\\Pi\_y\\mathbf{y} + \\Pi\_\\mu\\boldsymbol{\\mu}^- - (C^T\\Pi\_y C + \\Pi\_\\mu)\\boldsymbol{\\mu} = \\mathbf{q}\_t - M\\boldsymbol{\\mu} = \\mathbf{q}\_t - MD\\mathbf{r} \\\]

Substituting back:

\\\[ \\Delta\\mathcal{F}\_i = -2D\_i^T(\\mathbf{q}\_t - MD\\mathbf{r}) + D\_i^T M D\_i + \\beta(2r\_i+1) \\\]

### 4.6 The spike condition

For the spike to reduce free energy we need \\(\\Delta\\mathcal{F}\_i < 0\\). Dividing by 2:

\\\[ D\_i^T(\\mathbf{q}\_t - MD\\mathbf{r}) - \\tfrac{1}{2}D\_i^T M D\_i - \\beta(r\_i + \\tfrac{1}{2}) > 0 \\\]

This defines a natural voltage and a natural threshold for neuron \\(i\\):

Spike rule — neuron \\(i\\) fires when \\(v\_i > T\_i\\)

\\\[ v\_i = D\_i^T\\!\\left\[\\mathbf{q}\_t - MD\\mathbf{r}\\right\] = D\_i^T(\\mathbf{q}\_t - M\\boldsymbol{\\mu}) \\\] \\\[ T\_i = \\tfrac{1}{2}\\,D\_i^T M D\_i + \\beta\\!\\left(r\_i + \\tfrac{1}{2}\\right) \\\]

* * *

5\. Vector form of the voltage
------------------------------

Writing the voltages of all neurons simultaneously, substitute \\(\\mathbf{q}\_t = C^T\\Pi\_y\\mathbf{y} + \\Pi\_\\mu\\boldsymbol{\\mu}^-\\):

\\\[ \\mathbf{v} = D^T\\mathbf{q}\_t - D^T M D\\mathbf{r} = D^T C^T\\Pi\_y\\,\\mathbf{y} + D^T\\Pi\_\\mu\\,\\boldsymbol{\\mu}^- - D^T M D\\,\\mathbf{r} \\\]

Identifying the three weight matrices:

Voltage decomposition

\\\[ \\mathbf{v} = W\_y\\,\\mathbf{y} + W\_p\\,\\boldsymbol{\\mu}^- - O\\,\\mathbf{r} \\\] \\\[ W\_y = D^T C^T \\Pi\_y \\quad\\text{(sensory feedforward)} \\\] \\\[ W\_p = D^T \\Pi\_\\mu \\quad\\text{(predictive prior input)} \\\] \\\[ O = D^T M D = D^T(C^T\\Pi\_y C + \\Pi\_\\mu)D \\quad\\text{(recurrent inhibition)} \\\]

Base threshold

\\\[T\_i^{\\mathrm{base}} = \\tfrac{1}{2}\\,O\_{ii}\\\]

Adaptive threshold

\\\[T\_i = T\_i^{\\mathrm{base}} + \\beta\\!\\left(r\_i + \\tfrac{1}{2}\\right)\\\]

The threshold adapts with the neuron's own activity: neurons that have fired recently have a higher threshold, implementing automatic gain control and sparse representation.

* * *

6\. Voltage dynamics
--------------------

To derive how the voltage evolves between spikes, differentiate the voltage definition with respect to time, holding \\(\\mathbf{y}\\) and \\(\\boldsymbol{\\mu}^-\\) constant during the inner ZOH window (since \\(\\dot{\\boldsymbol{\\mu}}^- = 0\\) within a timestep):

\\\[ \\dot{\\mathbf{v}} = W\_y\\dot{\\mathbf{y}} + W\_p\\dot{\\boldsymbol{\\mu}}^- - O\\dot{\\mathbf{r}} \\\]

During the ZOH window, \\(\\dot{\\boldsymbol{\\mu}}^- = 0\\). Substituting \\(\\dot{\\mathbf{r}} = -\\tau\\mathbf{r} + \\mathbf{s}\\):

\\\[ \\dot{\\mathbf{v}} = W\_y\\dot{\\mathbf{y}} - O(-\\tau\\mathbf{r} + \\mathbf{s}) = W\_y\\dot{\\mathbf{y}} + \\tau O\\mathbf{r} - O\\mathbf{s} \\\]

Now substitute back using \\(\\mathbf{v} = W\_y\\mathbf{y} + W\_p\\boldsymbol{\\mu}^- - O\\mathbf{r}\\), so \\(O\\mathbf{r} = \\mathbf{b} - \\mathbf{v}\\) where \\(\\mathbf{b} = W\_y\\mathbf{y} + W\_p\\boldsymbol{\\mu}^-\\) is the bias current:

\\\[ \\dot{\\mathbf{v}} = -\\tau\\mathbf{v} + \\tau\\mathbf{b} + \\dot{\\mathbf{b}} - O\\mathbf{s} \\\]

Under ZOH (\\(\\dot{\\mathbf{b}} = 0\\)), this simplifies to the canonical leaky-integrator form with recurrent inhibition:

Voltage dynamics (ZOH inner window)

\\\[ \\dot{\\mathbf{v}} = -\\tau\\mathbf{v} + \\tau(W\_y\\mathbf{y} + W\_p\\boldsymbol{\\mu}^-) - O\\mathbf{s} \\\]

The positive-definite matrix \\(O\\) ensures that each spike immediately inhibits the whole network proportionally to the columns of \\(D\\). The leak term \\(-\\tau\\mathbf{v}\\) drives the voltage toward the current bias current. Together these implement a continuous relaxation toward the minimum of the free energy.

An important stability clarification: writing the dynamics in terms of \\(\\mathbf{r}\\) gives an apparent \\(+\\tau O\\mathbf{r}\\) term which looks destabilising since \\(O \\succ 0\\). But after rewriting in terms of \\(\\mathbf{v}\\) the same system has the standard negative-leak \\(-\\tau\\mathbf{v}\\), which is stable. The positive-definiteness of \\(O\\) is not a stability problem — it is a coordinate artifact of the \\(\\mathbf{r}\\)-representation.

* * *

7\. Between-step prior update
-----------------------------

At the transition between observation steps, the bias current \\(\\mathbf{b}\\) changes because both \\(\\mathbf{y}\\) and \\(\\boldsymbol{\\mu}^-\\) jump. This contributes an instantaneous voltage impulse equal to the change in bias:

\\\[ \\mathbf{v}(t^+\_{\\mathrm{new}}) = \\mathbf{v}(t^-\_{\\mathrm{old}}) + \\Delta\\mathbf{b}, \\qquad \\Delta\\mathbf{b} = \\mathbf{b}\_{\\mathrm{new}} - \\mathbf{b}\_{\\mathrm{old}} \\\]

where \\(\\mathbf{b}\_{\\mathrm{new}} = W\_y\\mathbf{y}\_t + W\_p\\boldsymbol{\\mu}\_t^-\\) uses the new observation and new prior, and \\(\\boldsymbol{\\mu}\_t^- = \\Phi\\boldsymbol{\\mu}\_{t-1}\\). This step is implemented in code as `self.v += b_new - self.b`.

* * *

8\. Complete estimator summary
------------------------------

Full equations — target-free SFEC estimator

\\\[ \\textbf{Prior:}\\quad \\boldsymbol{\\mu}\_t^- = \\Phi\\,\\boldsymbol{\\mu}\_{t-1}, \\qquad \\Phi \\approx I + \\Delta t\\,A\_{\\mathrm{int}} \\\] \\\[ \\textbf{Information vector:}\\quad \\mathbf{q}\_t = C^T\\Pi\_y\\mathbf{y}\_t + \\Pi\_\\mu\\boldsymbol{\\mu}\_t^- \\\] \\\[ \\textbf{Curvature:}\\quad M = C^T\\Pi\_y C + \\Pi\_\\mu, \\qquad O = D^T M D \\\] \\\[ \\textbf{Voltage:}\\quad v\_i = D\_i^T(\\mathbf{q}\_t - MD\\mathbf{r}) \\\] \\\[ \\textbf{Threshold:}\\quad T\_i = \\tfrac{1}{2}O\_{ii} + \\beta(r\_i + \\tfrac{1}{2}) \\\] \\\[ \\textbf{Dynamics:}\\quad \\dot{\\mathbf{v}} = -\\tau\\mathbf{v} + \\tau\\mathbf{b} - O\\mathbf{s}, \\quad \\mathbf{b} = W\_y\\mathbf{y} + W\_p\\boldsymbol{\\mu}^- \\\] \\\[ \\textbf{Estimate:}\\quad \\boldsymbol{\\mu} = D\\mathbf{r}, \\qquad \\dot{\\mathbf{r}} = -\\tau\\mathbf{r} + \\mathbf{s} \\\]

The exact Bayesian optimum (with \\(\\beta = 0\\)) is \\(\\boldsymbol{\\mu}^\\star = M^{-1}\\mathbf{q}\_t\\), recovering the information-form Kalman update. The spiking network approximates this solution through local threshold crossings.

When \\(C = I\\) and both precisions are scalar (\\(\\Pi\_y = \\pi\_y I\\), \\(\\Pi\_\\mu = \\pi\_\\mu I\\)), the optimal estimate reduces to a precision-weighted mean:

\\\[ \\boldsymbol{\\mu}\_t^\\star = \\frac{\\pi\_y\\,\\mathbf{y}\_t + \\pi\_\\mu\\,\\boldsymbol{\\mu}\_t^-}{\\pi\_y + \\pi\_\\mu} = \\frac{1}{1+\\rho}\\mathbf{y}\_t + \\frac{\\rho}{1+\\rho}\\boldsymbol{\\mu}\_t^-, \\qquad \\rho = \\frac{\\pi\_\\mu}{\\pi\_y} \\\]

The ratio \\(\\rho\\) is therefore the core Bayesian quantity: it determines how much the estimator trusts its own prediction relative to the new observation. The theoretically optimal value is:

\\\[ \\rho^\\star = \\frac{\\mathrm{tr}(R\_d)}{\\mathrm{tr}(P\_t^-)}, \\qquad P\_t^- = \\Phi P\_{t-1}\\Phi^T + Q\_d \\\]

* * *

9\. Precision learning — motivation
-----------------------------------

The estimator above uses fixed precision matrices \\(\\Pi\_y\\) and \\(\\Pi\_\\mu\\). In a real neural system, these quantities must be learned from local evidence: the system does not have access to the true noise covariances \\(R\_c\\) and \\(Q\_c\\). Two approaches are developed below, both derived from the free-energy principle and both strictly local in the sense that all computations happen within identifiable neural populations.

Before presenting either approach, recall the key insight about common-scale cancellation. If both precisions are scaled by the same factor \\(\\alpha\\):

\\\[ \\Pi\_y \\to \\alpha\\Pi\_y, \\quad \\Pi\_\\mu \\to \\alpha\\Pi\_\\mu \\implies M \\to \\alpha M,\\; O \\to \\alpha O,\\; T\_i \\to \\alpha T\_i,\\; v\_i \\to \\alpha v\_i \\\]

The spike condition \\(v\_i > T\_i\\) is invariant under common scaling (at \\(\\beta = 0\\)). So the only quantity that matters for inference is the _ratio_ \\(\\rho\\), not the absolute scale. Any precision-learning rule that only changes the common scale learns nothing useful about the Bayesian tradeoff. This was the core problem with the earlier approach.

* * *

10\. Precision learning: Method I — neuron-space ratio learner
--------------------------------------------------------------

### 10.1 Conceptual basis

This method stays as close as possible to the existing spiking architecture. Each neuron \\(i\\) maintains a single local variable \\(\\xi\_i\\) — its log precision ratio — and uses it to modulate its own two input branches independently. No new neural populations are introduced.

### 10.2 Factorising the voltage into two branches

Decompose the voltage of neuron \\(i\\) into a sensory branch and a prior branch:

\\\[ I\_i^y = \\left(W\_y^0\\,\\mathbf{y} - O^0\_y\\,\\mathbf{r}\\right)\_i, \\qquad W\_y^0 = D^T C^T,\\; O^0\_y = D^T C^T C D \\\]

\\\[ I\_i^\\mu = \\left(W\_p^0\\,\\boldsymbol{\\mu}^- - O^0\_\\mu\\,\\mathbf{r}\\right)\_i, \\qquad W\_p^0 = D^T,\\; O^0\_\\mu = D^T D \\\]

Both are computed at unit precision (\\(\\pi\_y = \\pi\_\\mu = 1\\)). The full voltage is then:

\\\[ v\_i = \\pi\_i^y\\,I\_i^y + \\pi\_i^\\mu\\,I\_i^\\mu \\\]

and the threshold correspondingly:

\\\[ T\_i = \\tfrac{1}{2}\\left(\\pi\_i^y\\,(O^0\_y)\_{ii} + \\pi\_i^\\mu\\,(O^0\_\\mu)\_{ii}\\right) + \\beta(r\_i+\\tfrac{1}{2}) \\\]

### 10.3 Parameterisation via log-ratio and common gain

Introduce per-neuron log variables so that precisions are always positive:

\\\[ \\pi\_i^y = e^{g\_i - \\xi\_i/2}, \\qquad \\pi\_i^\\mu = e^{g\_i + \\xi\_i/2} \\\]

where \\(g\_i\\) is the common log-gain (fixed initially, or adapted homeostatically) and \\(\\xi\_i\\) is the log precision-ratio variable. The ratio is:

\\\[ \\rho\_i = \\frac{\\pi\_i^\\mu}{\\pi\_i^y} = e^{\\xi\_i} \\\]

### 10.4 Deriving the local learning rule from free energy

Include log-precision terms in the free energy to avoid the trivial collapse toward zero precision. For diagonal precisions and a single channel the relevant term is:

\\\[ \\mathcal{F}\_\\lambda = e^\\lambda\\,a^2 - \\lambda T \\\]

where \\(a^2\\) is the squared local error current and \\(T\\) is the accumulation window length. This is the form used in the original precision-learning scheme. The gradient with respect to the log-precision \\(\\lambda\\) is:

\\\[ \\frac{\\partial \\mathcal{F}\_\\lambda}{\\partial \\lambda} = e^\\lambda\\,a^2 - T = \\pi\\,a^2 - T \\\]

At equilibrium, \\(\\pi\\,\\overline{a^2} = 1\\), i.e. the precision-weighted squared error equals unity. This is the _whitening condition_.

For the ratio variable \\(\\xi\_i\\), the relevant free energy component is the difference of the two branch energies. Differentiating the total free energy with respect to \\(\\xi\_i\\) at fixed \\(g\_i\\):

\\\[ \\frac{\\partial \\mathcal{F}}{\\partial \\xi\_i} = \\tfrac{1}{2}\\left(\\pi\_i^\\mu\\,\\overline{(I\_i^\\mu)^2} - \\pi\_i^y\\,\\overline{(I\_i^y)^2}\\right) \\\]

The resulting local ratio-update rule is:

Method I — log-ratio update (gradient descent on \\(\\mathcal{F}\\))

\\\[ \\tau\_\\xi\\,\\dot{\\xi}\_i = \\eta\_\\xi\\!\\left(\\pi\_i^y\\,q\_i^y - \\pi\_i^\\mu\\,q\_i^\\mu\\right) - \\kappa\_\\xi\\,\\xi\_i \\\] \\\[ \\tau\_q\\,\\dot{q}\_i^y = -q\_i^y + (I\_i^y)^2, \\qquad \\tau\_q\\,\\dot{q}\_i^\\mu = -q\_i^\\mu + (I\_i^\\mu)^2 \\\]

where \\(q\_i^y\\) and \\(q\_i^\\mu\\) are slow low-pass squared-error traces. The decay term \\(-\\kappa\_\\xi\\xi\_i\\) is a soft prior on \\(\\xi\_i\\) centered at zero (equal precisions), which prevents unbounded drift.

### 10.5 Equilibrium interpretation

At equilibrium \\(\\dot{\\xi}\_i = 0\\):

\\\[ \\pi\_i^y\\,\\overline{(I\_i^y)^2} = \\pi\_i^\\mu\\,\\overline{(I\_i^\\mu)^2} \\quad (\\text{plus the regularisation term}) \\\]

The ratio shifts until the precision-weighted energy in the sensory branch equals the precision-weighted energy in the prior branch. Concretely:

*   If sensory errors dominate: \\((I\_i^y)^2 \\gg (I\_i^\\mu)^2\\) → \\(\\pi\_i^y\\) falls, \\(\\pi\_i^\\mu\\) rises → estimator trusts the prior more.
*   If prior errors dominate: \\((I\_i^\\mu)^2 \\gg (I\_i^y)^2\\) → \\(\\pi\_i^\\mu\\) falls, \\(\\pi\_i^y\\) rises → estimator trusts the observation more.

### 10.6 Constraints and caveats

This method is fully local in neuron space: each neuron reads only its own branch currents, its own slow traces, and updates its own \\(\\xi\_i\\). However it learns a per-neuron ratio, not a per-state-channel ratio. For decoder columns that tile a shared state subspace (e.g. ±\\(D\_j\\) pairs), the two members of a pair must share one \\(\\xi\\) variable. Otherwise the asymmetric scaling breaks the bounding geometry of the SFEC spike condition.

The common scale \\(g\_i\\) can be adapted on a still-slower timescale toward a homeostatic target firing rate without affecting the ratio or the Bayesian inference quality.

* * *

11\. Precision learning: Method II — factorised error-precision circuit
-----------------------------------------------------------------------

### 11.1 Conceptual basis

Method I learns precision in neuron space and works well for overcomplete codes, but the learned quantity is a projection of the true precision onto individual neurons. Method II instead places the precision variable in the correct _channel space_ — the observation space and the state space respectively — and implements this through dedicated neural sub-populations. The result is more interpretable and more consistent with the original Bayesian meaning of the precisions.

The key insight is that the matrix notation hides local structure. Write the voltage as:

\\\[ v\_i = D\_i^T(\\mathbf{q}\_t - M\\boldsymbol{\\mu}) = \\sum\_l (CD)\_{li}\\,\\pi\_y^l\\,\\epsilon\_y^l + \\sum\_k D\_{ki}\\,\\pi\_\\mu^k\\,\\epsilon\_\\mu^k \\\]

where \\(\\epsilon\_y^l = y\_l - (C\\boldsymbol{\\mu})\_l\\) is the residual in observation channel \\(l\\), and \\(\\epsilon\_\\mu^k = \\mu\_k^- - \\mu\_k\\) is the residual in state channel \\(k\\). Each of these quantities can be computed locally by a small dedicated population.

### 11.2 Neural sub-populations

📍 Coding neurons \\(\\mathbf{r}\\)

→

👁 Sensory error \\(\\boldsymbol{\\epsilon}\_y\\)

→

⚖ Precision \\(\\pi\_y^l\\)

📍 Coding neurons \\(\\mathbf{r}\\)

→

🔮 Prior error \\(\\boldsymbol{\\epsilon}\_\\mu\\)

→

⚖ Precision \\(\\pi\_\\mu^k\\)

Concretely:

\\\[ \\textbf{Sensory error neurons (dim }m\\textbf{):}\\quad \\epsilon\_y^l = y\_l - \\sum\_i (CD)\_{li}\\,r\_i \\\]

\\\[ \\textbf{Prior error neurons (dim }n\\textbf{):}\\quad \\epsilon\_\\mu^k = \\mu\_k^- - \\sum\_i D\_{ki}\\,r\_i \\\]

\\\[ \\textbf{Precision neurons (dim }m+n\\textbf{):}\\quad \\pi\_y^l = e^{\\lambda\_y^l}, \\quad \\pi\_\\mu^k = e^{\\lambda\_\\mu^k} \\\]

All matrices (\\(CD\\) and \\(D\\)) are fixed synaptic weights. The precision neurons are slow modulatory units that multiply the error-neuron signals before feeding back to the coding neurons. All computation is carried by identified neural populations — there is no external matrix algebra.

### 11.3 Voltage as local synaptic currents

The voltage of coding neuron \\(i\\) is now written as a sum of precision-gated local currents:

Method II — voltage as precision-gated currents

\\\[ v\_i = \\sum\_{l=1}^{m} (CD)\_{li}\\,\\pi\_y^l\\,\\epsilon\_y^l \\;+\\; \\sum\_{k=1}^{n} D\_{ki}\\,\\pi\_\\mu^k\\,\\epsilon\_\\mu^k \\\]

The threshold is correspondingly:

\\\[ T\_i = \\frac{1}{2}\\!\\left(\\sum\_l \\pi\_y^l\\,(CD)\_{li}^2 + \\sum\_k \\pi\_\\mu^k\\,D\_{ki}^2\\right) + \\beta\\!\\left(r\_i + \\tfrac{1}{2}\\right) \\\]

This is the self-effect of neuron \\(i\\)'s own spike propagating back through the same local loops — no global computation needed.

### 11.4 Free energy with log-precision terms

The full free energy to be minimised over both \\(\\boldsymbol{\\mu}\\) and the log-precisions is:

\\\[ \\mathcal{F} = \\sum\_l \\pi\_y^l\\,(\\epsilon\_y^l)^2 - \\sum\_l \\log\\pi\_y^l + \\sum\_k \\pi\_\\mu^k\\,(\\epsilon\_\\mu^k)^2 - \\sum\_k \\log\\pi\_\\mu^k + \\beta\\,\\mathbf{r}^T\\mathbf{r} \\\]

The log-determinant terms \\(-\\log\\pi\\) prevent the trivial solution \\(\\pi \\to 0\\). Taking the gradient with respect to each log-precision:

\\\[ \\frac{\\partial \\mathcal{F}}{\\partial \\lambda\_y^l} = \\pi\_y^l\\,(\\epsilon\_y^l)^2 - 1, \\qquad \\frac{\\partial \\mathcal{F}}{\\partial \\lambda\_\\mu^k} = \\pi\_\\mu^k\\,(\\epsilon\_\\mu^k)^2 - 1 \\\]

### 11.5 Local learning rules

Each precision neuron performs gradient descent on the free energy through its own slow trace:

Method II — precision learning rules (active-inference gradient descent)

\\\[ \\tau\_q\\,\\dot{q}\_y^l = -q\_y^l + (\\epsilon\_y^l)^2, \\qquad \\tau\_\\lambda\\,\\dot{\\lambda}\_y^l = \\eta\_\\lambda(1 - \\pi\_y^l\\,q\_y^l) - \\kappa\_\\lambda(\\lambda\_y^l - \\lambda\_y^0) \\\] \\\[ \\tau\_q\\,\\dot{q}\_\\mu^k = -q\_\\mu^k + (\\epsilon\_\\mu^k)^2, \\qquad \\tau\_\\lambda\\,\\dot{\\lambda}\_\\mu^k = \\eta\_\\lambda(1 - \\pi\_\\mu^k\\,q\_\\mu^k) - \\kappa\_\\lambda(\\lambda\_\\mu^k - \\lambda\_\\mu^0) \\\]

where \\(q\_y^l\\) and \\(q\_\\mu^k\\) are slow exponential moving averages of the squared channel errors, \\(\\eta\_\\lambda\\) is the learning rate, and \\(\\kappa\_\\lambda(\\lambda - \\lambda\_0)\\) is a soft prior keeping precisions near a default value.

### 11.6 Equilibrium conditions

At equilibrium, \\(\\dot{\\lambda} = 0\\) gives the whitening conditions:

\\\[ \\pi\_y^l\\,\\overline{(\\epsilon\_y^l)^2} \\approx 1 \\quad \\forall\\,l, \\qquad \\pi\_\\mu^k\\,\\overline{(\\epsilon\_\\mu^k)^2} \\approx 1 \\quad \\forall\\,k \\\]

The precision neuron adjusts its gain until the precision-weighted squared error in its channel equals one — a local residual whitening criterion. This is the same condition that appears in variational Bayes and expectation-maximisation for Gaussian models.

### 11.7 Ratio extraction (for analysis)

For the case \\(C = I\\) and matched channels (\\(m = n\\)), the precision ratio for each state dimension \\(k\\) is directly readable from the two precision neurons:

\\\[ \\rho\_k(t) = \\frac{\\pi\_\\mu^k(t)}{\\pi\_y^k(t)} = e^{\\lambda\_\\mu^k(t) - \\lambda\_y^k(t)} \\\]

Under the whitening equilibrium conditions:

\\\[ \\rho\_k^\\star \\approx \\frac{\\overline{(\\epsilon\_y^k)^2}}{\\overline{(\\epsilon\_\\mu^k)^2}} = \\frac{R\_d^{kk}}{(P\_t^-)^{kk}} \\\]

matching the Kalman-optimal ratio for each diagonal channel separately. This is the precise formal sense in which Method II learns the "correct" Bayesian ratio.

* * *

12\. Comparison of the two methods
----------------------------------

Method I — neuron-space ratio

One \\(\\xi\_i\\) per coding neuron (or ± pair). Two branch currents per neuron. Learns a projected precision ratio in neuron space. Minimal additional population. Must share \\(\\xi\\) across ± pairs. Stays closest to original SCN/SFEC architecture.

Method II — channel-space precision

Two dedicated sub-populations: error neurons (\\(m+n\\)) and precision neurons (\\(m+n\\)). Learns true channel-space precisions. Whitening condition is interpretable and testable. Larger circuit. Converges to Kalman-optimal ratio for diagonal case.

In both methods the important timescale hierarchy must be respected: spiking inference (\\(\\tau \\sim 0.1\\)) is fastest, inner ZOH relaxation is next, then observation steps (\\(\\Delta t \\sim 10^{-3}\\) s), and precision learning is slowest (\\(\\tau\_q \\gg 1/\\tau\\)). If precision updates run at the same timescale as the inference dynamics, the bounding geometry of the SFEC condition changes during the relaxation, breaking the free-energy descent guarantee.

13\. Expected effects on the controller
---------------------------------------

In the estimator-only design, the controller reads \\(\\boldsymbol{\\mu} = D\\mathbf{r}\\) and produces control \\(u\_t = -K(\\boldsymbol{\\mu}\_t - z\_t)\\). The controller is insulated from the precision-learning dynamics. Precision adaptation affects control only through the estimate quality.

The effective observer gain in the scalar/isotropic case is:

\\\[ L\_k(t) = \\frac{\\pi\_y^k(t)}{\\pi\_y^k(t) + \\pi\_\\mu^k(t)} = \\frac{1}{1 + \\rho\_k(t)} \\\]

When observation noise rises: residuals \\((\\epsilon\_y^k)^2\\) increase → \\(\\pi\_y^k\\) falls → \\(L\_k\\) decreases → the estimator follows its prior more → control signal becomes smoother. When process noise or model mismatch rises: residuals \\((\\epsilon\_\\mu^k)^2\\) increase → \\(\\pi\_\\mu^k\\) falls → \\(L\_k\\) increases → the estimator corrects faster from measurements → control reacts faster to disturbances.

For the controller to be informed about self-generated motions, the predictor must include an efference copy of the motor command:

\\\[ \\boldsymbol{\\mu}\_t^- = \\Phi\\,\\boldsymbol{\\mu}\_{t-1} + \\Gamma\\,u\_{t-1} \\\]

Without this term, self-generated motion is misattributed to process noise, corrupting the learned prior precision.