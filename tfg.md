## ⚛️ Deep Inelastic Scattering (DIS) Flow: From Measurement to Quarks

This process establishes that the proton is composed of smaller, point-like constituents called **partons** (quarks and gluons), and determines their momentum distribution.

### Phase 1: Experimental Measurement (The Raw Data)

The experiment involves firing a high-energy lepton (usually an electron) at a stationary target (a proton). Only the outgoing lepton is detected (**inclusive scattering**).

|**Variable**|**Description**|**Role in Experiment**|
|---|---|---|
|**$E$**|Initial Energy of the Lepton|Set by the particle accelerator.|
|**$E'$**|Final Energy of the Scattered Lepton|**Measured** by the detector.|
|**$\theta$**|Lepton Scattering Angle|**Measured** by the detector.|
|**$\frac{d^2\sigma}{d\Omega dE'}$**|Differential Cross-Section|The probability of scattering into a specific angle and energy range. This is the **primary experimental result**.|

---

### Phase 2: Kinematic Calculation (Defining $x$ and $Q^2$)

The raw measurements $(E', \theta)$ are converted into two Lorentz-invariant quantities, which define the nature of the collision, regardless of the observer's reference frame.

|**Variable**|**Definition (Lab Frame)**|**Physical Meaning**|
|---|---|---|
|**$Q^2$**|$Q^2 \approx 4E E' \sin^2(\theta/2)$|**Resolution Scale.** The squared 4-momentum transfer. It defines how "deeply" the proton is probed. High $Q^2$ means high resolution.|
|**$\nu$** (Energy Transfer)|$\nu = E - E'$|The energy lost by the lepton, which is transferred to the proton.|
|**$x$** (Bjorken Scaling Variable)|$x := \frac{Q^2}{2M\nu}$|**Momentum Fraction.** The fraction of the proton's total momentum that is carried by the struck parton (quark) in the infinite momentum frame. _Its range is $0 < x \le 1$._|

**Crucial Point:** For any scattering event, you calculate a specific pair of **$(x, Q^2)$**.

---

### Phase 3: Physics Extraction (The Structure Functions)

The measured cross-section is theoretically related to the proton's internal structure through a general formula that depends on $x$, $Q^2$, and two unknown functions, $F_1$ and $F_2$.

#### **The General Cross-Section Formula**

The measured cross-section, $\frac{d^2\sigma}{d\Omega dE'}$, is proportional to a function that mixes $F_1$ and $F_2$ with known kinematic factors:

$$\sigma_{\text{measured}} \propto \left[ \frac{1}{1 + \epsilon} F_2(x, Q^2) + \frac{2x\epsilon}{1 + \epsilon} F_1(x, Q^2) \right]$$

- $F_1(x, Q^2)$ and $F_2(x, Q^2)$ are the **Structure Functions** of the proton. They contain all the physics information about the proton's internal structure.
    
- $\epsilon$ is a kinematic factor depending on the scattering angle $\theta$ (the virtual photon's polarization).
    

#### **Separating $F_1$ and $F_2$ (Rosenbluth Separation)**

1. **Fix $x$ and $Q^2$:** The experiment performs multiple cross-section measurements at different initial beam energies $E$ and scattering angles $\theta$. By carefully selecting these variables, they can obtain different measurements $\sigma$ while ensuring **$x$ and $Q^2$ remain the same**.
    
2. **Vary $\epsilon$:** Since $x$ and $Q^2$ are fixed, $F_1$ and $F_2$ are constant, but the kinematic factor $\epsilon$ changes because the angle $\theta$ changed.
    
3. **Linear Fit:** By plotting the measured cross-section $\sigma$ against $\epsilon$, the resulting points form a straight line.
    
    - The **slope** of the line gives one combination of $F_1$ and $F_2$.
        
    - The **intercept** of the line gives a different combination of $F_1$ and $F_2$.
        
4. **Extraction:** Solving the two linear equations allows $F_1(x, Q^2)$ and $F_2(x, Q^2)$ to be **uniquely extracted** for that specific pair of $(x, Q^2)$.
    

---

### Phase 4: Interpretation (The Parton Model)

The extracted structure functions are directly related to the **Parton Distribution Functions (PDFs)**, $q(x)$, which represent the probability of finding a quark with momentum fraction $x$ inside the proton.

- In the simplified **Parton Model**, the structure functions are sums over the squared charges of the quarks ($e_q$) multiplied by their PDFs:
    

$$F_2(x) = \sum_{\text{quarks } i} e_i^2 \cdot x \cdot q_i(x)$$

- The **Callan-Gross Relation** ($F_2 = 2x F_1$) is also checked, which provides strong evidence that the partons have spin $1/2$ (i.e., they are quarks).