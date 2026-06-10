# SMEFT, QCD and EFT at the LHC — Personal Study Notes

> These notes summarise an extended conversation working through a master's thesis on the triple-gluon operator, PDF-EFT fits, and related topics. Every conceptual doubt that came up is addressed here so it doesn't come up again.

---

## Table of Contents

1. [Di-jets](#1-di-jets)
2. [CP Symmetry and Operators in QCD](#2-cp-symmetry-and-operators-in-qcd)
3. [CP in QED vs QCD — Why the Difference?](#3-cp-in-qed-vs-qcd--why-the-difference)
4. [The Triple-Gluon Operator and Non-Interference](#4-the-triple-gluon-operator-and-non-interference)
5. [Why More Jets Doesn't Always Help](#5-why-more-jets-doesnt-always-help)
6. [What is EFT and the SMEFT Framework?](#6-what-is-eft-and-the-smeft-framework)
7. [Renormalization — What It Is and What It Isn't](#7-renormalization--what-it-is-and-what-it-isnt)
8. [LO vs NLO — Perturbative Expansion in Practice](#8-lo-vs-nlo--perturbative-expansion-in-practice)
9. [Wilson Coefficients — Where They Come From](#9-wilson-coefficients--where-they-come-from)
10. [Cross Sections, Amplitudes and Fitting](#10-cross-sections-amplitudes-and-fitting)
11. [PDFs and Their Entanglement with EFT](#11-pdfs-and-their-entanglement-with-eft)
12. [SMEFT Theory Errors](#12-smeft-theory-errors)
13. [LEP Constraints and Why Precision ≠ Tight Bounds](#13-lep-constraints-and-why-precision--tight-bounds)
14. [The ST Observable and Its Pitfalls](#14-the-st-observable-and-its-pitfalls)
15. [SIMUNet and Closure Tests](#15-simunet-and-closure-tests)

---

## 1. Di-jets

A **jet** is a collimated spray of hadrons produced when a quark or gluon is knocked out of a proton in a collision. Because of **confinement** (quarks cannot exist freely), the parton immediately fragments into a shower of mesons and baryons that the detector sees as a cone of particles.

A **di-jet event** is one where two such jets are produced back-to-back. This happens when two partons (quarks or gluons) collide and scatter at large angles:

```
proton → [quark] ──┐
                    ├──→ scatter at high energy → jet + jet
proton → [gluon] ──┘
```

Di-jets are useful because:
- They directly probe the highest parton-parton energies available
- They are sensitive to new contact interactions (e.g. four-quark operators from new heavy bosons)
- They are the simplest final state to reconstruct experimentally

Bounds from di-jet searches on four-quark contact interactions reach scales of ~10 TeV (with Wilson coefficient = 1).

---

## 2. CP Symmetry and Operators in QCD

### What C and P are

- **C (Charge conjugation)**: replaces every particle with its antiparticle
- **P (Parity)**: flips all spatial coordinates: $(x,y,z) \to (-x,-y,-z)$
- **CP**: both transformations applied together

A Lagrangian term is **CP-even** if it is unchanged under CP, and **CP-odd** if it changes sign.

### The Standard QCD Lagrangian

At dimension-4 (renormalizable level), QCD has exactly two gauge-invariant operators built from the gluon field strength $G^{\mu\nu}$:

$$\mathcal{L}_{QCD} \supset -\frac{1}{4}G^{a\mu\nu}G^a_{\mu\nu} + \theta \frac{g^2}{32\pi^2} G^{a\mu\nu}\tilde{G}^a_{\mu\nu}$$

- The **first term** is the standard kinetic and self-interaction term. It is **CP-even** and is what we call "normal QCD."
- The **second term** (the θ-term) involves the **dual** field strength $\tilde{G}^{\mu\nu} = \frac{1}{2}\epsilon^{\mu\nu\rho\sigma}G_{\rho\sigma}$. It is **CP-odd**.

The dual introduces the Levi-Civita tensor $\epsilon^{\mu\nu\rho\sigma}$, which is a pseudotensor — it changes sign under parity. This is what makes $G\tilde{G}$ CP-odd.

### The Strong CP Problem

The θ-term is not forbidden by any symmetry — it must exist in QCD. But experiments tell us $\theta \lesssim 10^{-10}$. Why is a free dimensionless parameter so unnaturally small? This is the **strong CP problem**. It is not that the CP-odd operator doesn't exist — it does. It is that its coefficient is bizarrely tiny with no known reason.

### How We Know θ is Small: The Neutron EDM

The CP-odd $G\tilde{G}$ term generates an **electric dipole moment (EDM)** for the neutron. Physically: if gluon interactions violate CP, the charge distribution inside the neutron becomes asymmetric (positive and negative charge centers don't coincide), which is by definition an EDM.

The prediction is:

$$d_n \sim e \cdot \theta \cdot \frac{m_q}{m_N^2} \sim \theta \times 10^{-16} \; e\cdot\text{cm}$$

The experimental bound is $|d_n| < 1.8 \times 10^{-26}\; e\cdot\text{cm}$, giving $\theta < 10^{-10}$.

This is a **low-energy precision observable** that constrains high-energy CP-odd physics. Even a tiny CP-odd coupling at the gluon level produces a measurable hadron-level effect.

### Dimension-6 Triple-Gluon Operators

At the EFT level (dimension-6), there are two analogous operators:

| Operator | CP | Constrained by |
|---|---|---|
| $f^{abc}G^{a\nu}_\mu G^{b\rho}_\nu G^{c\mu}_\rho$ | **Even** ($\mathcal{O}_G$) | Only LHC observables |
| $f^{abc}\tilde{G}^{a\nu}_\mu G^{b\rho}_\nu G^{c\mu}_\rho$ | **Odd** | Neutron EDM (very tight) |

The CP-odd dimension-6 operator contributes to the neutron EDM alongside the θ-term, so it is killed by the same low-energy bound. The CP-even operator $\mathcal{O}_G$ **cannot contribute to the neutron EDM** by definition (generating an EDM requires CP violation). So $\mathcal{O}_G$ can only be constrained at colliders — this is what makes it interesting and relatively free to be large.

**Key point**: Normal QCD does not have a triple-gluon CP-even operator at dimension-4. The gluon self-couplings in the SM come from the covariant derivative structure and give 3- and 4-gluon vertices fixed by gauge invariance. $\mathcal{O}_G$ is genuinely new physics that modifies those vertices.

---

## 3. CP in QED vs QCD — Why the Difference?

### At Dimension-4 in QED

QED also has a θ-term:

$$\mathcal{L} \supset \theta_{QED} \frac{e^2}{32\pi^2} F^{\mu\nu}\tilde{F}_{\mu\nu}$$

In electromagnetism, $F^{\mu\nu}\tilde{F}_{\mu\nu} = \vec{E}\cdot\vec{B}$.

This is a **total derivative** — it equals $\partial_\mu K^\mu$ for some current $K^\mu$. In classical field theory (and in perturbation theory) a total derivative doesn't contribute to the equations of motion and has no physical effect.

In QCD, $G^{\mu\nu}\tilde{G}_{\mu\nu}$ is also a total derivative classically. But due to the **non-Abelian topology** of SU(3), there exist field configurations called **instantons** — non-perturbative tunneling events — for which this total derivative doesn't vanish when integrated over all spacetime. These make the θ-term physically real in QCD.

In QED, the gauge group is U(1) — Abelian with **trivial topology**. No instantons exist. The θ-term is genuinely irrelevant physically.

### The Deep Reason

The photon is **electrically neutral** — it doesn't self-interact at tree level. There is no triple-photon vertex at dimension-4 (forbidden by gauge invariance). The non-Abelian nature of SU(3) is what gives gluons self-interactions and a topologically non-trivial vacuum, which is what makes the CP-odd operator physical.

### The Electron EDM — The Closest QED Analog

The closest QED analog to the neutron EDM is:

$$\mathcal{L} \supset \frac{d_e}{2} \bar{\psi} \sigma^{\mu\nu} \gamma^5 \psi F_{\mu\nu}$$

This is CP-odd and physically meaningful, but it involves **fermions** not just photons. In the SM it is negligibly small, but new physics with CP-violating couplings to electrons can enhance it. The current bound $|d_e| < 4.1 \times 10^{-30}\; e\cdot\text{cm}$ is one of the most precise measurements in physics.

### Summary

| Theory | CP-odd dim-4 | Physically relevant? | Why |
|---|---|---|---|
| QED | $F\tilde{F}$ | No | Total derivative, trivial U(1) topology |
| QCD | $G\tilde{G}$ | Yes | Non-trivial SU(3) vacuum topology (instantons) |
| QED dim-6 | Pure photon ops | No | Bianchi identity kills them |
| QED dim-6 | Electron EDM $\bar\psi\sigma\gamma^5\psi F$ | Yes | Involves fermions |

**Bottom line**: The Abelian nature of U(1) saves QED from a strong-CP-like problem. QCD has no such luck.

---

## 4. The Triple-Gluon Operator and Non-Interference

### The EFT Cross Section Decomposition

When you add $\mathcal{O}_G$ to the SM, the cross section becomes:

$$\sigma = \underbrace{|\mathcal{M}_{SM}|^2}_{\text{pure SM}} + \underbrace{2\,\text{Re}(\mathcal{M}_{SM}^* \mathcal{M}_{EFT})}_{\text{interference, linear in }1/\Lambda^2} + \underbrace{|\mathcal{M}_{EFT}|^2}_{\text{quadratic in }1/\Lambda^4}$$

The **interference term** (second piece) is what you want — it is linear in $c_G/\Lambda^2$ and gives the cleanest, strongest handle on new physics.

### What is an Amplitude $\mathcal{M}$?

$\mathcal{M}$ is the **scattering amplitude** — the quantum mechanical object computed from Feynman diagrams that encodes the probability of a process occurring. The cross section (what detectors measure) goes like $|\mathcal{M}|^2$, analogous to intensity being the square of a wave amplitude in optics.

### What is Helicity?

Helicity is the **spin projection along the direction of motion** of a particle. For a gluon it can be $+1$ (right-handed) or $-1$ (left-handed). In QCD scattering, the amplitude depends strongly on the helicity configuration of all external particles.

The SM gluon scattering amplitudes are dominated by **MHV (Maximally Helicity Violating)** configurations — specific helicity assignments that give the largest contributions.

The dimension-6 operator $\mathcal{O}_G$ produces amplitudes with a **different helicity structure** — it contributes to configurations that are suppressed or zero in the SM. This means $\mathcal{M}_{SM}$ and $\mathcal{M}_{EFT}$ are orthogonal in helicity space: their product $\mathcal{M}_{SM}^*\mathcal{M}_{EFT} = 0$.

This is the **non-interference result**: the linear term vanishes at tree level for $2\to 2$ gluon scattering.

### Why This is a Problem

Since the linear term is zero, the only sensitivity to $\mathcal{O}_G$ comes from the quadratic term $|\mathcal{M}_{EFT}|^2 \sim 1/\Lambda^4$. This is problematic because:

1. $1/\Lambda^4$ is the same order as **dimension-8 operators** that were never included in the analysis
2. The constraint derived is theoretically inconsistent — you're working at dimension-6 but extracting information from a dimension-8 level effect
3. Any bound on $c_G$ could equally well be attributed to some unknown dimension-8 operator

---

## 5. Why More Jets Doesn't Always Help

The intuition is: with more external gluons in the process ($2\to 3$, $2\to 4$, ...), more helicity combinations are available, potentially allowing the interference term to become non-zero.

However, as the thesis notes, **even going to high jet multiplicities doesn't recover the linear term**. The non-interference is more robust than a simple $2\to 2$ accident. The helicity structure that kills the interference is a property of the operator itself, not just of the number of external particles.

The fact that experimental sensitivity *does* improve with jet multiplicity (as seen in the CMS analysis) is therefore suspicious — it means the improvement comes entirely from the quadratic $1/\Lambda^4$ term, bringing all the theoretical consistency problems described above. This is one of the key unresolved puzzles the thesis investigates.

Additionally, the CMS selection using the $S_T$ observable is dominated by **di-jet-like configurations** even in high-multiplicity samples — most of the energy is carried by two hard jets, with the rest being soft radiation. So the kinematic situation doesn't change much with jet multiplicity, making the sensitivity improvement even harder to understand.

---

## 6. What is EFT and the SMEFT Framework?

### The Basic Idea of EFT

An Effective Field Theory (EFT) is a description of physics valid only below some energy scale $\Lambda$. Above $\Lambda$, there is some unknown "UV" (ultraviolet = high energy) theory with new particles and interactions. Below $\Lambda$, those heavy particles are too massive to produce directly, but their effects don't disappear — they are encoded as **higher-dimensional operators** suppressed by powers of $1/\Lambda$.

This is analogous to Fermi's theory of beta decay: before the W boson was discovered, its effects at low energies could be described by a four-fermion contact interaction $G_F \bar\psi\psi\bar\psi\psi$, where $G_F \sim 1/M_W^2$.

### SMEFT

The **Standard Model Effective Field Theory (SMEFT)** extends the SM Lagrangian with all possible higher-dimensional operators consistent with SM symmetries:

$$\mathcal{L}_{SMEFT} = \mathcal{L}_{SM} + \sum_i \frac{c_i}{\Lambda^2}\mathcal{O}_i^{(6)} + \sum_j \frac{d_j}{\Lambda^4}\mathcal{O}_j^{(8)} + \ldots$$

- $\mathcal{O}_i^{(6)}$ are **dimension-6 operators** — there are 59 independent ones (for one fermion generation)
- $c_i$ are the **Wilson coefficients** — dimensionless numbers encoding the strength of each new interaction
- $\Lambda$ is the **cutoff scale** — the energy at which the EFT breaks down

The power of SMEFT is that it is **model-independent**: you don't need to specify what the UV theory is. Any BSM theory will produce some pattern of Wilson coefficients, but the operators themselves are fixed by symmetry.

### The EFT Expansion Validity

The EFT expansion is valid only when $E \ll \Lambda$. When $E \sim \Lambda$, all higher-dimensional operators become equally important and the truncation at dimension-6 fails completely.

---

## 7. Renormalization — What It Is and What It Isn't

### The Core Problem

In any quantum field theory, loop diagrams involve integrals over all possible internal momenta:

$$\int_0^\infty \frac{d^4k}{k^2 - m^2} \sim \int^\infty k\, dk \to \infty$$

These integrals diverge. This happens because we pretend the theory is valid to arbitrarily high energies, which it isn't.

### What Renormalization Does

Renormalization is the systematic procedure to:

1. **Regularize**: make the integral temporarily finite (e.g. dimensional regularization — work in $4-\epsilon$ dimensions)
2. **Absorb**: the divergences into redefinitions of the parameters (masses, couplings, operator coefficients)
3. **Predict**: physical observables are now finite and well-defined

A theory is **renormalizable** if only a **finite number** of parameters are needed to absorb all divergences to all loop orders. The SM is renormalizable (proven by 't Hooft and Veltman in 1971). SMEFT is not renormalizable — but that's fine, it's explicitly an EFT valid only below $\Lambda$.

### The Physical Content of Renormalization

Renormalization is not just a mathematical trick. It carries real physical information: **parameters depend on the energy scale** at which you probe them. The strong coupling $\alpha_s$ is genuinely different at 10 GeV versus 1000 GeV — this is measurable and measured. This running is encoded in the **renormalization group equations (RGE)**:

$$\mu \frac{d\alpha_s}{d\mu} = \beta(\alpha_s)$$

### What Renormalization Does NOT Do

**Renormalization does not determine the Wilson coefficients.** This is a common confusion. The $c_i$ are fixed by **matching** to the UV theory (see next section), not by renormalization. What renormalization does is tell you **how $c_i$ run with energy scale** once they are fixed:

$$\mu \frac{dc_i}{d\mu} = \gamma_{ij} c_j$$

This running is process-independent and captures the effect of SM loops between the matching scale $\Lambda$ and the experimental scale $\mu$.

### Renormalization vs NLO Calculation — The Key Distinction

This is subtle. Renormalization of the SMEFT Lagrangian makes the theory consistent and tells you how coefficients run. But this is **not** the same as computing NLO corrections to a specific process.

```
Renormalization group:  how cᵢ evolve with scale μ
                        → general, process-independent
                        → encodes loops at the Lagrangian level

NLO calculation:        quantum corrections to a specific amplitude
                        → process-dependent
                        → encodes loops at the cross-section level
```

Both are needed. The RGE gives you the right $c_i$ at the right scale. The NLO calculation gives you the right amplitude using those $c_i$.

---

## 8. LO vs NLO — Perturbative Expansion in Practice

### The Expansion

Cross sections are computed as a power series in the strong coupling $\alpha_s \approx 0.1$:

$$\sigma = \alpha_s^n \left[ \sigma_0 + \alpha_s \sigma_1 + \alpha_s^2 \sigma_2 + \ldots \right]$$

- **LO (Leading Order)**: only $\sigma_0$ — tree-level diagrams only
- **NLO**: adds $\alpha_s \sigma_1$ — one-loop virtual corrections + real gluon emission
- **NNLO**: adds $\alpha_s^2 \sigma_2$ — two loops, etc.

### Why NLO Corrections Can Be Large

Since $\alpha_s \approx 0.1$, you might think NLO adds ~10% corrections. But the NLO coefficient $\sigma_1$ can be large — sometimes $\sigma_1/\sigma_0 \sim 10$, making the NLO correction 100%. This happens because:

- There are many color factor combinations in QCD
- **Large logarithms** $\ln(Q^2/\mu^2)$ appear at each loop order and can be $\sim 10$ even when $\alpha_s \sim 0.1$

### Real and Virtual Emissions at NLO

At NLO there are two types of corrections:

- **Virtual**: a loop diagram where an extra gluon is emitted and immediately reabsorbed. These are complex and can be negative. They are **UV divergent** (fixed by renormalization) and **IR divergent** (infrared divergence from soft/collinear gluons).
- **Real emission**: an extra gluon actually goes into the final state. These are always positive contributions. Also **IR divergent**.

By the **KLN theorem**, IR divergences cancel exactly when you add virtual and real contributions together:

$$\sigma_{NLO} = \sigma_{LO} + \underbrace{\sigma_{virtual}}_{\text{IR divergent, negative}} + \underbrace{\sigma_{real}}_{\text{IR divergent, positive}} = \text{finite}$$

You **must** include both to get a finite answer. Computing only the loops without real emission gives an infinity.

### Why This Matters for Extracting Wilson Coefficients

If NLO corrections to $\sigma_{SM}$ are large and you ignore them, you will see a fake discrepancy between your LO prediction and the data, and incorrectly attribute it to new physics ($c_i \neq 0$). NLO is essential to know whether a deviation is real or just a missing correction.

### Three Criteria for Needing NLO in SMEFT

1. **$\Lambda$ is in the range 1–3 TeV**: EFT effects might be visible at LHC, and if you see a deviation you need NLO to interpret it precisely
2. **Experimental precision reaches ~10%**: NLO corrections are comparable to your error bars and cannot be ignored
3. **Your LO result will be used by others**: NLO is always strictly more useful — anyone wanting LO can extract it from NLO, but not vice versa

---

## 9. Wilson Coefficients — Where They Come From

### Matching: The Source of Wilson Coefficients

Suppose there is a UV theory with a heavy boson $Z'$ of mass $M$ and coupling $g'$. At energies $E \ll M$, you cannot produce $Z'$, but its effects don't vanish. You **integrate it out** — solve its equation of motion and substitute back into the Lagrangian. This produces effective operators with coefficients:

$$\frac{c_i}{\Lambda^2} \sim \frac{g'^2}{M^2}$$

The procedure of demanding that the UV theory and the EFT give identical predictions at the boundary scale $\Lambda$ is called **matching**:

$$\mathcal{M}_{UV}\bigg|_{E=\Lambda} = \mathcal{M}_{SMEFT}\bigg|_{E=\Lambda}$$

This fixes $c_i$ in terms of UV parameters. If you don't know the UV theory, you leave $c_i$ as free parameters to be measured.

### The Full Chain

```
UV theory at scale Λ  (unknown: SUSY? Extra dims? Z'? ...)
         ↓  matching: integrate out heavy particles
c_i(Λ) determined
         ↓  RGE running: SM loops between Λ and μ
c_i(μ) at experimental scale
         ↓  NLO calculation of specific process
σ(c_i) as polynomial in Wilson coefficients
         ↓  compare to data, minimize χ²
best-fit c_i ± uncertainties
         ↓  interpret
constraints on UV theory parameters
```

### The Model-Independence of SMEFT

The genius of SMEFT is that steps 3–5 are completely independent of what the UV theory is. You compute $\sigma(c_i)$ once. Then any BSM theorist can plug in their predicted values of $c_i$ and check consistency with your results. The calculation is universal.

---

## 10. Cross Sections, Amplitudes and Fitting

### The i-th Cross Section

In a global fit you don't measure one cross section — you measure many. The index $i$ labels each separate measurement:

```
i = 1 → tt̄ total cross section at 8 TeV
i = 2 → tt̄ total cross section at 13 TeV
i = 3 → tt̄Z associated production
i = 4 → differential distribution, bin 1
...
i = N → all other included measurements
```

For each measurement, the theoretical prediction is a polynomial in the Wilson coefficients:

$$\sigma_i^{th}(c_1, c_2, \ldots) = \sigma_{SM,i} + \sum_n \frac{c_n}{\Lambda^2}\sigma_{i,n} + \sum_{n,m}\frac{c_{n,m}}{\Lambda^4}\sigma_{i,n,m}$$

where $\sigma_{SM,i}$, $\sigma_{i,n}$, $\sigma_{i,n,m}$ are numbers computed once from Feynman diagrams.

**The same Wilson coefficients appear in all measurements simultaneously.** This is what makes combining many processes powerful — different operators have different effects in different processes, allowing you to disentangle them.

### What is a Figure of Merit?

A figure of merit is a single number quantifying how well theory agrees with data. The standard choice in particle physics is **chi-squared**:

$$\chi^2(c_1, c_2, \ldots) = \sum_i \frac{\left(\sigma_i^{th}(c_1,\ldots) - \sigma_i^{measured}\right)^2}{\delta_i^2}$$

where $\delta_i$ is the experimental uncertainty on measurement $i$.

- $\chi^2$ small → theory close to data → good fit
- $\chi^2$ large → theory far from data → bad fit

You **minimize** $\chi^2$ over the Wilson coefficients to find the best-fit values.

### How You Separate SM and EFT Contributions Experimentally

You don't — you can't look at a single event and say "this came from the SM diagram." What you do is:

1. Measure total cross sections and distributions experimentally
2. Compute theoretical predictions as a function of $c_i$
3. Fit $c_i$ so that theory matches data

The "separation" is done statistically using **kinematic distributions** — EFT operators often produce different angular distributions or energy spectra than the SM, allowing statistical disentanglement even though every event contains contributions from all diagrams.

---

## 11. PDFs and Their Entanglement with EFT

### What PDFs Are

The **Parton Distribution Functions (PDFs)** $f_a(x, \mu)$ encode the probability of finding a parton of type $a$ carrying momentum fraction $x$ inside a proton at scale $\mu$. Every cross section prediction at a hadron collider requires them:

$$\sigma(pp \to X) = \sum_{a,b} \int dx_1 dx_2\, f_a(x_1, \mu) f_b(x_2, \mu) \cdot \hat{\sigma}(ab \to X)$$

PDFs cannot be calculated from first principles — they must be extracted by fitting experimental data.

### The Chicken-and-Egg Problem

**PDF fitters** use LHC top quark data assuming the SM is exactly correct. Any tension with predictions is attributed to incorrectly known PDFs → they adjust the PDFs.

**SMEFT fitters** use the same data assuming the PDFs are correct. Any tension is attributed to new physics → they adjust the Wilson coefficients.

Both groups use the **same data** but blame discrepancies on **completely different sources**. They cannot both be right.

### Question 1: Are SM-PDFs Contaminated by BSM Physics?

If yes, it means PDF fitters absorbed a BSM signal into a distorted PDF:

$$\text{data} = \sigma_{SM}(f^{\text{BSM-contaminated}}) = \sigma_{BSM}(f^{\text{true}})$$

When SMEFT analysts then use those contaminated PDFs as their baseline, the BSM signal is already partially hidden. They will underestimate $c_i$ or miss effects entirely. "Yes to question 1" means **both approaches are compromised** — the only consistent solution is to fit PDFs and EFT coefficients simultaneously.

### Question 2: Are SMEFT Results Dependent on PDF Choice?

Yes — and this is serious. Using PDFs that already absorbed top quark data while also fitting EFT coefficients to top quark data double-counts the information.

### Why You Cannot Separate the Regimes for Top Quarks

For many processes you can cleanly separate:
- Low energy data → sensitive to PDFs, insensitive to EFT
- High energy data → sensitive to EFT, PDFs already pinned down

For **top quark production** this separation fails:
- The top is heavy ($m_t \approx 173$ GeV) so even threshold production is at high energy
- Gluon PDFs at high $x$ are uncertain precisely in the high-energy regime where EFT effects grow
- PDFs and EFT effects are **simultaneously uncertain and important in exactly the same kinematic region**

There is no clean window. They are fundamentally entangled in the same data.

---

## 12. SMEFT Theory Errors

### The Problem of Multiple Truncations

The SMEFT prediction can be truncated in different ways:
- Linear in EFT: keep only the interference term $\sim 1/\Lambda^2$
- Quadratic in EFT: also keep the squared term $\sim 1/\Lambda^4$
- Different renormalization scale choices
- Different input parameter schemes ($G_F$ scheme vs $\alpha$ scheme)

Each choice gives a different numerical answer. The spread between choices is your **theoretical uncertainty**.

### Two Sources of SMEFT Theory Error (Eq. 3.24)

$$\Delta_i^{SMEFT} = \underbrace{\sum_j X_{ij}\frac{C^8_{ij}v_T^4}{\Lambda^4}}_{\text{dimension-8 contamination}} + \underbrace{\sum_j \frac{(g^{ij}_{SM})^2}{16\pi^2}C^6_{ij}\ln\left[\frac{\Lambda^2}{v_T^2}\right]\frac{v_T^2}{\Lambda^2}}_{\text{missing NLO corrections}}$$

- **First term**: the contribution of dimension-8 operators you neglected, suppressed by $v_T^4/\Lambda^4$ where $v_T \approx 246$ GeV is the Higgs VEV
- **Second term**: the missing one-loop NLO correction, with $g^2/(16\pi^2)$ being the typical loop factor, and the logarithm $\ln(\Lambda^2/v_T^2)$ potentially large when $\Lambda \gg v_T$

### Practical Implication

Once experimental errors reach ~10% level, SMEFT theory errors are comparable and must be included. At per-mille experimental precision, ignoring theory errors of a few percent is completely unjustified — you are dominated by the theoretical uncertainty, not the experimental one.

---

## 13. LEP Constraints and Why Precision ≠ Tight Bounds

### LEP I and II

- **LEP I**: ran at the Z boson mass (~91 GeV), produced millions of Z bosons, achieved **per-mille precision** on Z properties
- **LEP II**: ran at higher energies (~200 GeV), produced W bosons, ~few percent precision

### The False Hierarchy

The naive assumption: per-mille experimental precision → per-mille constraints on Wilson coefficients.

This is **wrong** because the mapping between experimental precision and operator constraints depends on the **sensitivity**:

$$\sigma = \sigma_{SM} + \sum_i \frac{c_i}{\Lambda^2} \underbrace{\frac{\partial\sigma}{\partial c_i}}_{\text{how strongly operator }i\text{ affects this observable}}$$

If $\partial\sigma/\partial c_i$ is tiny for operator $i$, then even a per-mille measurement of $\sigma$ gives a **poor constraint** on $c_i$. The experimental precision and the operator constraint are decoupled by this sensitivity factor.

Some operators have much larger effects at higher energies (LEP II or LHC) than at LEP I, despite LEP I being more precise. The hierarchy in experimental precision does not translate into a hierarchy of operator constraints.

### The Practical Danger

A common (unjustified) practice is:
1. See that LEP I data is per-mille precise
2. Conclude those Wilson coefficients are "essentially zero"
3. **Set them to zero** in LHC analyses to simplify the fit

This is not justified. Setting them to zero introduces a hidden bias. The thesis authors argue these parameters should be kept free in LHC analyses.

---

## 14. The ST Observable and Its Pitfalls

### What ST Is

$$S_T = E_T^{miss} + \sum_j E_{T,j}$$

The **scalar sum of all transverse energies** in the event — missing transverse energy plus all jet transverse energies. It captures "how energetic was this event overall" in a single number.

### The Four Pitfalls Identified

**Pitfall 1 — Di-jet dominance despite high multiplicity**: Even in high jet-multiplicity events, the CMS $S_T$ selection is dominated by di-jet-like configurations (two hard jets carry most of the energy, rest is soft). But we know di-jet configurations give zero linear interference with $\mathcal{O}_G$. So why does sensitivity improve with jet multiplicity? Something is not understood.

**Pitfall 2 — EFT breakdown**: The limits are set using data in the high-$S_T$ tail where $S_T \approx \Lambda$. In this region $E/\Lambda \approx 1$ and the EFT expansion has completely broken down. All higher-dimensional operators become equally important. The bound may be an artifact of using the EFT outside its validity.

**Pitfall 3 — Dimension-8 contamination**: The constraint comes from the $\mathcal{O}(1/\Lambda^4)$ quadratic term. But dimension-8 operators contribute at the same order and were never included. The bound on $c_G$ cannot be cleanly separated from possible dimension-8 contributions.

**Pitfall 4 — ST may not be optimal**: $S_T$ is an inclusive variable that washes out angular information. Observables sensitive to **hard, well-separated jets** might do better, since $\mathcal{O}_G$ modifies the angular structure of gluon scattering. Configurations with widely separated jets probe the regime where the anomalous vertex has the most distinctive effect.

### Why Experiments Look at High Energy ($E/\Lambda \approx 1$)

Because that's where the signal is biggest. EFT effects grow as $(E/\Lambda)^2$ or $(E/\Lambda)^4$, so at low energies the deviation from the SM is completely buried in experimental uncertainties. There is a fundamental tension:

- **Low energy**: EFT is valid, but signal is invisible
- **High energy**: signal is visible, but EFT has broken down

Honest resolutions require either: unitarity cuts removing events with $E > \Lambda$, using a full UV-complete theory instead of EFT, or careful marginalization over $\Lambda$.

---

## 15. SIMUNet and Closure Tests

### SIMUNet

**SIMUNet** is a neural-network-based fitting framework designed to perform **simultaneous fits of PDFs and EFT Wilson coefficients**. It addresses the chicken-and-egg problem described in Section 11 by not assuming either PDFs or EFT coefficients are fixed — it fits both at the same time from the same data.

### Closure Tests

A **closure test** is a validation procedure for any fitting methodology:

1. **Generate pseudo-data** using known ("truth") values of the parameters you want to extract (e.g. specific values of $c_G$ and specific PDFs)
2. **Run the full fitting pipeline** on this pseudo-data as if it were real experimental data
3. **Check whether you recover** the known input values

If you recover them: the pipeline is working correctly. If you don't: something is wrong with the methodology (bias in the fit, incorrect parameterization, etc.).

Closure tests are essential because in real data you never know the true answer. Testing on pseudo-data where you do know the answer validates that your methodology is unbiased before you apply it to real measurements.

### What This Thesis Does

The thesis:
1. Investigates the constraints on $\mathcal{O}_G$ from multi-jet observables, examining the four pitfalls above
2. Applies those constraints to simultaneous PDF+EFT fits using SIMUNet
3. Performs closure tests to validate the simultaneous fitting procedure

This directly addresses the inconsistency between SM-PDF and fixed-PDF approaches by building the only framework that treats both on equal footing.

---

## Quick Reference: Key Formulas

### SMEFT Lagrangian
$$\mathcal{L}_{SMEFT} = \mathcal{L}_{SM} + \sum_i \frac{c_i}{\Lambda^2}\mathcal{O}_i^{(6)} + \ldots$$

### Cross Section Decomposition
$$\sigma = \sigma_{SM} + \frac{c_i}{\Lambda^2}\sigma_{int} + \frac{c_i^2}{\Lambda^4}\sigma_{EFT}$$

### Chi-squared Figure of Merit
$$\chi^2 = \sum_i \frac{(\sigma_i^{th} - \sigma_i^{measured})^2}{\delta_i^2}$$

### NLO Structure
$$\sigma_{NLO} = \sigma_{LO}(1 + \alpha_s K), \quad \alpha_s \approx 0.1 \text{ at LHC scales}$$

### SMEFT Theory Error (leading terms)
$$\Delta_i^{SMEFT} \sim \frac{v_T^4}{\Lambda^4} + \frac{g^2}{16\pi^2}\ln\frac{\Lambda^2}{v_T^2}\frac{v_T^2}{\Lambda^2}$$

### Neutron EDM Bound on θ
$$d_n \sim \theta \times 10^{-16}\; e\cdot\text{cm}, \quad |d_n| < 1.8\times 10^{-26}\; e\cdot\text{cm} \implies \theta < 10^{-10}$$

---

## Quick Reference: Key Concepts

| Term | Meaning |
|---|---|
| Di-jet | Two back-to-back jets from parton-parton scattering |
| CP | Combined charge conjugation + parity symmetry |
| θ-term | CP-odd dimension-4 gluon operator; source of strong CP problem |
| Neutron EDM | Experimental observable that bounds CP violation in QCD |
| $\mathcal{O}_G$ | CP-even dimension-6 triple-gluon operator; only constrained at LHC |
| Helicity | Spin projection along direction of motion; $\pm 1$ for gluons |
| Non-interference | $\mathcal{M}_{SM}^*\mathcal{M}_{EFT} = 0$ due to helicity mismatch |
| LO/NLO | Leading/Next-to-leading order in perturbative $\alpha_s$ expansion |
| Matching | Procedure that fixes Wilson coefficients from UV theory |
| Running | How parameters change with energy scale (RGE) |
| PDF | Parton Distribution Function; probability of finding parton with momentum fraction $x$ |
| $S_T$ | Scalar sum of all transverse energies in an event |
| Figure of merit | Single number ($\chi^2$) measuring goodness of fit |
| Closure test | Validation of fitting pipeline using pseudo-data with known truth |
| SIMUNet | Neural network framework for simultaneous PDF+EFT fits |
| Per-mille | One part in a thousand (0.001); ten times more precise than 1% |
| LEP I / LEP II | Electron-positron collider at CERN; ran at Z mass / above W threshold |
