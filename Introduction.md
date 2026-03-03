# PRELIMINARY MATERIAL

## Dependency Map of Concepts

```

Quantum Mechanics I (prerequisite)

│

├── Special Relativity & 4-Vector Notation

│ │

│ └── Classical Field Theory (Lagrangian Density, Action)

│ │

│ ├── Symmetries & Noether's Theorem

│ │ │

│ │ ├── Internal Symmetries (Global)

│ │ │ │

│ │ │ ├── Lie Groups & Lie Algebras

│ │ │ │ │

│ │ │ │ ├── Abelian: U(1)

│ │ │ │ │ │

│ │ │ │ │ └── Gauge Principle (Abelian) → QED

│ │ │ │ │

│ │ │ │ └── Non-Abelian: SU(N)

│ │ │ │ │

│ │ │ │ └── Gauge Principle (Non-Abelian) → Yang-Mills

│ │ │ │ │

│ │ │ │ ├── SU(3)_c → QCD (gluons, color)

│ │ │ │ │

│ │ │ │ ├── SU(2)_L × U(1)_Y → Electroweak

│ │ │ │ │

│ │ │ │ └── Full SM Gauge Group

│ │ │ │

│ │ │ └── Spontaneous Symmetry Breaking

│ │ │ │

│ │ │ └── Higgs Mechanism → Mass Generation

│ │ │

│ │ └── Spacetime Symmetries → Lorentz Representations

│ │ │

│ │ └── Scalars, Vectors, Spinors (Dirac Equation)

│ │

│ └── Quantization of Fields (Conceptual)

│ │

│ ├── Particles as Field Excitations

│ │

│ ├── Feynman Diagrams & Perturbation Theory

│ │

│ ├── Loop Diagrams → Divergences

│ │ │

│ │ └── Renormalization

│ │ │

│ │ └── Renormalization Group

│ │ │

│ │ └── Running Couplings (β-functions)

│ │ │

│ │ └── Asymptotic Freedom in QCD

│ │

│ └── Operator Dimension & Power Counting

│ │

│ └── Effective Field Theory

│ │

│ ├── Decoupling & Matching

│ │

│ └── SMEFT

│ │

│ ├── Dimension-6 Operator Basis (Warsaw)

│ │

│ ├── Wilson Coefficients & Running

│ │

│ └── The O_G Operator

```
## Length Estimate and Justification

**Estimated total word count:** ~95,000 words

**Estimated pages (at 500 words/page):** ~190 pages

**Estimated reading time:** ~30–38 hours (at 15–20 pages/hour with reflection)

**Justification:** The conceptual distance between Quantum Mechanics I and SMEFT dimension-6 operators is enormous. The student must traverse:

- Classical field theory (new formalism)

- Special relativity notation (new language)

- Quantum field theory (paradigm shift from QM)

- Group theory beyond basic linear algebra (new mathematics)

- Gauge symmetry (profoundly new physical concept)

- Non-Abelian generalizations (significant mathematical complexity)

- The full Standard Model (complex structure with multiple sectors)

- Renormalization (counterintuitive conceptual framework)

- Effective field theory (philosophical shift in what a "theory" means)

- SMEFT specifically (technical operator classification)

Each topic requires careful scaffolding. No step can be skipped without creating a logical gap. The estimate reflects the minimal treatment needed for genuine understanding, not encyclopedic coverage.

---

# PART I: FOUNDATIONS

---

# Chapter 1: From Particles to Fields

## Learning Objectives

After completing this chapter, the student will be able to:

1. Explain why ordinary quantum mechanics is insufficient for describing high-energy particle physics.

2. Articulate the conceptual necessity of quantum field theory.

3. Describe the basic idea of a field and distinguish it from a particle.

4. Understand the role of special relativity in motivating field theory.

---

## 1.1 What You Already Know

In your Quantum Mechanics I course, you studied a framework with the following features:

- A system is described by a state vector $|\psi\rangle$ in a Hilbert space $\mathcal{H}$.

- Observables are represented by Hermitian operators acting on $\mathcal{H}$.

- Time evolution is governed by the Schrödinger equation: $i\hbar \frac{\partial}{\partial t}|\psi\rangle = \hat{H}|\psi\rangle$.

- The number of particles in the system is fixed. If you begin with one electron, you always have one electron.

- Position $\hat{x}$ and momentum $\hat{p}$ satisfy $[\hat{x}, \hat{p}] = i\hbar$.

This framework is spectacularly successful for atomic physics, molecular physics, and condensed matter at low energies. However, it contains a deep limitation that becomes apparent when we try to merge it with Einstein's special relativity.

## 1.2 The Problem: Quantum Mechanics Meets Special Relativity

### 1.2.1 The Energy-Mass Equivalence

Einstein's special relativity, formulated in 1905, contains the famous relation:

$$E = mc^2$$

More precisely, the full energy-momentum relation for a particle of mass $m$ is:

$$E^2 = (pc)^2 + (mc^2)^2$$

where $p$ is the magnitude of the three-momentum and $c$ is the speed of light. This equation has a dramatic consequence: **energy can be converted into matter and vice versa.** If a particle has energy $E \geq 2m_e c^2$ (where $m_e$ is the electron mass), it can in principle produce an electron-positron pair.

### 1.2.2 Why Particle Number Cannot Be Fixed

In your QM I course, you solved the Schrödinger equation for one particle, or perhaps two. The Hilbert space was that of a fixed number of particles. But consider what happens when energies become large enough:

- An electron scattering off a nucleus can radiate a photon. Now we have an electron *and* a photon — the particle number has changed from 1 to 2.

- A photon with sufficient energy can produce an electron-positron pair. Particle number: 1 → 2 (or 1 → 3, counting the photon if it survives).

- Even the vacuum itself, in the presence of strong fields, can spontaneously produce particle-antiparticle pairs.

**The fixed-particle-number framework of QM I cannot accommodate these processes.** We need a framework where the number of particles is a dynamical variable — where particles can be created and destroyed.

### 1.2.3 The Dirac Equation's Lesson

One might try a minimal approach: simply write a relativistic version of the Schrödinger equation. This is precisely what Dirac did in 1928. His equation (which we will study in Chapter 7) successfully describes spin-1/2 particles in a relativistically covariant way. However, it inevitably predicts negative-energy solutions, which Dirac reinterpreted as antiparticles. The very structure of relativistic quantum theory demands that antiparticles exist, and therefore that particle-antiparticle creation and annihilation must be possible. A single-particle theory is inherently inconsistent with special relativity.

## 1.3 The Solution: Fields

### 1.3.1 What Is a Field?

You are already familiar with the concept of a field from classical physics. The electric field $\vec{E}(\vec{x}, t)$ assigns a vector to every point in space and every moment in time. The temperature $T(\vec{x}, t)$ assigns a number to every point. A **field** is simply a physical quantity that is defined at every point in spacetime.

Formally:

> **Definition 1.1 (Classical Field).** A classical field is a function $\phi: \mathbb{R}^{3+1} \to V$, where $\mathbb{R}^{3+1}$ represents spacetime (three spatial dimensions plus one time dimension) and $V$ is some target space (real numbers, complex numbers, vectors, matrices, etc.).

Examples:

- **Scalar field:** $\phi(x, t) \in \mathbb{R}$. A single real number at each spacetime point. Example: temperature.

- **Vector field:** $\vec{A}(x, t) \in \mathbb{R}^3$. A three-component vector at each spacetime point. Example: the magnetic vector potential.

- **Spinor field:** $\psi(x, t) \in \mathbb{C}^4$. A four-component complex object. Example: the Dirac field for an electron.

### 1.3.2 From Particles to Fields: The Conceptual Leap

In quantum mechanics, you quantized the motion of particles: position and momentum became operators. In **quantum field theory (QFT)**, we quantize the fields themselves: the field $\phi(\vec{x}, t)$ becomes an operator $\hat{\phi}(\vec{x}, t)$ acting on a much larger Hilbert space.

This larger Hilbert space — called **Fock space** — contains states with any number of particles:

$$\mathcal{F} = \mathcal{H}_0 \oplus \mathcal{H}_1 \oplus \mathcal{H}_2 \oplus \mathcal{H}_3 \oplus \cdots$$

where $\mathcal{H}_0$ is the vacuum (zero particles), $\mathcal{H}_1$ is the one-particle Hilbert space, $\mathcal{H}_2$ the two-particle space, and so on. In this framework:

- **Particles are excitations of fields.** An electron is not a fundamental point-like entity; it is a quantized excitation of the electron field $\psi(\vec{x}, t)$.

- **Particle creation and annihilation are natural.** The field operators can add or remove excitations from Fock space.

- **Each particle species corresponds to a different field.** There is an electron field, a photon field, a quark field, a gluon field, a Higgs field, etc.

### 1.3.3 An Analogy

Think of a calm lake. The "vacuum" is the lake at rest. A "particle" is a ripple on the surface. You can have zero ripples (vacuum), one ripple (one particle), two ripples (two particles), and so on. The ripples can be created, can interact with each other, and can be destroyed. The fundamental object is not the ripple — it is the lake (the field). The ripple is merely an excitation of the lake.

This is not just an analogy. In quantum field theory, particles literally are excitations of underlying quantum fields that permeate all of spacetime.

## 1.4 Why Fields? A Summary of Motivations

| Feature | QM I (Particle-based) | QFT (Field-based) |

|---|---|---|

| Particle number | Fixed | Variable (creation/annihilation) |

| Compatibility with SR | Problematic | Built in |

| Antiparticles | Not natural | Automatically predicted |

| Fundamental object | Particle | Field |

| State space | $\mathcal{H}_N$ for $N$ particles | Fock space $\mathcal{F}$ |

## 1.5 The Road Ahead

The remainder of this book constructs, step by step, the framework needed to formulate the Standard Model of particle physics and its effective field theory extension. Here is a brief roadmap:

1. **Part I (Chapters 1–4):** We build the classical foundation — relativistic notation, Lagrangian field theory, and symmetry principles.

2. **Part II (Chapters 5–7):** We introduce the quantum field theory framework — quantized fields, Feynman diagrams, and the Dirac equation for fermions.

3. **Part III (Chapters 8–10):** We construct gauge theories — starting from electromagnetism and generalizing to non-Abelian theories like QCD.

4. **Part IV (Chapters 11–13):** We assemble the Standard Model — its gauge group, particle content, and the Higgs mechanism.

5. **Part V (Chapters 14–15):** We confront quantum corrections — renormalization and the running of coupling constants.

6. **Part VI (Chapters 16–18):** We develop Effective Field Theory and apply it to the Standard Model (SMEFT), culminating in an understanding of dimension-6 operators and the $O_G$ operator.

## Conceptual Summary

- Ordinary quantum mechanics describes a fixed number of particles and is incompatible with special relativity at high energies.

- Special relativity implies that energy can create particles, so particle number must be dynamical.

- The solution is to make *fields*, not particles, the fundamental objects.

- Particles emerge as quantized excitations of fields.

- Quantum field theory describes physics using operator-valued fields on a Fock space that allows any number of particles.

## Exercises

**Exercise 1.1.** The electron mass is $m_e \approx 0.511$ MeV/$c^2$. What is the minimum photon energy required to produce an electron-positron pair $e^+e^-$? Explain why a single-particle quantum mechanics cannot describe what happens above this energy scale.

**Exercise 1.2.** In quantum mechanics I, the position of a particle $\hat{x}$ is an operator. In quantum field theory, the field $\hat{\phi}(\vec{x},t)$ is an operator, but $\vec{x}$ is merely a label (like time $t$ in QM I). Explain in your own words why promoting position from operator to label is a conceptual demotion of "position" and a promotion of "field."

**Exercise 1.3.** Consider the Fock space $\mathcal{F} = \bigoplus_{n=0}^{\infty} \mathcal{H}_n$. If $|0\rangle$ is the vacuum state and $a^\dagger$ creates a particle, describe what the states $|0\rangle$, $a^\dagger|0\rangle$, $(a^\dagger)^2|0\rangle$ represent physically. How does this compare with the harmonic oscillator raising operator from QM I?

---

# Chapter 2: Special Relativity and Four-Vector Notation

## Learning Objectives

After completing this chapter, the student will be able to:

1. Write physical quantities using four-vector notation and the Einstein summation convention.

2. Use the Minkowski metric to raise and lower indices.

3. Construct Lorentz-invariant quantities.

4. Express derivatives, momenta, and the d'Alembertian in covariant notation.

---

## 2.1 Why We Need Relativistic Notation

The Standard Model is a relativistic quantum field theory. Every equation we will write must respect Lorentz invariance — meaning it takes the same form in all inertial reference frames. To make this invariance manifest, we use a compact notation built on four-vectors and tensors. Mastering this notation now will save enormous effort later.

## 2.2 Spacetime and Events

In special relativity, space and time are unified into a single four-dimensional continuum called **spacetime**. An event is specified by four coordinates:

$$x^\mu = (x^0, x^1, x^2, x^3) = (ct, x, y, z)$$

The index $\mu$ runs over $\{0, 1, 2, 3\}$, where $0$ is the time component and $1, 2, 3$ are spatial components.

> **Convention:** Throughout this book, we use **natural units** where $c = \hbar = 1$. In these units, energy, momentum, and mass all have the same dimension (which we call "energy" and measure in electron-volts, eV). Length and time both have dimensions of inverse energy. This simplifies every equation. We can always restore $c$ and $\hbar$ by dimensional analysis at the end.

In natural units:

$$x^\mu = (t, x, y, z) = (t, \vec{x})$$

## 2.3 The Minkowski Metric

The spacetime interval between two events is:

$$ds^2 = dt^2 - dx^2 - dy^2 - dz^2$$

This is preserved by Lorentz transformations. We encode it in the **Minkowski metric tensor**:

$$\eta_{\mu\nu} = \text{diag}(+1, -1, -1, -1) = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0 & -1 & 0 & 0 \\ 0 & 0 & -1 & 0 \\ 0 & 0 & 0 & -1 \end{pmatrix}$$

> **Convention alert.** There are two common sign conventions for the metric: $(+,-,-,-)$ (sometimes called "mostly minus" or "particle physics convention") and $(-,+,+,+)$ ("mostly plus" or "general relativity convention"). We use the **mostly minus** convention $(+,-,-,-)$ throughout this book.

The inverse metric $\eta^{\mu\nu}$ satisfies $\eta^{\mu\alpha}\eta_{\alpha\nu} = \delta^\mu_{\ \nu}$. Numerically, $\eta^{\mu\nu}$ has the same components as $\eta_{\mu\nu}$ for the Minkowski metric.

## 2.4 The Einstein Summation Convention

> **Convention 2.1 (Einstein Summation).** When an index appears once as a superscript (upper index) and once as a subscript (lower index) in a single term, summation over all values of that index ($0,1,2,3$) is implied.

Example:

$$A^\mu B_\mu \equiv \sum_{\mu=0}^{3} A^\mu B_\mu = A^0 B_0 + A^1 B_1 + A^2 B_2 + A^3 B_3$$

A repeated summed index is called a **dummy index** or **contracted index**. An uncontracted index is called a **free index**.

## 2.5 Raising and Lowering Indices

The metric tensor converts upper indices to lower indices and vice versa:

$$x_\mu \equiv \eta_{\mu\nu} x^\nu$$

Explicitly:

$$x_0 = x^0 = t, \quad x_1 = -x^1 = -x, \quad x_2 = -x^2 = -y, \quad x_3 = -x^3 = -z$$

So: $x_\mu = (t, -x, -y, -z) = (t, -\vec{x})$.

To raise: $x^\mu = \eta^{\mu\nu} x_\nu$.

The **spacetime interval** can be written as:

$$ds^2 = \eta_{\mu\nu} dx^\mu dx^\nu = dx^\mu dx_\mu$$

## 2.6 Lorentz Transformations

A Lorentz transformation is a linear transformation $x^\mu \to x'^\mu = \Lambda^\mu_{\ \nu} x^\nu$ that preserves the spacetime interval:

$$\eta_{\mu\nu} \Lambda^\mu_{\ \alpha} \Lambda^\nu_{\ \beta} = \eta_{\alpha\beta}$$

This defines the **Lorentz group**. It includes:

- **Rotations** in three-dimensional space

- **Boosts** (changes of velocity between inertial frames)

A quantity that does not change under Lorentz transformations is called a **Lorentz scalar** or **Lorentz invariant**.

## 2.7 Important Four-Vectors

### Four-Momentum

$$p^\mu = (E, \vec{p}) = (E, p_x, p_y, p_z)$$

The Lorentz-invariant quantity:

$$p^\mu p_\mu = p^2 = E^2 - |\vec{p}|^2 = m^2$$

This is the relativistic energy-momentum relation (in natural units).

### Four-Derivative

$$\partial_\mu \equiv \frac{\partial}{\partial x^\mu} = \left(\frac{\partial}{\partial t}, \frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z}\right) = \left(\frac{\partial}{\partial t}, \vec{\nabla}\right)$$

Note: $\partial_\mu$ carries a lower index. The upper-index version is:

$$\partial^\mu = \eta^{\mu\nu} \partial_\nu = \left(\frac{\partial}{\partial t}, -\vec{\nabla}\right)$$

### The d'Alembertian

$$\Box \equiv \partial^\mu \partial_\mu = \frac{\partial^2}{\partial t^2} - \nabla^2$$

This is the Lorentz-invariant generalization of the Laplacian $\nabla^2$.

## 2.8 Lorentz Scalars, Vectors, and Tensors

A **Lorentz scalar** $\phi(x)$ is unchanged: $\phi'(x') = \phi(x)$.

A **Lorentz four-vector** $V^\mu$ transforms as $V'^\mu = \Lambda^\mu_{\ \nu} V^\nu$.

A **Lorentz tensor** of rank 2, $T^{\mu\nu}$, transforms as $T'^{\mu\nu} = \Lambda^\mu_{\ \alpha} \Lambda^\nu_{\ \beta} T^{\alpha\beta}$.

**Key principle:** To write Lorentz-invariant equations, ensure that all free indices on both sides of the equation are in the same position (all upper or all lower) and match.

## 2.9 The Levi-Civita Symbol

We will later need the totally antisymmetric symbol:

$$\epsilon^{\mu\nu\rho\sigma}$$

defined by $\epsilon^{0123} = +1$ and antisymmetric under exchange of any two indices. It has $4! = 24$ nonzero components (half are $+1$, half are $-1$), and is zero whenever any two indices are equal.

## 2.10 Notation Summary Table

| Symbol | Name | Definition |

|---|---|---|

| $x^\mu$ | Contravariant position | $(t, \vec{x})$ |

| $x_\mu$ | Covariant position | $(t, -\vec{x})$ |

| $\eta_{\mu\nu}$ | Minkowski metric | diag$(+1,-1,-1,-1)$ |

| $p^\mu$ | Four-momentum | $(E, \vec{p})$ |

| $\partial_\mu$ | Four-derivative | $(\partial_t, \vec{\nabla})$ |

| $\partial^\mu$ | Raised four-derivative | $(\partial_t, -\vec{\nabla})$ |

| $\Box$ | d'Alembertian | $\partial_t^2 - \nabla^2$ |

| $A \cdot B$ | Lorentz inner product | $A^\mu B_\mu = \eta_{\mu\nu} A^\mu B^\nu$ |

## Conceptual Summary

- Spacetime is described by four coordinates $x^\mu = (t, \vec{x})$.

- The Minkowski metric $\eta_{\mu\nu} = \text{diag}(+1,-1,-1,-1)$ defines the geometry of spacetime.

- Physical laws must be Lorentz invariant: they take the same form in all inertial frames.

- The Einstein summation convention sums over repeated upper-lower index pairs.

- Every physical equation we write in this book will use this four-vector notation.

## Exercises

**Exercise 2.1.** Verify that $p^\mu p_\mu = m^2$ reduces to $E^2 = |\vec{p}|^2 + m^2$ in natural units. What does this equation give for a massless particle ($m=0$)?

**Exercise 2.2.** Show that $\partial_\mu x^\nu = \delta^\nu_\mu$ (the Kronecker delta). Then compute $\partial_\mu(x^\nu x_\nu)$.

**Exercise 2.3.** If $\phi(x)$ is a Lorentz scalar field and $A_\mu(x)$ is a Lorentz vector field, explain why $A^\mu \partial_\mu \phi$ is a Lorentz scalar but $A^\mu \partial^\nu \phi$ is a Lorentz tensor.

---

# Chapter 3: Classical Field Theory

## Learning Objectives

After completing this chapter, the student will be able to:

1. Write the Lagrangian density for classical fields.

2. Derive the Euler-Lagrange equations for fields from the action principle.

3. Construct the Lagrangian for the Klein-Gordon field and the electromagnetic field.

4. Understand the concept of equations of motion arising from a Lagrangian.

---

## 3.1 From Particle Mechanics to Field Theory

In classical mechanics, you learned the Lagrangian formalism. For a particle with generalized coordinate $q(t)$:

- **Lagrangian:** $L(q, \dot{q}) = T - V$

- **Action:** $S = \int dt\, L(q, \dot{q})$

- **Euler-Lagrange equation:** $\frac{d}{dt}\frac{\partial L}{\partial \dot{q}} - \frac{\partial L}{\partial q} = 0$

The equations of motion follow from demanding that the action $S$ is stationary under small variations $q(t) \to q(t) + \delta q(t)$ that vanish at the endpoints.

We now generalize this to **fields**. A field $\phi(\vec{x}, t) = \phi(x)$ depends on both space and time. The field plays the role of the dynamical variable, and $\vec{x}$ is just a continuous label (like the index $i$ labeling different particles).

## 3.2 The Lagrangian Density

For fields, the Lagrangian is an integral over space of a **Lagrangian density** $\mathcal{L}$:

$$L = \int d^3x\, \mathcal{L}(\phi, \partial_\mu \phi)$$

> **Definition 3.1 (Lagrangian Density).** The Lagrangian density $\mathcal{L}$ is a function of the field(s) $\phi(x)$ and their first spacetime derivatives $\partial_\mu \phi(x)$, evaluated at a single spacetime point $x$. It is a Lorentz scalar.

The **action** is:

$$S = \int d^4x\, \mathcal{L}(\phi, \partial_\mu \phi)$$

where $d^4x = dt\, d^3x$ is the four-dimensional spacetime volume element.

> **Key distinction:** $L$ is the Lagrangian (a function of time only, after spatial integration). $\mathcal{L}$ is the Lagrangian density (a function of the spacetime point $x$). In field theory, we almost always work with $\mathcal{L}$ and often just call it "the Lagrangian" when the context is clear.

## 3.3 The Euler-Lagrange Equation for Fields

**Principle of stationary action:** The physical field configuration $\phi(x)$ is the one that makes the action $S$ stationary: $\delta S = 0$.

We vary $\phi(x) \to \phi(x) + \delta\phi(x)$, require $\delta\phi = 0$ on the spacetime boundary, and compute:

$$\delta S = \int d^4x \left[\frac{\partial \mathcal{L}}{\partial \phi}\delta\phi + \frac{\partial \mathcal{L}}{\partial(\partial_\mu\phi)}\delta(\partial_\mu\phi)\right]$$

Since $\delta(\partial_\mu \phi) = \partial_\mu(\delta\phi)$, we integrate the second term by parts:

$$\delta S = \int d^4x \left[\frac{\partial \mathcal{L}}{\partial \phi} - \partial_\mu\frac{\partial \mathcal{L}}{\partial(\partial_\mu\phi)}\right]\delta\phi + \text{boundary terms}$$

The boundary terms vanish by assumption. Since $\delta\phi$ is arbitrary, we obtain:

> **Euler-Lagrange equation for fields:**

> $$\partial_\mu \frac{\partial \mathcal{L}}{\partial(\partial_\mu\phi)} - \frac{\partial \mathcal{L}}{\partial \phi} = 0 \tag{3.1}$$

This is the equation of motion for the field $\phi(x)$.

## 3.4 Example: The Real Klein-Gordon Field

The simplest Lorentz-invariant Lagrangian density for a real scalar field $\phi(x)$ is:

$$\mathcal{L}_{\text{KG}} = \frac{1}{2}(\partial_\mu\phi)(\partial^\mu\phi) - \frac{1}{2}m^2\phi^2 \tag{3.2}$$

Let us verify that this is sensible. The first term is:

$$\frac{1}{2}\partial_\mu\phi\, \partial^\mu\phi = \frac{1}{2}\left[(\partial_t\phi)^2 - (\vec{\nabla}\phi)^2\right]$$

which is the kinetic energy density minus the gradient energy density — a relativistic version of the kinetic term. The second term $-\frac{1}{2}m^2\phi^2$ is a "mass term" (potential energy density).

Applying the Euler-Lagrange equation (3.1):

$$\frac{\partial \mathcal{L}}{\partial \phi} = -m^2\phi, \quad \frac{\partial \mathcal{L}}{\partial(\partial_\mu\phi)} = \partial^\mu\phi$$

Therefore:

$$\partial_\mu \partial^\mu \phi + m^2\phi = 0$$

$$\boxed{(\Box + m^2)\phi = 0} \tag{3.3}$$

This is the **Klein-Gordon equation**, the relativistic wave equation for a scalar field of mass $m$. It generalizes the non-relativistic Schrödinger equation and is the simplest relativistic field equation.

## 3.5 Example: The Electromagnetic Field

The electromagnetic field in vacuum is described by the four-potential:

$$A^\mu(x) = (\Phi, \vec{A})$$

where $\Phi$ is the electric potential and $\vec{A}$ is the magnetic vector potential. The **field strength tensor** is:

$$F_{\mu\nu} \equiv \partial_\mu A_\nu - \partial_\nu A_\mu \tag{3.4}$$

This is an antisymmetric tensor ($F_{\mu\nu} = -F_{\nu\mu}$). Its components encode the electric and magnetic fields:

$$F_{0i} = \partial_0 A_i - \partial_i A_0 = -E_i, \quad F_{ij} = \partial_i A_j - \partial_j A_i = -\epsilon_{ijk}B_k$$

The Lagrangian density for the free electromagnetic field is:

$$\mathcal{L}_{\text{EM}} = -\frac{1}{4}F_{\mu\nu}F^{\mu\nu} \tag{3.5}$$

Expanding this out:

$$\mathcal{L}_{\text{EM}} = \frac{1}{2}(\vec{E}^2 - \vec{B}^2)$$

Applying the Euler-Lagrange equations to this Lagrangian yields Maxwell's equations in vacuum. We will return to this in Chapter 8.

## 3.6 Multiple Fields and Interactions

When a theory contains multiple fields $\phi_1, \phi_2, \ldots$, the Lagrangian density depends on all of them:

$$\mathcal{L} = \mathcal{L}(\phi_1, \phi_2, \ldots, \partial_\mu\phi_1, \partial_\mu\phi_2, \ldots)$$

Each field has its own Euler-Lagrange equation.

Interactions between fields arise from terms in $\mathcal{L}$ that involve products of different fields. For example, a coupling between a scalar field $\phi$ and a fermion field $\psi$ might look like $\mathcal{L}_{\text{int}} = -g\phi\bar\psi\psi$, where $g$ is a **coupling constant** that sets the strength of the interaction.

## 3.7 The Importance of the Lagrangian

In modern particle physics, the Lagrangian density is the central object. Once you specify $\mathcal{L}$, you have completely defined the theory: the particle content (which fields appear), their masses (from quadratic terms), and all their interactions (from higher-order terms). The rest of this book is, in essence, the story of how to determine the correct $\mathcal{L}$ for fundamental physics.

## Conceptual Summary

- Classical field theory is built by generalizing the Lagrangian formalism from particle coordinates $q(t)$ to field configurations $\phi(x)$.

- The Lagrangian density $\mathcal{L}(\phi, \partial_\mu\phi)$ is a Lorentz scalar encoding all dynamics.

- The action $S = \int d^4x\, \mathcal{L}$ is extremized to yield the Euler-Lagrange equations of motion.

- The Klein-Gordon equation $(\Box + m^2)\phi = 0$ describes a free massive scalar field.

- The electromagnetic Lagrangian $-\frac{1}{4}F_{\mu\nu}F^{\mu\nu}$ generates Maxwell's equations.

- Specifying $\mathcal{L}$ is specifying the complete theory.

## Exercises

**Exercise 3.1.** Consider the Lagrangian $\mathcal{L} = \frac{1}{2}\partial_\mu\phi\,\partial^\mu\phi - \frac{\lambda}{4!}\phi^4$, where $\lambda > 0$ is a coupling constant. Derive the equation of motion. The $\phi^4$ term represents a self-interaction. How does this differ from the Klein-Gordon equation?

**Exercise 3.2.** Verify that $F_{\mu\nu}F^{\mu\nu} = -2(\vec{E}^2 - \vec{B}^2)$ by writing out the components of $F_{\mu\nu}$ in terms of $\vec{E}$ and $\vec{B}$.

**Exercise 3.3.** Why must $\mathcal{L}$ be a Lorentz scalar? What would go wrong physically if $\mathcal{L}$ depended on the reference frame?

---

# Chapter 4: Symmetries and Conservation Laws

## Learning Objectives

After completing this chapter, the student will be able to:

1. Define continuous symmetries of a Lagrangian.

2. State and apply Noether's theorem.

3. Distinguish between spacetime and internal symmetries.

4. Explain the concept of a conserved current.

5. Understand global internal symmetries as a precursor to gauge symmetry.

---

## 4.1 What Is a Symmetry?

> **Definition 4.1 (Symmetry).** A symmetry of a physical theory is a transformation of the fields and/or coordinates that leaves the action $S = \int d^4x\, \mathcal{L}$ invariant.

More precisely, a transformation $\phi(x) \to \phi'(x)$ is a symmetry if $\mathcal{L}(\phi', \partial_\mu\phi') = \mathcal{L}(\phi, \partial_\mu\phi)$ (or more generally, if $\mathcal{L}$ changes by at most a total derivative, which does not affect the equations of motion).

Symmetries are the most powerful organizing principle in physics. They constrain the form of the Lagrangian, determine the particle content, and guarantee conservation laws.

## 4.2 Noether's Theorem

> **Theorem 4.1 (Noether's Theorem).** Every continuous symmetry of the action is associated with a conserved current $j^\mu(x)$ satisfying $\partial_\mu j^\mu = 0$, and hence a conserved charge $Q = \int d^3x\, j^0(x)$.

This is one of the most profound results in theoretical physics. Let us prove it for internal symmetries (transformations that change the fields but not the coordinates).

**Proof sketch.** Suppose $\phi(x) \to \phi(x) + \alpha\, \delta\phi(x)$ is a symmetry, where $\alpha$ is a constant infinitesimal parameter. Then by definition $\delta\mathcal{L} = 0$ (or a total derivative — let us take $\delta\mathcal{L}=0$ for simplicity). On the other hand, computing $\delta\mathcal{L}$ directly:

$$\delta\mathcal{L} = \frac{\partial\mathcal{L}}{\partial\phi}\delta\phi + \frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)}\partial_\mu(\delta\phi)$$

Using the Euler-Lagrange equation to replace $\frac{\partial\mathcal{L}}{\partial\phi} = \partial_\mu\frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)}$:

$$\delta\mathcal{L} = \left[\partial_\mu\frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)}\right]\delta\phi + \frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)}\partial_\mu(\delta\phi) = \partial_\mu\left[\frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)}\delta\phi\right]$$

Since $\delta\mathcal{L} = 0$, we obtain $\partial_\mu j^\mu = 0$ with:

$$\boxed{j^\mu = \frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)}\delta\phi} \tag{4.1}$$

The conserved charge is:

$$Q = \int d^3x\, j^0(x), \quad \frac{dQ}{dt} = 0$$

## 4.3 Spacetime Symmetries

**Translation invariance** ($x^\mu \to x^\mu + a^\mu$) leads to conservation of four-momentum. The associated conserved object is the **energy-momentum tensor** $T^{\mu\nu}$.

**Rotational invariance** leads to conservation of angular momentum.

**Lorentz boost invariance** leads to conservation of the center-of-energy motion.

These are the symmetries associated with the Poincaré group (Lorentz group + translations), and they are built into any Lorentz-invariant field theory automatically.

## 4.4 Internal Symmetries: The Key Idea

The symmetries that will matter most for us are **internal symmetries** — transformations that mix field components but do not affect spacetime coordinates.

### 4.4.1 A Simple Example: U(1) Global Symmetry

Consider a complex scalar field $\phi(x)$ (which has two real degrees of freedom: $\phi = \frac{1}{\sqrt{2}}(\phi_1 + i\phi_2)$) with Lagrangian:

$$\mathcal{L} = \partial_\mu\phi^*\,\partial^\mu\phi - m^2\phi^*\phi - \lambda(\phi^*\phi)^2$$

Now consider the transformation:

$$\phi(x) \to e^{i\alpha}\phi(x), \quad \phi^*(x) \to e^{-i\alpha}\phi^*(x)$$

where $\alpha$ is a real constant. Since $\phi^*\phi \to e^{-i\alpha}e^{i\alpha}\phi^*\phi = \phi^*\phi$, and similarly for the kinetic term, the Lagrangian is invariant.

This is a **global U(1) symmetry**: the transformation is the same at every spacetime point (hence "global"), and the set of transformations $\{e^{i\alpha} : \alpha \in \mathbb{R}\}$ forms the group $U(1)$ (unitary $1\times 1$ matrices, i.e., complex phases).

By Noether's theorem, the conserved current is:

$$j^\mu = i(\phi^*\partial^\mu\phi - \phi\,\partial^\mu\phi^*)$$

and the conserved charge $Q = \int d^3x\, j^0$ can be interpreted as **particle number** (or, after quantization, the difference between particle and antiparticle numbers). This is the prototype of electric charge conservation.

### 4.4.2 Global SU(N) Symmetry: A Preview

Now suppose we have $N$ complex scalar fields $\phi_i(x)$, $i = 1, \ldots, N$, arranged into a column vector:

$$\Phi = \begin{pmatrix} \phi_1 \\ \phi_2 \\ \vdots \\ \phi_N \end{pmatrix}$$

Consider the Lagrangian:

$$\mathcal{L} = \partial_\mu\Phi^\dagger \partial^\mu\Phi - m^2\Phi^\dagger\Phi - \lambda(\Phi^\dagger\Phi)^2$$

This is invariant under:

$$\Phi(x) \to U\Phi(x)$$

where $U$ is any constant $N\times N$ **unitary matrix** ($U^\dagger U = UU^\dagger = \mathbb{I}$). The set of such matrices forms the group $U(N)$. If we further require $\det(U) = 1$, we get the **special unitary group** $SU(N)$.

This non-Abelian (non-commutative) symmetry will be crucial: the Standard Model is built on $SU(3) \times SU(2) \times U(1)$.

## 4.5 Global vs. Local Symmetries: A Crucial Preview

Notice that in the examples above, $\alpha$ and $U$ are constants — the same at every point in spacetime. This makes them **global** symmetries.

A profound question arises: *What happens if we demand the symmetry hold locally — allowing the transformation parameter to vary from point to point?* That is, what if we require invariance under:

$$\phi(x) \to e^{i\alpha(x)}\phi(x)$$

where $\alpha(x)$ depends on $x$?

This seemingly innocent change will force us to introduce new fields — the **gauge fields** — and will lead us directly to the forces of nature. This is the subject of Chapters 8-10.

## 4.6 The Connection Between Symmetry and Physics

Let us emphasize why symmetries are so central:

1. **Conservation laws:** Every continuous symmetry yields a conserved quantity (Noether).

2. **Selection rules:** Symmetries constrain which processes can occur.

3. **Lagrangian structure:** Requiring a symmetry dramatically restricts the allowed terms in $\mathcal{L}$.

4. **Forces from symmetries:** As we will see, promoting global symmetries to local (gauge) symmetries generates interaction terms — the forces between particles.

The Standard Model is, at its core, the most general renormalizable Lagrangian consistent with the gauge symmetry $SU(3)_C \times SU(2)_L \times U(1)_Y$ and the known particle content.

## Conceptual Summary

- A symmetry is a transformation that leaves the action invariant.

- Noether's theorem: every continuous symmetry → conserved current → conserved charge.

- Spacetime symmetries (translations, rotations, boosts) yield conservation of energy, momentum, angular momentum.

- Internal symmetries (U(1), SU(N)) yield conserved quantum numbers (charge, color, etc.).

- Global symmetries use constant transformation parameters; local (gauge) symmetries use spacetime-dependent parameters.

- Requiring local invariance will force us to introduce gauge fields, generating the fundamental forces.

## Exercises

**Exercise 4.1.** For the complex scalar field with $\mathcal{L} = \partial_\mu\phi^*\partial^\mu\phi - m^2|\phi|^2$, verify that $j^\mu = i(\phi^*\partial^\mu\phi - \phi\partial^\mu\phi^*)$ is conserved by showing $\partial_\mu j^\mu = 0$ using the equations of motion.

**Exercise 4.2.** Explain in words why a term like $\lambda\phi^3$ in the Lagrangian for a complex field $\phi$ would *break* the U(1) symmetry, while $\lambda(\phi^*\phi)^2$ preserves it. What physical conservation law would be violated?

**Exercise 4.3.** A Lagrangian for two real scalar fields $\phi_1, \phi_2$ with the same mass has the form $\mathcal{L} = \frac{1}{2}(\partial_\mu\phi_1)^2 + \frac{1}{2}(\partial_\mu\phi_2)^2 - \frac{1}{2}m^2(\phi_1^2 + \phi_2^2)$. Show that this Lagrangian is invariant under SO(2) rotations in the internal $(\phi_1, \phi_2)$ space. How many conserved charges does Noether's theorem predict?

---

# Chapter 5: Quantum Fields — Conceptual Framework

## Learning Objectives

After completing this chapter, the student will be able to:

1. Describe the quantization of a scalar field conceptually.

2. Interpret particles as excitations of quantum fields.

3. Understand creation and annihilation operators in the field theory context.

4. Grasp the structure of Fock space.

5. Understand the vacuum state and vacuum fluctuations.

---

## 5.1 Quantizing the Scalar Field: Overview

In Chapter 3, we treated $\phi(x)$ as a classical field. Now we promote it to a quantum operator $\hat{\phi}(x)$, just as in QM I we promoted the classical position $x$ to the operator $\hat{x}$.

For the free Klein-Gordon field, the key result (which we state without complete derivation, as the algebraic structure is what matters for us) is:

$$\hat{\phi}(x) = \int \frac{d^3p}{(2\pi)^3}\frac{1}{\sqrt{2E_{\vec{p}}}}\left[\hat{a}_{\vec{p}}\, e^{-ip\cdot x} + \hat{a}_{\vec{p}}^\dagger\, e^{+ip\cdot x}\right] \tag{5.1}$$

where $E_{\vec{p}} = \sqrt{|\vec{p}|^2 + m^2}$, and $p\cdot x = E_{\vec{p}}t - \vec{p}\cdot\vec{x}$.

The operators $\hat{a}_{\vec{p}}$ and $\hat{a}_{\vec{p}}^\dagger$ satisfy the **commutation relations**:

$$[\hat{a}_{\vec{p}}, \hat{a}_{\vec{q}}^\dagger] = (2\pi)^3\delta^{(3)}(\vec{p}-\vec{q}) \tag{5.2}$$

$$[\hat{a}_{\vec{p}}, \hat{a}_{\vec{q}}] = [\hat{a}_{\vec{p}}^\dagger, \hat{a}_{\vec{q}}^\dagger] = 0$$

These are exactly the algebra of harmonic oscillator raising and lowering operators — one for each momentum $\vec{p}$. This is no accident: a free field is mathematically equivalent to infinitely many independent harmonic oscillators, one at each momentum.

## 5.2 Particle Interpretation

- $\hat{a}_{\vec{p}}^\dagger$ **creates** a particle with momentum $\vec{p}$.

- $\hat{a}_{\vec{p}}$ **annihilates** a particle with momentum $\vec{p}$.

The **vacuum state** $|0\rangle$ is defined as the state with no particles:

$$\hat{a}_{\vec{p}}|0\rangle = 0 \quad \text{for all } \vec{p}$$

A one-particle state with momentum $\vec{p}$ is:

$$|\vec{p}\rangle = \hat{a}_{\vec{p}}^\dagger|0\rangle$$

A two-particle state:

$$|\vec{p}_1, \vec{p}_2\rangle = \hat{a}_{\vec{p}_1}^\dagger\hat{a}_{\vec{p}_2}^\dagger|0\rangle$$

And so on. The collection of all such states forms the **Fock space** $\mathcal{F}$.

**This is the central insight of quantum field theory: each type of particle in nature corresponds to a quantum field, and individual particles are quantized excitations of that field.**

## 5.3 Spin and Statistics

A crucial result from quantum field theory (the **spin-statistics theorem**) states:

- **Integer-spin fields** (spin 0, 1, 2, ...) must be quantized with **commutation** relations. Their particles are **bosons**. Example: photons, Higgs boson.

- **Half-integer-spin fields** (spin 1/2, 3/2, ...) must be quantized with **anticommutation** relations. Their particles are **fermions**. Example: electrons, quarks.

For fermions, the creation and annihilation operators satisfy $\{\hat{b}_{\vec{p}}, \hat{b}_{\vec{q}}^\dagger\} = (2\pi)^3\delta^{(3)}(\vec{p}-\vec{q})$, where $\{A,B\} \equiv AB + BA$ is the anticommutator. This automatically enforces the Pauli exclusion principle.

## 5.4 Antiparticles

For a complex field (as opposed to a real field), the expansion involves two sets of operators:

$$\hat{\phi}(x) = \int \frac{d^3p}{(2\pi)^3\sqrt{2E_{\vec{p}}}}\left[\hat{a}_{\vec{p}}\, e^{-ipx} + \hat{b}_{\vec{p}}^\dagger\, e^{+ipx}\right]$$

Here $\hat{a}_{\vec{p}}^\dagger$ creates a **particle** and $\hat{b}_{\vec{p}}^\dagger$ creates an **antiparticle**. The particle and antiparticle have the same mass but opposite quantum numbers (like electric charge). The electron field creates electrons and positrons.

## 5.5 The Vacuum Is Not Empty

Even the vacuum $|0\rangle$ is not trivially "empty." Quantum fields have fluctuations in the vacuum state — **vacuum fluctuations**. These are not just theoretical curiosities; they produce measurable effects like the Casimir effect and the Lamb shift. More importantly for us, vacuum fluctuations are responsible for the divergences we will encounter in loop diagrams (Chapter 14).

## 5.6 The Hamiltonian and Energy

The total energy (Hamiltonian) of the free scalar field can be expressed as:

$$\hat{H} = \int \frac{d^3p}{(2\pi)^3}\, E_{\vec{p}}\, \hat{a}_{\vec{p}}^\dagger \hat{a}_{\vec{p}} + \text{(infinite constant)}$$

The operator $\hat{a}_{\vec{p}}^\dagger \hat{a}_{\vec{p}}$ is the **number operator** for mode $\vec{p}$. The infinite constant (vacuum energy) is discarded by normal ordering (a regularization procedure) — it is an early hint that quantum field theory has infinities that need careful treatment.

## Conceptual Summary

- Quantizing a field means promoting it to an operator on Fock space.

- The field decomposes into creation and annihilation operators for each momentum mode.

- Particles are quantized excitations of the field: $|\vec{p}\rangle = a^\dagger_{\vec{p}}|0\rangle$.

- Integer-spin particles are bosons (commutation relations); half-integer-spin are fermions (anticommutation relations).

- Complex fields describe both particles and antiparticles.

- The vacuum has quantum fluctuations.

## Exercises

**Exercise 5.1.** Using $[a_{\vec{p}}, a_{\vec{q}}^\dagger] = (2\pi)^3\delta^{(3)}(\vec{p}-\vec{q})$, show that the one-particle state $|\vec{p}\rangle = a_{\vec{p}}^\dagger|0\rangle$ has energy $E_{\vec{p}}$ by computing $H|\vec{p}\rangle$.

**Exercise 5.2.** Explain why a real scalar field $\phi = \phi^*$ has no antiparticle distinct from the particle itself, while a complex field does.

**Exercise 5.3.** Draw a parallel between the quantum harmonic oscillator from QM I (with states $|n\rangle = \frac{(a^\dagger)^n}{\sqrt{n!}}|0\rangle$) and the quantum field theory Fock space. What replaces the quantum number $n$?

---

# Chapter 6: Interactions and Feynman Diagrams

## Learning Objectives

After completing this chapter, the student will be able to:

1. Understand how interactions are encoded in the Lagrangian.

2. Explain the basic idea of perturbation theory in QFT.

3. Read simple Feynman diagrams and extract physical content.

4. Understand the role of coupling constants.

5. Recognize that loops in Feynman diagrams correspond to quantum corrections.

---

## 6.1 Free vs. Interacting Theories

A free field theory (like the Klein-Gordon theory with just a mass term) is exactly solvable but boring: particles travel without ever interacting. All the interesting physics comes from **interaction terms** in the Lagrangian.

Consider the scalar field with a self-interaction:

$$\mathcal{L} = \frac{1}{2}(\partial_\mu\phi)^2 - \frac{1}{2}m^2\phi^2 - \frac{\lambda}{4!}\phi^4$$

The last term describes a process where four $\phi$-particles meet at a point and interact. The coupling constant $\lambda$ controls the strength of this interaction.

## 6.2 Perturbation Theory

Exact solutions to interacting quantum field theories are generally impossible. Instead, we use **perturbation theory**: we treat the interaction as a small perturbation (when $\lambda$ is small) and compute observables as a power series in $\lambda$.

The key quantity in particle physics is the **scattering amplitude** $\mathcal{M}$, which determines the probability that some set of initial particles will scatter into some set of final particles. The probability is proportional to $|\mathcal{M}|^2$.

In perturbation theory:

$$\mathcal{M} = \mathcal{M}^{(0)} + \lambda \mathcal{M}^{(1)} + \lambda^2 \mathcal{M}^{(2)} + \cdots$$

Each term involves increasingly complicated integrals. Richard Feynman devised a brilliant graphical method to organize this expansion.

## 6.3 Feynman Diagrams

A **Feynman diagram** is a pictorial representation of a term in the perturbative expansion of a scattering amplitude. Each diagram contains:

- **External lines:** represent the incoming and outgoing particles.

- **Internal lines (propagators):** represent virtual particles exchanged during the interaction. Each propagator is associated with a mathematical expression involving the particle's momentum and mass.

- **Vertices:** represent interaction events, where lines meet. Each vertex is associated with a coupling constant from $\mathcal{L}$.

### 6.3.1 Feynman Rules

Each Lagrangian generates a set of **Feynman rules** — a dictionary that translates every element of a diagram into a mathematical expression. The rules for $\phi^4$ theory:

1. **Propagator** (internal line): $\frac{i}{p^2 - m^2 + i\epsilon}$ (where $\epsilon \to 0^+$ is a small positive number ensuring correct boundary conditions).

2. **Vertex** (four lines meeting): $-i\lambda$.

3. **External lines**: contribute factors of 1 (for scalars).

4. **Conservation**: four-momentum is conserved at every vertex.

5. **Integration**: integrate $\int \frac{d^4k}{(2\pi)^4}$ over every undetermined loop momentum.

### 6.3.2 Example: Tree-Level Scattering

The simplest $\phi\phi \to \phi\phi$ scattering in $\phi^4$ theory involves a single vertex:

```

p₁ ──────┐

╳ (vertex, factor -iλ)

p₂ ──────┘──── p₃

└──── p₄

```

The amplitude is simply $\mathcal{M} = -i\lambda$ at lowest order. This is called a **tree-level** or **Born-level** diagram (no loops).

### 6.3.3 Loop Diagrams and Quantum Corrections

At the next order in $\lambda$, diagrams acquire **loops**:

```

p₁ ──╳──○──╳── p₃

p₂ ──┘ └── p₄

```

where the circle represents a closed loop of virtual particles. The loop requires integrating over all possible loop momenta:

$$\int \frac{d^4k}{(2\pi)^4} \frac{i}{k^2 - m^2}\frac{i}{(p-k)^2 - m^2}$$

This integral often **diverges** — it gives infinity. Dealing with these infinities is the subject of **renormalization** (Chapter 14).

## 6.4 The Exchange of Particles as Force

A profound reinterpretation: the **forces between particles are mediated by the exchange of other particles.** When two electrons repel each other, they exchange a virtual photon. When quarks attract each other inside a proton, they exchange virtual gluons.

In a Feynman diagram, a force-mediating particle appears as an internal line connecting two vertices:

```

e⁻ ────╳~~~~╳──── e⁻

γ (photon)

e⁻ ────╳~~~~╳──── e⁻

```

The wavy line ($\sim$) represents a photon propagator. The fact that the photon has zero mass leads to a long-range ($1/r$) Coulomb force. If the mediating particle is massive, the force is short-range.

## 6.5 Line Types by Particle Spin

Different line styles denote different particle types in Feynman diagrams:

| Line style | Particle type | Spin | Examples |

|---|---|---|---|

| Solid line with arrow | Fermion | 1/2 | Electron, quark |

| Wavy line | Gauge boson | 1 | Photon, W, Z |

| Curly line | Gluon | 1 | Gluon |

| Dashed line | Scalar | 0 | Higgs boson |

Fermion lines carry arrows that indicate the flow of particle number (or equivalently, charge flow).

## 6.6 Coupling Constants and Perturbativity

The coupling constant determines:

1. The strength of the interaction at each vertex.

2. Whether perturbation theory is reliable.

If $g$ is the coupling at each vertex, a diagram with $n$ vertices contributes proportionally to $g^n$. For perturbation theory to work, we need $g$ (or $g^2/(4\pi)$) to be small enough that higher-order terms are suppressed.

In QED, the fine structure constant $\alpha = e^2/(4\pi) \approx 1/137$ is small, so perturbation theory works beautifully. In QCD, the coupling is large at low energies (this is related to **confinement**) but small at high energies (**asymptotic freedom**) — we will explore this in Chapters 12 and 15.

## Conceptual Summary

- Interactions appear as non-quadratic terms in $\mathcal{L}$ (e.g., $\phi^4$, $\bar{\psi}A_\mu\gamma^\mu\psi$).

- Feynman diagrams graphically represent terms in a perturbation series.

- Tree diagrams give the leading-order (classical) contribution; loop diagrams give quantum corrections.

- Forces between particles are mediated by the exchange of virtual particles.

- Loop diagrams involve integrals over all virtual momenta and typically diverge, necessitating renormalization.

## Exercises

**Exercise 6.1.** In $\phi^4$ theory, how many factors of $\lambda$ appear in a diagram with 3 vertices? How does the amplitude of this diagram scale with $\lambda$ compared to a 1-vertex diagram?

**Exercise 6.2.** Explain why a Feynman diagram with no loops (a tree diagram) can be considered a "classical" contribution, while loops represent quantum effects. *Hint:* each loop introduces one factor of $\hbar$ when natural units are restored.

**Exercise 6.3.** In QED, the electron-photon vertex has coupling constant $e$. A tree-level diagram for electron-electron scattering via single photon exchange has two vertices. What is the amplitude proportional to? How does this relate to Coulomb's law?

---

# Chapter 7: Fermions and the Dirac Equation

## Learning Objectives

After completing this chapter, the student will be able to:

1. Understand the need for spinor representations of the Lorentz group.

2. Write down the Dirac equation and Dirac Lagrangian.

3. Define the gamma matrices and their algebra.

4. Understand the meaning of the Dirac adjoint $\bar{\psi}$.

5. Know the physical content of the Dirac field: spin-1/2 particles and antiparticles.

---

## 7.1 Why Spinors?

Scalar fields ($\phi$) describe spin-0 particles. Vector fields ($A^\mu$) describe spin-1 particles. To describe electrons, quarks, and all other fermions (spin-1/2), we need a new type of field: a **spinor field**.

A spinor is a mathematical object that transforms under a specific representation of the Lorentz group — one that does not exist for ordinary vectors. Under a rotation by $2\pi$, a vector returns to itself, but a spinor picks up a minus sign. Only after a $4\pi$ rotation does a spinor return to its original value.

## 7.2 The Dirac Gamma Matrices

The **Dirac gamma matrices** $\gamma^\mu$ ($\mu = 0,1,2,3$) are four $4 \times 4$ matrices satisfying the **Clifford algebra**:

$$\{\gamma^\mu, \gamma^\nu\} \equiv \gamma^\mu\gamma^\nu + \gamma^\nu\gamma^\mu = 2\eta^{\mu\nu}\mathbb{I}_{4\times4} \tag{7.1}$$

This anticommutation relation defines the gamma matrices up to unitary equivalence. Key properties:

- $(\gamma^0)^2 = \mathbb{I}$, $(\gamma^i)^2 = -\mathbb{I}$ (for $i = 1,2,3$).

- $(\gamma^0)^\dagger = \gamma^0$, $(\gamma^i)^\dagger = -\gamma^i$.

We also define the important matrix:

$$\gamma^5 \equiv i\gamma^0\gamma^1\gamma^2\gamma^3 \tag{7.2}$$

which satisfies $(\gamma^5)^2 = \mathbb{I}$ and $\{\gamma^5, \gamma^\mu\} = 0$. This matrix plays a crucial role in distinguishing left-handed and right-handed fermions, which is essential for the weak interaction.

## 7.3 The Dirac Equation

The **Dirac field** $\psi(x)$ is a four-component complex spinor. The Dirac equation is:

$$(i\gamma^\mu\partial_\mu - m)\psi(x) = 0 \tag{7.3}$$

Using the Feynman slash notation $\slashed{\partial} \equiv \gamma^\mu\partial_\mu$:

$$(i\slashed{\partial} - m)\psi = 0$$

The corresponding Lagrangian density is:

$$\mathcal{L}_{\text{Dirac}} = \bar{\psi}(i\slashed{\partial} - m)\psi = \bar{\psi}(i\gamma^\mu\partial_\mu - m)\psi \tag{7.4}$$

where the **Dirac adjoint** is defined as:

$$\bar{\psi} \equiv \psi^\dagger \gamma^0 \tag{7.5}$$

The $\gamma^0$ factor is necessary to make $\bar{\psi}\psi$ a Lorentz scalar (rather than the naive $\psi^\dagger\psi$, which transforms like the time component of a four-vector).

## 7.4 Physical Content

The Dirac equation describes:

- **Particles** with spin 1/2 (e.g., electrons) — two spin states (up and down).

- **Antiparticles** with spin 1/2 (e.g., positrons) — two spin states.

Total: four degrees of freedom, matching the four components of $\psi$.

## 7.5 Chirality: Left-Handed and Right-Handed Fermions

Using $\gamma^5$, we can define **projection operators**:

$$P_L = \frac{1 - \gamma^5}{2}, \quad P_R = \frac{1 + \gamma^5}{2} \tag{7.6}$$

These satisfy $P_L + P_R = \mathbb{I}$, $P_L^2 = P_L$, $P_R^2 = P_R$, $P_L P_R = 0$.

The **left-handed** and **right-handed** components of $\psi$ are:

$$\psi_L = P_L\psi, \quad \psi_R = P_R\psi$$

**Chirality is central to the Standard Model.** The weak interaction treats left-handed and right-handed fermions differently: left-handed fermions participate in weak interactions, while right-handed fermions do not (more precisely, they carry different gauge quantum numbers). This is called **parity violation** and is a fundamental feature of nature.

## 7.6 Lorentz Covariant Bilinears

The following quantities, built from $\bar{\psi}$ and $\psi$, transform in well-defined ways under the Lorentz group:

| Bilinear | Lorentz type | Components |

|---|---|---|

| $\bar{\psi}\psi$ | Scalar | 1 |

| $\bar{\psi}\gamma^5\psi$ | Pseudoscalar | 1 |

| $\bar{\psi}\gamma^\mu\psi$ | Vector | 4 |

| $\bar{\psi}\gamma^\mu\gamma^5\psi$ | Axial vector | 4 |

| $\bar{\psi}\sigma^{\mu\nu}\psi$ | Tensor | 6 |

where $\sigma^{\mu\nu} = \frac{i}{2}[\gamma^\mu, \gamma^\nu]$. These bilinears are the building blocks for constructing Lorentz-invariant interaction terms in the Lagrangian.

## 7.7 Multiple Fermion Flavors

In the Standard Model, there are multiple types (flavors) of fermions. Each flavor has its own Dirac field: $\psi_e$ for the electron, $\psi_u$ for the up quark, etc. When we discuss gauge symmetry, these fields will also carry gauge indices.

## Conceptual Summary

- Spin-1/2 particles require spinor fields — four-component objects satisfying the Dirac equation.

- The gamma matrices satisfy $\{\gamma^\mu, \gamma^\nu\} = 2\eta^{\mu\nu}$ and encode the coupling between spin and spacetime.

- The Dirac Lagrangian $\bar{\psi}(i\slashed{\partial}-m)\psi$ describes a massive fermion and its antiparticle.

- $\gamma^5$ defines chirality; $P_{L,R} = (1\mp\gamma^5)/2$ project onto left/right-handed components.

- The weak force distinguishes left-handed from right-handed fermions.

- Lorentz-covariant bilinears $\bar{\psi}\Gamma\psi$ are the building blocks for constructing invariant interactions.

## Exercises

**Exercise 7.1.** Using the Clifford algebra $\{\gamma^\mu, \gamma^\nu\} = 2\eta^{\mu\nu}$, show that $(\gamma^0)^2 = \mathbb{I}$ and $(\gamma^1)^2 = -\mathbb{I}$.

**Exercise 7.2.** Verify that $P_L = \frac{1-\gamma^5}{2}$ is a projection operator: show $P_L^2 = P_L$ and $P_L P_R = 0$.

**Exercise 7.3.** The Dirac mass term is $-m\bar{\psi}\psi = -m(\bar{\psi}_L\psi_R + \bar{\psi}_R\psi_L)$. Explain in words why a mass term *mixes* left-handed and right-handed components. Why would this be problematic if left-handed and right-handed components had different gauge charges?

---

# PART III: GAUGE THEORIES

---

# Chapter 8: Abelian Gauge Symmetry and Quantum Electrodynamics

## Learning Objectives

After completing this chapter, the student will be able to:

1. Explain the gauge principle: how promoting a global symmetry to a local one requires introducing a gauge field.

2. Define the covariant derivative and its role.

3. Construct the QED Lagrangian from the gauge principle.

4. Understand the physical meaning of gauge invariance.

---

## 8.1 The Gauge Principle

In Chapter 4, we saw that the Dirac Lagrangian $\mathcal{L} = \bar{\psi}(i\slashed{\partial} - m)\psi$ is invariant under the **global** U(1) transformation:

$$\psi(x) \to e^{iq\alpha}\psi(x), \quad \bar{\psi}(x) \to \bar{\psi}(x)e^{-iq\alpha}$$

where $\alpha$ is a constant and $q$ is the charge of the fermion. The Noether current associated with this symmetry is the electromagnetic current.

Now we ask a seemingly innocent question: **what if we promote $\alpha$ to a function of spacetime, $\alpha(x)$?**

$$\psi(x) \to e^{iq\alpha(x)}\psi(x) \tag{8.1}$$

Is the Lagrangian still invariant?

The answer is **no**. The problem is with the derivative term:

$$\partial_\mu\psi(x) \to e^{iq\alpha(x)}\partial_\mu\psi(x) + iq(\partial_\mu\alpha(x))e^{iq\alpha(x)}\psi(x)$$

The derivative has produced an extra term $iq(\partial_\mu\alpha)\psi$ that spoils the invariance. This term arises because the derivative compares the field at two different points, which have undergone different transformations.

## 8.2 The Covariant Derivative

To fix this, we introduce a new field $A_\mu(x)$ — the **gauge field** — and define the **covariant derivative**:

$$D_\mu \equiv \partial_\mu - iqA_\mu(x) \tag{8.2}$$

We demand that $A_\mu$ transforms simultaneously as:

$$A_\mu(x) \to A_\mu(x) + \partial_\mu\alpha(x) \tag{8.3}$$

Then:

$$D_\mu\psi \to (\partial_\mu - iq(A_\mu + \partial_\mu\alpha))e^{iq\alpha}\psi = e^{iq\alpha}(\partial_\mu - iqA_\mu)\psi = e^{iq\alpha}D_\mu\psi$$

The covariant derivative of $\psi$ transforms the same way as $\psi$ itself. Therefore $\bar{\psi}(i\slashed{D} - m)\psi$ is gauge-invariant.

> **New abstraction:** The covariant derivative $D_\mu$ is a derivative that "knows about" the gauge transformation and compensates for the position-dependent phase. It ensures that differentiation and gauge transformation are compatible.

## 8.3 The QED Lagrangian

We must also add a kinetic term for the gauge field $A_\mu$. The field strength tensor:

$$F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu \tag{8.4}$$

is automatically gauge-invariant (verify: the $\partial_\mu\partial_\nu\alpha$ terms cancel due to the antisymmetry). The complete QED Lagrangian is:

$$\boxed{\mathcal{L}_{\text{QED}} = \bar{\psi}(i\slashed{D} - m)\psi - \frac{1}{4}F_{\mu\nu}F^{\mu\nu}} \tag{8.5}$$

Expanding $\slashed{D} = \gamma^\mu(\partial_\mu - iqA_\mu)$:

$$\mathcal{L}_{\text{QED}} = \bar{\psi}(i\slashed{\partial} - m)\psi - \frac{1}{4}F_{\mu\nu}F^{\mu\nu} + q\bar{\psi}\gamma^\mu\psi\, A_\mu$$

The three terms are:

1. **Free fermion:** $\bar{\psi}(i\slashed{\partial} - m)\psi$ — kinetic and mass terms for the electron.

2. **Free gauge field:** $-\frac{1}{4}F_{\mu\nu}F^{\mu\nu}$ — kinetic term for the photon.

3. **Interaction:** $q\bar{\psi}\gamma^\mu\psi\, A_\mu$ — the coupling between the electron and the photon.

The interaction term gives the QED vertex in Feynman diagrams: an electron emits or absorbs a photon with coupling strength $q$ (which we identify with $e$, the elementary charge).

## 8.4 The Photon Has No Mass

Notice that a mass term for $A_\mu$ would be $\frac{1}{2}m_A^2 A_\mu A^\mu$. But this is **not gauge-invariant** (since $A_\mu \to A_\mu + \partial_\mu\alpha$ under gauge transformation). Therefore, gauge invariance **forbids** a photon mass. This is why the photon is massless and the electromagnetic force is long-range.

This is a powerful consequence of gauge symmetry: it determines not only the form of the interactions but also constrains the particle masses.

## 8.5 Summary of the Gauge Principle

The logical chain is:

1. Start with a global symmetry of the matter Lagrangian.

2. Demand that this symmetry hold **locally** (at every spacetime point independently).

3. This fails unless we introduce a **gauge field** $A_\mu$ and replace $\partial_\mu \to D_\mu = \partial_\mu - iqA_\mu$.

4. The gauge field must transform as $A_\mu \to A_\mu + \partial_\mu\alpha$.

5. Add a kinetic term $-\frac{1}{4}F_{\mu\nu}F^{\mu\nu}$ for the gauge field.

6. The result: the gauge field mediates a force between charged particles.

**Forces arise from the requirement of local gauge invariance.** This is arguably the most beautiful and powerful principle in all of particle physics.

## 8.6 Gauge Invariance as Redundancy

It is important to understand that gauge symmetry is not a symmetry in the usual physical sense (like rotational symmetry). Rather, it represents a **redundancy in our description**: different values of $A_\mu$ related by gauge transformations describe the same physical situation. The "symmetry" is in the mathematical formulation, not in the physics.

This redundancy is the price we pay for a manifestly Lorentz-covariant description of massless spin-1 particles.

## Conceptual Summary

- Promoting a global U(1) symmetry to a local one requires introducing the gauge field $A_\mu$.

- The covariant derivative $D_\mu = \partial_\mu - iqA_\mu$ transforms covariantly: $D_\mu\psi \to e^{iq\alpha}D_\mu\psi$.

- The QED Lagrangian $\bar{\psi}(i\slashed{D}-m)\psi - \frac{1}{4}F^2$ is completely determined by the gauge principle.

- The interaction $q\bar{\psi}\gamma^\mu A_\mu\psi$ — the electromagnetic interaction — emerges automatically.

- Gauge invariance forbids a photon mass, explaining why electromagnetism is long-range.

- Gauge invariance represents a redundancy in the description, not a physical symmetry.

## Exercises

**Exercise 8.1.** Verify explicitly that $F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu$ is invariant under $A_\mu \to A_\mu + \partial_\mu\alpha$.

**Exercise 8.2.** Show that the mass term $\frac{1}{2}m^2 A_\mu A^\mu$ is not gauge-invariant. What would happen physically if the photon had a mass?

**Exercise 8.3.** Starting from the Lagrangian for a complex scalar field $\mathcal{L} = (\partial_\mu\phi)^*(\partial^\mu\phi) - m^2|\phi|^2$, implement the gauge principle: replace $\partial_\mu \to D_\mu = \partial_\mu - iqA_\mu$. Write out the resulting Lagrangian and identify the interaction terms. How many different types of vertices appear?

---

# Chapter 9: Lie Groups and Lie Algebras

## Learning Objectives

After completing this chapter, the student will be able to:

1. Define Lie groups and Lie algebras.

2. Understand generators, structure constants, and commutation relations.

3. Work with the specific groups U(1), SU(2), and SU(3).

4. Understand group representations.

5. Compute simple products of generators using structure constants.

---

## 9.1 Motivation

In Chapter 8, we used the group U(1) — complex phase rotations. This is the simplest example of a Lie group: it is continuous, one-dimensional, and **Abelian** (commutative: $e^{i\alpha}e^{i\beta} = e^{i\beta}e^{i\alpha}$).

The Standard Model requires **non-Abelian** (non-commutative) generalizations: SU(2) and SU(3). Before constructing non-Abelian gauge theories (Chapter 10), we need the mathematical language of Lie groups and Lie algebras.

## 9.2 Lie Groups

> **Definition 9.1 (Lie Group).** A Lie group is a group whose elements form a smooth manifold. In other words, its elements are labeled by continuous parameters, and the group operations (multiplication and inversion) are smooth functions of these parameters.

Examples relevant to us:

- **U(1):** $\{e^{i\alpha} : \alpha \in \mathbb{R}\}$. One parameter. Elements are $1\times 1$ unitary matrices (phases).

- **U(N):** $\{U \in \text{GL}(N,\mathbb{C}) : U^\dagger U = \mathbb{I}\}$. $N^2$ parameters. Unitary $N\times N$ matrices.

- **SU(N):** $\{U \in U(N) : \det U = 1\}$. $N^2 - 1$ parameters. Special unitary matrices.

- **SO(N):** $\{R \in \text{GL}(N,\mathbb{R}) : R^T R = \mathbb{I}, \det R = 1\}$. Real orthogonal matrices with unit determinant.

## 9.3 Lie Algebras and Generators

Any element of a Lie group continuously connected to the identity can be written as:

$$U = e^{i\alpha^a T^a} \tag{9.1}$$

where:

- $\alpha^a$ are real parameters ($a = 1, \ldots, \dim(\text{group})$)

- $T^a$ are called the **generators** of the group

- Summation over $a$ is implied (Einstein convention)

For **unitary** groups, the generators $T^a$ are **Hermitian matrices**: $(T^a)^\dagger = T^a$.

The generators satisfy commutation relations that define the **Lie algebra**:

$$[T^a, T^b] = if^{abc}T^c \tag{9.2}$$

The constants $f^{abc}$ are called the **structure constants** of the Lie algebra. They are:

- Real

- Totally antisymmetric: $f^{abc} = -f^{bac} = -f^{acb} = \ldots$

> **Definition 9.2 (Abelian vs. Non-Abelian).** A group is **Abelian** if all its elements commute (equivalently, $f^{abc} = 0$ for all $a,b,c$). It is **non-Abelian** if some elements do not commute ($f^{abc} \neq 0$ for some $a,b,c$).

U(1) is Abelian ($f^{abc} = 0$ trivially — there is only one generator). SU(2) and SU(3) are non-Abelian.

## 9.4 The Group SU(2)

$SU(2)$ is the group of $2\times 2$ unitary matrices with unit determinant. It has $2^2 - 1 = 3$ generators.

A convenient choice of generators is:

$$T^a = \frac{\sigma^a}{2}, \quad a = 1, 2, 3$$

where $\sigma^a$ are the **Pauli matrices** (which you know from QM I):

$$\sigma^1 = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad \sigma^2 = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad \sigma^3 = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$$

The commutation relations are:

$$[T^a, T^b] = i\epsilon^{abc}T^c$$

where $\epsilon^{abc}$ is the three-dimensional Levi-Civita symbol. So the structure constants of SU(2) are $f^{abc} = \epsilon^{abc}$.

You have already seen this algebra in QM I — it is the **angular momentum algebra** $[J_i, J_j] = i\epsilon_{ijk}J_k$.

## 9.5 The Group SU(3)

$SU(3)$ is the group of $3\times 3$ unitary matrices with unit determinant. It has $3^2 - 1 = 8$ generators.

A standard choice is the **Gell-Mann matrices** $\lambda^a$ ($a = 1, \ldots, 8$), with generators $T^a = \frac{\lambda^a}{2}$:

$$\lambda^1 = \begin{pmatrix} 0&1&0\\1&0&0\\0&0&0 \end{pmatrix}, \quad \lambda^2 = \begin{pmatrix} 0&-i&0\\i&0&0\\0&0&0 \end{pmatrix}, \quad \lambda^3 = \begin{pmatrix} 1&0&0\\0&-1&0\\0&0&0 \end{pmatrix}$$

$$\lambda^4 = \begin{pmatrix} 0&0&1\\0&0&0\\1&0&0 \end{pmatrix}, \quad \lambda^5 = \begin{pmatrix} 0&0&-i\\0&0&0\\i&0&0 \end{pmatrix}, \quad \lambda^6 = \begin{pmatrix} 0&0&0\\0&0&1\\0&1&0 \end{pmatrix}$$

$$\lambda^7 = \begin{pmatrix} 0&0&0\\0&0&-i\\0&i&0 \end{pmatrix}, \quad \lambda^8 = \frac{1}{\sqrt{3}}\begin{pmatrix} 1&0&0\\0&1&0\\0&0&-2 \end{pmatrix}$$

These satisfy $[T^a, T^b] = if^{abc}T^c$ where $f^{abc}$ are the SU(3) structure constants. Key nonzero values include $f^{123} = 1$, $f^{147} = f^{246} = f^{257} = f^{345} = 1/2$, $f^{156} = f^{367} = -1/2$, $f^{458} = f^{678} = \sqrt{3}/2$.

The important normalization convention is:

$$\text{Tr}(T^a T^b) = \frac{1}{2}\delta^{ab} \tag{9.3}$$

This holds for both SU(2) and SU(3) in the **fundamental representation**.

## 9.6 Representations

> **Definition 9.3 (Representation).** A representation of a Lie group $G$ is a homomorphism $\rho: G \to GL(V)$ mapping group elements to invertible linear transformations on a vector space $V$. Equivalently, it provides matrices for the generators that satisfy the same commutation relations as the abstract algebra.

The key representations we need:

### Fundamental Representation

- **SU(N):** The generators are $N \times N$ matrices acting on an $N$-component vector (column vector). This is the **smallest non-trivial representation** and is $N$-dimensional.

- For SU(3): the fundamental representation is **3-dimensional**. Quarks transform in this representation.

- For SU(2): the fundamental representation is **2-dimensional**. Left-handed fermions form doublets.

### Adjoint Representation

- **SU(N):** The generators are $(N^2-1) \times (N^2-1)$ matrices defined by $(T^a_{\text{adj}})_{bc} = -if^{abc}$. This representation has dimension $N^2 - 1$.

- For SU(3): the adjoint representation is **8-dimensional**. Gluons transform in this representation.

- For SU(2): the adjoint representation is **3-dimensional**. The W-bosons transform in this representation.

> **Physical significance:** The representation determines how a field transforms under the symmetry group. Quarks are in the fundamental 3 of SU(3); gluons are in the adjoint 8 of SU(3). The representation dictates the number of "colors" (or other gauge quantum numbers) a particle carries.

## 9.7 Casimir Operators and Group Constants

Two group-theoretic constants appear frequently:

The **quadratic Casimir** in representation $R$:

$$T^a_R T^a_R = C_R \cdot \mathbb{I}$$

For SU(N):

- Fundamental: $C_F = \frac{N^2-1}{2N}$

- Adjoint: $C_A = N$

For SU(3): $C_F = 4/3$, $C_A = 3$.

The **Dynkin index** $T_R$: $\text{Tr}(T^a_R T^b_R) = T_R \delta^{ab}$

For SU(N): $T_F = 1/2$ (fundamental), $T_A = N$ (adjoint).

## Conceptual Summary

- A Lie group is a continuous group; elements near the identity are generated by exponentiating generators: $U = e^{i\alpha^a T^a}$.

- Generators satisfy $[T^a, T^b] = if^{abc}T^c$, defining the Lie algebra.

- Structure constants $f^{abc}$ encode the non-commutativity of the group.

- $U(1)$ is Abelian ($f^{abc}=0$); $SU(2)$ and $SU(3)$ are non-Abelian.

- Representations specify how fields transform. Key ones: fundamental (quarks) and adjoint (gluons).

- $SU(2)$: 3 generators (Pauli matrices / 2). $SU(3)$: 8 generators (Gell-Mann matrices / 2).

## Exercises

**Exercise 9.1.** Verify that $[\sigma^1/2, \sigma^2/2] = i\sigma^3/2$ (i.e., the SU(2) structure constants are $f^{abc} = \epsilon^{abc}$).

**Exercise 9.2.** Show that the generators $T^a = \lambda^a/2$ of SU(3) are traceless (i.e., $\text{Tr}(T^a) = 0$). Why does the tracelessness condition correspond to the requirement $\det(e^{i\alpha^a T^a}) = 1$?

**Exercise 9.3.** The adjoint representation of SU(2) has generators $(T^a_{\text{adj}})_{bc} = -i\epsilon^{abc}$. Write these out as explicit $3 \times 3$ matrices for $a = 1,2,3$. Verify that they satisfy $[T^a_{\text{adj}}, T^b_{\text{adj}}] = i\epsilon^{abc}T^c_{\text{adj}}$.

---

# Chapter 10: Non-Abelian Gauge Theories (Yang-Mills Theory)

## Learning Objectives

After completing this chapter, the student will be able to:

1. Generalize the gauge principle from U(1) to SU(N).

2. Construct the non-Abelian covariant derivative.

3. Define the non-Abelian field strength tensor and understand its self-interaction terms.

4. Write the Yang-Mills Lagrangian.

5. Explain why non-Abelian gauge bosons carry charge and interact with each other.

---

## 10.1 From Abelian to Non-Abelian

In Chapter 8, we gauged U(1) and obtained QED. Now we gauge SU(N) and obtain **Yang-Mills theory** — the mathematical framework underlying both the strong and weak nuclear forces.

Consider $N$ fermion fields $\psi_i(x)$ ($i = 1, \ldots, N$) arranged into a column vector:

$$\Psi = \begin{pmatrix} \psi_1 \\ \vdots \\ \psi_N \end{pmatrix}$$

Under a **global** SU(N) transformation: $\Psi \to U\Psi$ where $U = e^{ig\alpha^a T^a}$ with constant parameters $\alpha^a$. The free Lagrangian $\bar{\Psi}(i\slashed{\partial} - m)\Psi$ is invariant.

Now **promote to local**: $\alpha^a \to \alpha^a(x)$, so $U = U(x)$.

## 10.2 The Non-Abelian Covariant Derivative

As in the Abelian case, $\partial_\mu\Psi$ does not transform covariantly. We introduce **gauge fields** $A_\mu^a(x)$ for each generator ($a = 1, \ldots, N^2-1$) and define the matrix-valued gauge field:

$$A_\mu(x) \equiv A_\mu^a(x) T^a \tag{10.1}$$

This is an $N \times N$ matrix at each spacetime point. The **covariant derivative** is:

$$D_\mu = \partial_\mu - igA_\mu = \partial_\mu - igA_\mu^a T^a \tag{10.2}$$

where $g$ is the gauge coupling constant.

The gauge field transforms as:

$$A_\mu \to UA_\mu U^\dagger + \frac{i}{g}U\partial_\mu U^\dagger \tag{10.3}$$

This ensures that $D_\mu\Psi \to U D_\mu\Psi$.

## 10.3 The Non-Abelian Field Strength Tensor

The field strength tensor is defined via:

$$[D_\mu, D_\nu] = -igF_{\mu\nu} \tag{10.4}$$

Computing explicitly:

$$F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu - ig[A_\mu, A_\nu] \tag{10.5}$$

In component form ($F_{\mu\nu} = F_{\mu\nu}^a T^a$):

$$F_{\mu\nu}^a = \partial_\mu A_\nu^a - \partial_\nu A_\mu^a + gf^{abc}A_\mu^b A_\nu^c \tag{10.6}$$

> **Critical difference from the Abelian case:** The last term $gf^{abc}A_\mu^b A_\nu^c$ is new! In U(1), $f^{abc} = 0$, so this term vanishes, and we recover $F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu$. In non-Abelian theories, the field strength itself depends on the gauge field nonlinearly.

This has a profound physical consequence: **non-Abelian gauge bosons carry charge and interact with each other.** Photons do not interact with other photons (at tree level), because the photon is uncharged. But gluons carry color charge and interact with other gluons.

## 10.4 The Yang-Mills Lagrangian

The complete Yang-Mills Lagrangian for a gauge field coupled to fermions is:

$$\boxed{\mathcal{L}_{\text{YM}} = -\frac{1}{2}\text{Tr}(F_{\mu\nu}F^{\mu\nu}) + \bar{\Psi}(i\slashed{D} - m)\Psi} \tag{10.7}$$

Using the normalization $\text{Tr}(T^aT^b) = \frac{1}{2}\delta^{ab}$:

$$-\frac{1}{2}\text{Tr}(F_{\mu\nu}F^{\mu\nu}) = -\frac{1}{4}F_{\mu\nu}^a F^{a\mu\nu}$$

Expanding the kinetic term $-\frac{1}{4}F_{\mu\nu}^a F^{a\mu\nu}$ using Eq. (10.6) reveals:

1. **Quadratic terms** $(\partial A)^2$: free propagation of gauge bosons.

2. **Cubic terms** $gf^{abc}(\partial A)AA$: **three-gluon vertex.**

3. **Quartic terms** $g^2 f^{abc}f^{ade}AAAA$: **four-gluon vertex.**

```

Three-gluon vertex: Four-gluon vertex:

╱ ╲ ╱

╱ ╳

╳ (∝ g) ╱ ╲ (∝ g²)

╱ ╲ ╱ ╲

```

These self-interactions are entirely absent in QED and are the hallmark of non-Abelian gauge theories.

## 10.5 Gauge Boson Mass

As in the Abelian case, a mass term $\frac{1}{2}m^2 A_\mu^a A^{a\mu}$ is **not gauge-invariant**. Therefore, non-Abelian gauge bosons are also massless — unless the gauge symmetry is spontaneously broken (Chapter 13).

In the Standard Model:

- Gluons (SU(3) gauge bosons) remain massless → QCD has unbroken SU(3) gauge symmetry.

- W and Z bosons (SU(2)×U(1) gauge bosons) acquire mass via the Higgs mechanism → electroweak symmetry is spontaneously broken.

## 10.6 Comparison: Abelian vs. Non-Abelian

| Feature | U(1) (QED) | SU(N) (Yang-Mills) |

|---|---|---|

| Gauge field | $A_\mu$ (1 field) | $A_\mu^a$ ($N^2-1$ fields) |

| Field strength | $\partial_\mu A_\nu - \partial_\nu A_\mu$ | $\partial_\mu A_\nu^a - \partial_\nu A_\mu^a + gf^{abc}A_\mu^b A_\nu^c$ |

| Self-interaction | No | Yes (3- and 4-point) |

| Gauge boson charge | Uncharged | Charged (carry adjoint color) |

| Coupling constant | $e$ | $g$ |

## Conceptual Summary

- Gauging SU(N) requires introducing $N^2-1$ gauge fields $A_\mu^a$.

- The covariant derivative is $D_\mu = \partial_\mu - igA_\mu^aT^a$.

- The field strength $F_{\mu\nu}^a$ contains a term $gf^{abc}A_\mu^bA_\nu^c$ that makes it non-linear in $A_\mu$.

- This non-linearity produces gauge boson self-interactions: 3-gluon and 4-gluon vertices.

- Non-Abelian gauge bosons carry charge (unlike the photon) and interact with each other.

- Gauge invariance forbids gauge boson masses.

## Exercises

**Exercise 10.1.** Starting from Eq. (10.5), derive the component form (10.6). *Hint:* write $A_\mu = A_\mu^a T^a$ and use $[T^a, T^b] = if^{abc}T^c$.

**Exercise 10.2.** In SU(2) Yang-Mills theory, how many gauge fields $A_\mu^a$ are there? In SU(3)? Relate these numbers to the dimension of the adjoint representation.

**Exercise 10.3.** Explain physically why gluons, which carry color charge, must interact with each other, while photons, which carry no electric charge, do not (at tree level). How is this related to the structure constants $f^{abc}$?

---

# PART IV: THE STANDARD MODEL

---

# Chapter 11: The Standard Model — Structure and Content

## Learning Objectives

After completing this chapter, the student will be able to:

1. State the gauge group of the Standard Model.

2. List all fermion fields and their gauge quantum numbers.

3. Understand how the gauge structure determines the interactions.

4. Describe the role of the Higgs field.

5. Write the general structure of the Standard Model Lagrangian.

---

## 11.1 The Gauge Group

The Standard Model (SM) of particle physics is a Yang-Mills gauge theory with gauge group:

$$\boxed{G_{\text{SM}} = SU(3)_C \times SU(2)_L \times U(1)_Y} \tag{11.1}$$

Each factor is associated with a different force:

| Group | Force | Gauge bosons | Number | Coupling |

|---|---|---|---|---|

| $SU(3)_C$ | Strong (color) | Gluons $G_\mu^a$ | 8 | $g_s$ |

| $SU(2)_L$ | Weak (left) | $W_\mu^a$ | 3 | $g$ |

| $U(1)_Y$ | Hypercharge | $B_\mu$ | 1 | $g'$ |

The subscripts denote:

- $C$ = "color" (the charge of the strong force)

- $L$ = "left" (couples only to left-handed fermions)

- $Y$ = "hypercharge" (related to, but not identical to, electric charge)

Total: $8 + 3 + 1 = 12$ gauge bosons.

## 11.2 The Fermion Content

The SM contains three **generations** of fermions, identical in their gauge quantum numbers but different in mass. We describe one generation; the others are copies.

### 11.2.1 Left-Handed Fermions

Left-handed fermions ($\psi_L = P_L \psi$) transform as **doublets** under $SU(2)_L$:

**Quarks:**

$$Q_L = \begin{pmatrix} u_L \\ d_L \end{pmatrix} \quad \text{transforms as } (\mathbf{3}, \mathbf{2}, +\tfrac{1}{6})$$

**Leptons:**

$$L_L = \begin{pmatrix} \nu_L \\ e_L \end{pmatrix} \quad \text{transforms as } (\mathbf{1}, \mathbf{2}, -\tfrac{1}{2})$$

The notation $(\mathbf{R}_3, \mathbf{R}_2, Y)$ denotes the representation under $SU(3)_C$, $SU(2)_L$, and the $U(1)_Y$ hypercharge.

- $\mathbf{3}$: fundamental (triplet) of SU(3) — quarks carry color.

- $\mathbf{1}$: singlet of SU(3) — leptons are colorless.

- $\mathbf{2}$: fundamental (doublet) of SU(2) — left-handed fields form weak doublets.

### 11.2.2 Right-Handed Fermions

Right-handed fermions ($\psi_R = P_R\psi$) are **singlets** under $SU(2)_L$:

$$u_R: (\mathbf{3}, \mathbf{1}, +\tfrac{2}{3}), \quad d_R: (\mathbf{3}, \mathbf{1}, -\tfrac{1}{3}), \quad e_R: (\mathbf{1}, \mathbf{1}, -1)$$

There is no right-handed neutrino in the minimal SM (this has implications for neutrino masses, which are observed but not part of the minimal SM).

### 11.2.3 Three Generations

The above pattern repeats three times:

| Generation | Quarks | Leptons |

|---|---|---|

| 1st | $(u, d)$ | $(\nu_e, e)$ |

| 2nd | $(c, s)$ | $(\nu_\mu, \mu)$ |

| 3rd | $(t, b)$ | $(\nu_\tau, \tau)$ |

All three generations have identical gauge quantum numbers; they differ only in their masses (determined by Yukawa couplings to the Higgs field).

## 11.3 The Higgs Field

The **Higgs field** $H$ is a complex scalar doublet under $SU(2)_L$:

$$H = \begin{pmatrix} H^+ \\ H^0 \end{pmatrix} \quad \text{transforms as } (\mathbf{1}, \mathbf{2}, +\tfrac{1}{2}) \tag{11.2}$$

Its role is to **break the electroweak symmetry spontaneously** (Chapter 13). Without it, all SM particles would be massless.

## 11.4 The SM Lagrangian: Structure

The full SM Lagrangian has four main parts:

$$\mathcal{L}_{\text{SM}} = \mathcal{L}_{\text{gauge}} + \mathcal{L}_{\text{fermion}} + \mathcal{L}_{\text{Higgs}} + \mathcal{L}_{\text{Yukawa}} \tag{11.3}$$

### 11.4.1 Gauge Sector

$$\mathcal{L}_{\text{gauge}} = -\frac{1}{4}G_{\mu\nu}^a G^{a\mu\nu} - \frac{1}{4}W_{\mu\nu}^a W^{a\mu\nu} - \frac{1}{4}B_{\mu\nu}B^{\mu\nu} \tag{11.4}$$

where:

- $G_{\mu\nu}^a = \partial_\mu G_\nu^a - \partial_\nu G_\mu^a + g_s f^{abc}G_\mu^b G_\nu^c$ is the **gluon field strength** ($a = 1, \ldots, 8$)

- $W_{\mu\nu}^a = \partial_\mu W_\nu^a - \partial_\nu W_\mu^a + g\epsilon^{abc}W_\mu^b W_\nu^c$ is the **SU(2) field strength** ($a = 1, 2, 3$)

- $B_{\mu\nu} = \partial_\mu B_\nu - \partial_\nu B_\mu$ is the **U(1) field strength** (Abelian, no self-interaction)

### 11.4.2 Fermion Sector

$$\mathcal{L}_{\text{fermion}} = \sum_{\text{fermions}} \bar{\Psi}\, i\slashed{D}\, \Psi \tag{11.5}$$

where the covariant derivative for each fermion depends on its gauge quantum numbers. For example, for the left-handed quark doublet:

$$D_\mu Q_L = \left(\partial_\mu - ig_s G_\mu^a T^a_s - ig W_\mu^a T^a_w - ig'Y B_\mu\right) Q_L$$

where $T^a_s = \lambda^a/2$ are SU(3) generators, $T^a_w = \sigma^a/2$ are SU(2) generators, and $Y$ is the hypercharge.

Note: **no explicit mass terms for fermions appear here.** Writing $m\bar{\psi}\psi = m(\bar{\psi}_L\psi_R + \bar{\psi}_R\psi_L)$ would require coupling left-handed and right-handed components, which have different SU(2) quantum numbers. Such a term is not gauge-invariant. Fermion masses arise from the Yukawa interactions after electroweak symmetry breaking.

### 11.4.3 Higgs Sector

$$\mathcal{L}_{\text{Higgs}} = (D_\mu H)^\dagger(D^\mu H) - V(H) \tag{11.6}$$

with the Higgs potential:

$$V(H) = -\mu^2 H^\dagger H + \lambda(H^\dagger H)^2 \tag{11.7}$$

The negative $\mu^2$ term drives spontaneous symmetry breaking (Chapter 13).

### 11.4.4 Yukawa Sector

$$\mathcal{L}_{\text{Yukawa}} = -y_u \bar{Q}_L \tilde{H} u_R - y_d \bar{Q}_L H d_R - y_e \bar{L}_L H e_R + \text{h.c.} \tag{11.8}$$

where $\tilde{H} = i\sigma^2 H^*$ and "h.c." means Hermitian conjugate. The Yukawa couplings $y_f$ are free parameters that determine fermion masses after the Higgs acquires a vacuum expectation value.

## 11.5 Electric Charge

The electric charge is not a fundamental quantum number of the SM gauge group. It is a combination:

$$Q_{\text{em}} = T^3_w + Y \tag{11.9}$$

where $T^3_w$ is the third component of weak isospin. For instance:

- $u_L$: $T^3 = +1/2$, $Y = 1/6$, so $Q = 1/2 + 1/6 = 2/3$. ✓

- $d_L$: $T^3 = -1/2$, $Y = 1/6$, so $Q = -1/2 + 1/6 = -1/3$. ✓

- $e_L$: $T^3 = -1/2$, $Y = -1/2$, so $Q = -1/2 - 1/2 = -1$. ✓

## 11.6 Counting Parameters

The Standard Model has 19 free parameters (in the minimal version):

- 3 gauge couplings ($g_s$, $g$, $g'$)

- 6 quark masses (from Yukawa couplings)

- 3 charged lepton masses

- 2 Higgs parameters ($\mu$, $\lambda$)

- 4 CKM matrix parameters (quark mixing)

- 1 QCD vacuum angle ($\theta_{\text{QCD}}$)

All are determined by experiment, not by the theory.

## Conceptual Summary

- The SM is a gauge theory with group $SU(3)_C \times SU(2)_L \times U(1)_Y$.

- Fermions come in three generations of quarks and leptons.

- Left-handed fermions transform as doublets under $SU(2)_L$; right-handed as singlets.

- The SM Lagrangian consists of gauge, fermion, Higgs, and Yukawa sectors.

- All interactions are determined by the gauge principle and the particle content.

- Fermion masses are forbidden by gauge symmetry and arise only through the Higgs mechanism.

- Electric charge is $Q = T^3 + Y$.

## Exercises

**Exercise 11.1.** Verify that the hypercharge assignments are consistent with $Q = T^3 + Y$ for all right-handed fermions: $u_R$, $d_R$, $e_R$.

**Exercise 11.2.** Why can't we write a bare mass term $m_e\bar{e}_Le_R$ in the SM Lagrangian? What are the $SU(2)_L$ quantum numbers of $e_L$ vs $e_R$?

**Exercise 11.3.** Count the total number of gauge bosons in the Standard Model before and after electroweak symmetry breaking (where $W^\pm$, $Z^0$, and $\gamma$ emerge from the four electroweak gauge fields).

---

# Chapter 12: Quantum Chromodynamics

## Learning Objectives

After completing this chapter, the student will be able to:

1. Describe QCD as the SU(3) Yang-Mills theory of the strong force.

2. Explain color charge and the eight gluons.

3. Understand confinement and asymptotic freedom qualitatively.

4. Recognize the role of the gluon field strength tensor $G_{\mu\nu}^a$ and its properties.

5. Understand the QCD Lagrangian in detail.

---

## 12.1 QCD: The Theory of the Strong Force

**Quantum Chromodynamics (QCD)** is the sector of the Standard Model described by the gauge group $SU(3)_C$. It governs the strong nuclear force — the force that binds quarks into protons, neutrons, and other hadrons, and that binds protons and neutrons into atomic nuclei.

## 12.2 Color Charge

Quarks carry a quantum number called **color** (by analogy with optical colors — this has nothing to do with actual color). Each quark comes in three colors:

$$q = \begin{pmatrix} q_r \\ q_g \\ q_b \end{pmatrix} \tag{12.1}$$

where $r, g, b$ stand for "red," "green," "blue." This is the **fundamental representation** of SU(3): a three-component vector on which the $3\times 3$ matrices $T^a = \lambda^a/2$ act.

Antiquarks carry anticolor: $\bar{r}, \bar{g}, \bar{b}$ and transform in the conjugate fundamental representation $\bar{\mathbf{3}}$.

## 12.3 The Eight Gluons

$SU(3)$ has $3^2 - 1 = 8$ generators, so there are **eight gluon fields** $G_\mu^a$ ($a = 1, \ldots, 8$). Each gluon carries one color and one anticolor (in the adjoint representation).

This is the key difference from QED: **gluons carry color charge**. They interact with each other through three-gluon and four-gluon vertices, as discussed in Chapter 10.

## 12.4 The QCD Lagrangian

$$\boxed{\mathcal{L}_{\text{QCD}} = -\frac{1}{4}G_{\mu\nu}^a G^{a\mu\nu} + \sum_{f=1}^{n_f}\bar{q}_f(i\slashed{D} - m_f)q_f} \tag{12.2}$$

where:

- The **gluon field strength tensor** is:

$$G_{\mu\nu}^a = \partial_\mu G_\nu^a - \partial_\nu G_\mu^a + g_s f^{abc} G_\mu^b G_\nu^c \tag{12.3}$$

- The **covariant derivative** acting on quarks is:

$$D_\mu = \partial_\mu - ig_s G_\mu^a T^a \tag{12.4}$$

- The sum is over $n_f$ quark flavors ($u, d, s, c, b, t$).

- $f^{abc}$ are the SU(3) structure constants.

- $g_s$ is the strong coupling constant. One often writes $\alpha_s = g_s^2/(4\pi)$.

## 12.5 Gluon Self-Interactions

Expanding $-\frac{1}{4}G_{\mu\nu}^a G^{a\mu\nu}$ using (12.3):

$$-\frac{1}{4}G_{\mu\nu}^a G^{a\mu\nu} = -\frac{1}{4}(\partial_\mu G_\nu^a - \partial_\nu G_\mu^a)^2 - g_s f^{abc}(\partial_\mu G_\nu^a)G^{b\mu}G^{c\nu} - \frac{1}{4}g_s^2 f^{abc}f^{ade}G_\mu^b G_\nu^c G^{d\mu}G^{e\nu}$$

This contains:

1. **Free gluon propagation**: $(\partial G)^2$ terms.

2. **Three-gluon vertex**: proportional to $g_s$.

3. **Four-gluon vertex**: proportional to $g_s^2$.

These self-interactions are responsible for the dramatically different behavior of QCD compared to QED.

## 12.6 The Dual Field Strength Tensor

For later use (SMEFT operators), we define the **dual field strength tensor**:

$$\tilde{G}_{\mu\nu}^a = \frac{1}{2}\epsilon_{\mu\nu\rho\sigma}G^{a\rho\sigma} \tag{12.5}$$

where $\epsilon_{\mu\nu\rho\sigma}$ is the four-dimensional Levi-Civita symbol with $\epsilon_{0123} = +1$. The dual tensor exchanges "electric" and "magnetic" components of the gauge field.

An important identity: $G_{\mu\nu}^a \tilde{G}^{a\mu\nu}$ is a total derivative and is related to the topological structure of QCD (the $\theta$-term). While it plays a role in the strong CP problem, we note it here because operators involving $\tilde{G}$ appear in the SMEFT.

## 12.7 Confinement

A remarkable property of QCD is **confinement**: isolated quarks and gluons have never been observed. They are always confined inside color-neutral (color-singlet) bound states called **hadrons**.

There are two types of hadrons:

- **Mesons**: quark-antiquark pairs ($q\bar{q}$) — color + anticolor = colorless.

- **Baryons**: three quarks ($qqq$) — one of each color ($rgb$) = colorless.

Confinement arises because the QCD coupling constant $\alpha_s$ grows at low energies/large distances (opposite to QED), making the force between quarks stronger as they are pulled apart. It is as if the quarks are connected by a string of constant tension — eventually, pulling creates new quark-antiquark pairs rather than isolating a quark.

## 12.8 Asymptotic Freedom

At high energies/short distances, the QCD coupling $\alpha_s$ **decreases** — quarks behave almost as free particles. This property is called **asymptotic freedom** and was discovered by Gross, Wilczek, and Politzer in 1973 (Nobel Prize 2004).

We will derive the running of $\alpha_s$ in Chapter 15. The qualitative origin of asymptotic freedom is the gluon self-interaction: virtual gluon loops **anti-screen** color charge, weakening the effective coupling at short distances. This is opposite to QED, where virtual electron-positron pairs screen electric charge.

## 12.9 The Gluon Field Strength as a Matrix

It is often useful to write the field strength as an $SU(3)$ matrix:

$$G_{\mu\nu} \equiv G_{\mu\nu}^a T^a \tag{12.6}$$

Then:

$$G_{\mu\nu} = \partial_\mu G_\nu - \partial_\nu G_\mu - ig_s[G_\mu, G_\nu] \tag{12.7}$$

where $G_\mu \equiv G_\mu^a T^a$. The gauge-kinetic term becomes:

$$-\frac{1}{4}G_{\mu\nu}^a G^{a\mu\nu} = -\frac{1}{2}\text{Tr}(G_{\mu\nu}G^{\mu\nu}) \tag{12.8}$$

This matrix notation will be essential for writing SMEFT operators compactly.

## Conceptual Summary

- QCD is the $SU(3)_C$ Yang-Mills theory describing quarks and gluons.

- Quarks carry color charge (fundamental representation of SU(3)); gluons carry color-anticolor (adjoint representation).

- There are 8 gluons that interact with each other through 3- and 4-gluon vertices.

- Confinement: quarks and gluons are always bound into color-singlet hadrons.

- Asymptotic freedom: $\alpha_s$ decreases at high energies, making perturbation theory valid.

- The gluon field strength tensor $G_{\mu\nu}^a$ and its matrix form $G_{\mu\nu} = G_{\mu\nu}^aT^a$ are fundamental objects.

## Exercises

**Exercise 12.1.** Why does QED not exhibit confinement? Relate your answer to the Abelian nature of U(1) and the absence of photon self-interactions.

**Exercise 12.2.** Show that a baryon (three quarks, one of each color) is a color singlet. *Hint:* the color state is $\epsilon^{ijk} q_i q_j q_k$, which is invariant under SU(3) transformations.

**Exercise 12.3.** In QCD, how many interaction vertices exist (classify by the number of lines meeting at a vertex)? For each, state whether it involves quarks, gluons, or both, and give the power of $g_s$ associated with it.

---

# Chapter 13: Spontaneous Symmetry Breaking and the Higgs Mechanism

## Learning Objectives

After completing this chapter, the student will be able to:

1. Define spontaneous symmetry breaking.

2. State Goldstone's theorem and its implications.

3. Explain the Higgs mechanism: how gauge bosons acquire mass.

4. Understand the electroweak symmetry breaking pattern.

5. Know how fermion masses arise from Yukawa couplings.

---

## 13.1 Spontaneous Symmetry Breaking: The Concept

> **Definition 13.1 (Spontaneous Symmetry Breaking, SSB).** A symmetry is spontaneously broken if the Lagrangian is invariant under the symmetry, but the ground state (vacuum) is not.

The symmetry is not actually removed — it is "hidden." The Lagrangian still respects the symmetry, but the vacuum state "chooses" a particular direction, breaking the symmetry spontaneously.

### 13.1.1 Classical Analogy: The Mexican Hat

Consider a potential for a complex scalar field:

$$V(\phi) = -\mu^2|\phi|^2 + \lambda|\phi|^4, \quad \mu^2 > 0, \lambda > 0 \tag{13.1}$$

This potential has the shape of a "Mexican hat" (sombrero): the maximum is at $\phi = 0$, and the minimum forms a circle at:

$$|\phi_0| = \frac{\mu}{\sqrt{2\lambda}} \equiv \frac{v}{\sqrt{2}} \tag{13.2}$$

where $v = \mu/\sqrt{\lambda}$ is the **vacuum expectation value (VEV)**.

The potential is symmetric under $\phi \to e^{i\alpha}\phi$ (U(1) rotations), but the vacuum state $\phi_0 = \frac{v}{\sqrt{2}}$ is not — it picks out a specific phase. The symmetry is spontaneously broken.

## 13.2 Goldstone's Theorem

> **Theorem 13.1 (Goldstone's Theorem).** When a continuous global symmetry is spontaneously broken, there appears a massless scalar particle (a **Goldstone boson**) for each broken generator.

Expanding $\phi(x)$ around the vacuum:

$$\phi(x) = \frac{1}{\sqrt{2}}\left(v + h(x) + i\xi(x)\right)$$

where $h(x)$ is a massive field (the "Higgs" mode, excitations along the radial direction) and $\xi(x)$ is a massless field (the Goldstone boson, excitations along the circle of minima — the "flat" direction).

## 13.3 The Higgs Mechanism

Now comes the brilliant part. When the broken symmetry is a **local (gauge) symmetry**, the Goldstone bosons do not appear as physical particles. Instead, they are "eaten" by the gauge bosons, which acquire mass. This is the **Higgs mechanism** (Englert, Brout, Higgs, 1964).

### 13.3.1 How It Works (Abelian Example)

Consider the U(1) gauge theory with a complex scalar:

$$\mathcal{L} = (D_\mu\phi)^*(D^\mu\phi) - V(\phi) - \frac{1}{4}F_{\mu\nu}F^{\mu\nu}$$

with $D_\mu = \partial_\mu - iqA_\mu$ and $V(\phi) = -\mu^2|\phi|^2 + \lambda|\phi|^4$.

After SSB, expanding around $\phi_0 = v/\sqrt{2}$, the kinetic term $(D_\mu\phi)^*(D^\mu\phi)$ produces:

$$\frac{1}{2}q^2v^2 A_\mu A^\mu$$

This is a **mass term** for the gauge field! The gauge boson has acquired mass $m_A = qv$.

The Goldstone boson $\xi(x)$ has been "gauged away" — it becomes the longitudinal polarization of the massive gauge boson. A massless spin-1 particle has 2 polarizations; a massive one has 3. The missing degree of freedom comes from the Goldstone boson.

### 13.3.2 Counting Degrees of Freedom

| Before SSB | After SSB |

|---|---|

| Complex scalar: 2 d.o.f. | Massive Higgs $h$: 1 d.o.f. |

| Massless gauge boson: 2 d.o.f. | Massive gauge boson: 3 d.o.f. |

| **Total: 4 d.o.f.** | **Total: 4 d.o.f.** |

The total number of degrees of freedom is conserved, as it must be.

## 13.4 Electroweak Symmetry Breaking

In the Standard Model, the Higgs field is an SU(2) doublet (Eq. 11.2). The potential is:

$$V(H) = -\mu^2 H^\dagger H + \lambda(H^\dagger H)^2$$

The Higgs develops a VEV:

$$\langle H \rangle = \frac{1}{\sqrt{2}}\begin{pmatrix} 0 \\ v \end{pmatrix} \tag{13.3}$$

where $v \approx 246$ GeV.

The symmetry breaking pattern is:

$$SU(2)_L \times U(1)_Y \xrightarrow{\text{SSB}} U(1)_{\text{em}} \tag{13.4}$$

Four generators are broken... wait: $SU(2)_L$ has 3 generators, $U(1)_Y$ has 1, total = 4. After breaking, $U(1)_{\text{em}}$ has 1 generator. So $4 - 1 = 3$ generators are broken, producing 3 Goldstone bosons. These are eaten by 3 gauge bosons, giving mass to:

- $W^+ = \frac{1}{\sqrt{2}}(W^1 - iW^2)$: mass $m_W = gv/2 \approx 80.4$ GeV

- $W^- = \frac{1}{\sqrt{2}}(W^1 + iW^2)$: mass $m_{W^-} = m_{W^+}$

- $Z^0$: a mixture of $W^3$ and $B$, mass $m_Z = v\sqrt{g^2 + g'^2}/2 \approx 91.2$ GeV

The remaining orthogonal combination is the **photon** $\gamma$: massless, corresponding to the unbroken $U(1)_{\text{em}}$.

The physical Higgs boson $h$ (the radial mode) has mass $m_h = \sqrt{2\mu^2} \approx 125$ GeV (discovered at CERN in 2012).

## 13.5 Fermion Masses

The Yukawa interaction (Eq. 11.8) generates fermion masses after SSB. For example, for the electron:

$$-y_e\bar{L}_L H e_R \xrightarrow{\langle H\rangle \neq 0} -\frac{y_e v}{\sqrt{2}}\bar{e}_L e_R$$

This is a mass term with $m_e = y_e v/\sqrt{2}$. Each fermion mass is proportional to its Yukawa coupling and to the Higgs VEV.

## Conceptual Summary

- SSB occurs when the Lagrangian has a symmetry but the vacuum does not.

- Goldstone's theorem: broken global symmetries produce massless Goldstone bosons.

- Higgs mechanism: in a gauge theory, Goldstone bosons are "eaten" by gauge bosons, giving them mass.

- In the SM: $SU(2)_L \times U(1)_Y \to U(1)_{\text{em}}$, giving masses to $W^\pm$ and $Z^0$, while $\gamma$ remains massless.

- Fermion masses arise from Yukawa couplings to the Higgs field.

- The Higgs boson $h$ with mass ~125 GeV is the observable remnant of the mechanism.

## Exercises

**Exercise 13.1.** For the Mexican hat potential $V = -\mu^2|\phi|^2 + \lambda|\phi|^4$, find the minimum and compute the mass of the radial excitation $h$.

**Exercise 13.2.** Explain in words why a massless spin-1 particle has 2 degrees of freedom (2 transverse polarizations) while a massive spin-1 particle has 3 (2 transverse + 1 longitudinal). Why does the Goldstone boson provide the extra degree of freedom?

**Exercise 13.3.** The top quark has mass $m_t \approx 173$ GeV and $v \approx 246$ GeV. What is the top quark Yukawa coupling $y_t$? Why is it much larger than the electron Yukawa coupling? Is there a theoretical explanation?

---

# PART V: QUANTUM CORRECTIONS

---

# Chapter 14: Renormalization

## Learning Objectives

After completing this chapter, the student will be able to:

1. Explain why loop diagrams produce divergent integrals.

2. Understand the concept of regularization.

3. Explain renormalization conceptually and technically.

4. Distinguish between renormalizable and non-renormalizable theories.

5. Understand the concept of a renormalization scale.

---

## 14.1 The Problem of Infinities

In Chapter 6, we noted that loop diagrams involve integrals over all possible loop momenta. Consider the simplest loop correction to the propagator in $\phi^4$ theory:

$$\int \frac{d^4k}{(2\pi)^4}\frac{i}{k^2 - m^2 + i\epsilon} \tag{14.1}$$

This integral diverges: the integrand goes as $1/k^2$ for large $k$, and $\int d^4k/k^2$ diverges as $k^2$ for large momentum. This is an **ultraviolet (UV) divergence** — it comes from very high momenta (short distances).

When QFT was first developed, these infinities were a crisis. They appear to render the theory meaningless. The resolution is **renormalization**.

## 14.2 Regularization

Before dealing with infinities, we must first make them mathematically well-defined. **Regularization** is a procedure that temporarily renders the divergent integrals finite.

### 14.2.1 Cutoff Regularization

The simplest approach: integrate only up to some maximum momentum $\Lambda$ (the **cutoff**):

$$\int^{\Lambda} \frac{d^4k}{(2\pi)^4}\frac{1}{k^2 - m^2}$$

The result now depends on $\Lambda$ and diverges as $\Lambda \to \infty$.

### 14.2.2 Dimensional Regularization

A more sophisticated method (and the standard one in modern calculations): perform the integral in $d = 4 - 2\epsilon$ spacetime dimensions, where $\epsilon$ is a small parameter. Divergences appear as poles $1/\epsilon$ instead of as powers of $\Lambda$.

$$\int \frac{d^dk}{(2\pi)^d}\frac{1}{(k^2 - m^2)^n} = \text{function with poles at } \epsilon = 0$$

In dimensional regularization, one also introduces a **renormalization scale** $\mu$ with dimensions of energy, to keep coupling constants dimensionless. This scale will play a crucial role in the renormalization group (Chapter 15).

## 14.3 The Key Idea of Renormalization

The central insight of renormalization is:

> **The divergences can be absorbed into redefinitions of the parameters (masses, coupling constants, field normalizations) that appear in the Lagrangian.**

The "bare" parameters in the Lagrangian — the ones we originally wrote down — are not the physical, measured quantities. They are infinite (or cutoff-dependent), but so are the loop corrections. The combination — bare parameter + loop correction — yields a finite, physical result.

### 14.3.1 Renormalization of Mass

The physical mass $m_{\text{phys}}$ is not the bare mass $m_0$ appearing in $\mathcal{L}$. Including loop corrections:

$$m_{\text{phys}}^2 = m_0^2 + \delta m^2(\Lambda)$$

where $\delta m^2(\Lambda)$ diverges as $\Lambda \to \infty$. We choose $m_0^2$ to also depend on $\Lambda$ in precisely the way that makes $m_{\text{phys}}^2$ finite and equal to the measured value.

### 14.3.2 Renormalization of Coupling Constants

Similarly, the physical coupling $\lambda_{\text{phys}}$ differs from the bare coupling $\lambda_0$:

$$\lambda_{\text{phys}} = \lambda_0 + \delta\lambda(\Lambda)$$

Again, $\delta\lambda$ diverges, but $\lambda_0(\Lambda)$ is chosen to cancel the divergence.

### 14.3.3 Field Renormalization

The field itself must be rescaled: $\phi = Z^{1/2}\phi_R$, where $\phi_R$ is the renormalized field and $Z$ absorbs divergences from the field propagator.

## 14.4 Counterterms

In practice, one writes the Lagrangian as:

$$\mathcal{L} = \mathcal{L}_{\text{renormalized}} + \mathcal{L}_{\text{counterterms}}$$

The counterterms have the same form as the original terms in $\mathcal{L}$ but with coefficients chosen order by order in perturbation theory to cancel the divergences.

For $\phi^4$ theory:

$$\mathcal{L}_{\text{ct}} = \frac{1}{2}\delta Z(\partial_\mu\phi)^2 - \frac{1}{2}\delta m^2\phi^2 - \frac{\delta\lambda}{4!}\phi^4$$

where $\delta Z$, $\delta m^2$, $\delta\lambda$ contain divergent pieces that cancel the loop divergences.

## 14.5 Renormalizability

> **Definition 14.1 (Renormalizability).** A theory is renormalizable if all UV divergences that appear at any order in perturbation theory can be absorbed by a finite number of counterterms — specifically, by redefining only the parameters already present in the original Lagrangian.

Renormalizable theories have the remarkable property that once a finite number of parameters are fixed by experiment, all predictions are finite.

**Not all theories are renormalizable.** Whether a theory is renormalizable depends on the **mass dimensions** of its coupling constants. We need the concept of mass dimension:

In natural units ($\hbar = c = 1$), the action $S = \int d^4x\,\mathcal{L}$ is dimensionless. Since $[d^4x] = [\text{energy}]^{-4}$, we need $[\mathcal{L}] = [\text{energy}]^4$, i.e., mass dimension 4.

From the kinetic term $\frac{1}{2}(\partial_\mu\phi)^2$: $[\partial_\mu] = 1$ (energy), so $[\phi] = 1$.

For fermions: $[\psi] = 3/2$ (from $\bar\psi i\slashed{\partial}\psi$).

For gauge fields: $[A_\mu] = 1$ (from $(\partial A)^2$).

Now consider an interaction term with coupling $g$ and operator $\mathcal{O}$ of dimension $d$: $\mathcal{L}_{\text{int}} = g\mathcal{O}$. Since $[\mathcal{L}] = 4$, we need $[g] = 4 - d$.

| $[g]$ | Type | Example | Status |

|---|---|---|---|

| $[g] > 0$ | Super-renormalizable | $\phi^3$ ($g$ has dim 1) | Finitely many divergences |

| $[g] = 0$ | Renormalizable | $\phi^4$, QED, QCD | Infinitely many divergences but absorbable |

| $[g] < 0$ | Non-renormalizable | $\phi^6$ ($g$ has dim $-2$) | New divergences at each loop order |

**The Standard Model is a renormalizable theory.** All interaction terms have couplings with non-negative mass dimension.

## 14.6 What About Non-Renormalizable Theories?

Non-renormalizable theories are not useless — they are **effective field theories**, valid below some energy scale $\Lambda$. This is the key insight that leads to EFT (Chapter 16).

## 14.7 The Physical Picture

Renormalization reflects a deep physical fact: physical observables at a given energy scale are influenced by quantum fluctuations at all higher scales. Renormalization separates the physics at different scales in a consistent way.

The measured value of a coupling constant depends on the energy scale at which you measure it. This leads directly to the concept of **running couplings** (next chapter).

## Conceptual Summary

- Loop diagrams in QFT produce UV divergences.

- Regularization makes divergences mathematically tractable (cutoff or dimensional regularization).

- Renormalization absorbs divergences into redefinitions of bare parameters (mass, coupling, field normalization).

- A theory is renormalizable if only finitely many types of counterterms are needed.

- The mass dimension of coupling constants determines renormalizability: $[g] \geq 0$ → renormalizable.

- The Standard Model is renormalizable. Non-renormalizable theories become effective field theories.

## Exercises

**Exercise 14.1.** Compute the mass dimension of the coupling constant $g$ in the interaction $g\phi^6$ in $d=4$ dimensions. Is this interaction renormalizable?

**Exercise 14.2.** In QED, the interaction term is $e\bar{\psi}\gamma^\mu A_\mu\psi$. Compute $[\bar{\psi}\gamma^\mu A_\mu\psi]$ and verify that $[e] = 0$, confirming QED is renormalizable.

**Exercise 14.3.** Explain in your own words why the need for infinitely many counterterms in a non-renormalizable theory destroys its predictive power at high energies but not at low energies.

---

# Chapter 15: The Renormalization Group and Running Couplings

## Learning Objectives

After completing this chapter, the student will be able to:

1. Explain the concept of the renormalization scale $\mu$.

2. Define the beta function $\beta(g)$ and the anomalous dimension.

3. Solve the renormalization group equation for the running coupling.

4. Understand asymptotic freedom in QCD quantitatively.

5. Compute the one-loop running of $\alpha_s$ at a conceptual level.

---

## 15.1 The Renormalization Scale

When we renormalize a theory using dimensional regularization, we must introduce an arbitrary energy scale $\mu$ (the renormalization scale). Physical observables cannot depend on our arbitrary choice of $\mu$. This requirement leads to the **renormalization group equations (RGEs)**.

## 15.2 The Beta Function

The **running coupling** $g(\mu)$ is the coupling constant measured at energy scale $\mu$. Its dependence on $\mu$ is governed by the **beta function**:

$$\beta(g) \equiv \mu \frac{dg}{d\mu} \tag{15.1}$$

If $\beta > 0$, the coupling increases with energy (QED-like behavior).

If $\beta < 0$, the coupling decreases with energy (asymptotically free).

Often it is more convenient to write:

$$\mu\frac{d\alpha}{d\mu} = \beta(\alpha), \quad \alpha \equiv \frac{g^2}{4\pi}$$

## 15.3 One-Loop Beta Function of QCD

The one-loop beta function for the QCD coupling $\alpha_s = g_s^2/(4\pi)$ is:

$$\beta(\alpha_s) = -\frac{\alpha_s^2}{2\pi}\left(\frac{11}{3}C_A - \frac{4}{3}T_F n_f\right) \tag{15.2}$$

For SU(3): $C_A = 3$, $T_F = 1/2$, and $n_f$ is the number of active quark flavors. At one loop:

$$\beta_0 = \frac{11}{3}\cdot 3 - \frac{4}{3}\cdot\frac{1}{2}\cdot n_f = 11 - \frac{2n_f}{3}$$

For $n_f \leq 16$, $\beta_0 > 0$, giving $\beta(\alpha_s) < 0$. With $n_f = 6$ (all quarks), $\beta_0 = 7$. **QCD is asymptotically free.**

The two contributions have clear physical origins:

- The $\frac{11}{3}C_A$ term comes from **gluon self-interactions** (non-Abelian contribution). This is negative in $\beta(\alpha_s)$ and drives asymptotic freedom.

- The $-\frac{4}{3}T_F n_f$ term comes from **quark loops** and has the opposite sign (screening, like QED). But for $n_f \leq 16$, the gluon contribution dominates.

## 15.4 The Running Coupling

The RGE $\mu\frac{d\alpha_s}{d\mu} = -\frac{\beta_0}{2\pi}\alpha_s^2$ can be solved:

$$\alpha_s(\mu) = \frac{\alpha_s(\mu_0)}{1 + \frac{\beta_0}{2\pi}\alpha_s(\mu_0)\ln\frac{\mu}{\mu_0}} \tag{15.3}$$

Equivalently, introducing the **QCD scale** $\Lambda_{\text{QCD}} \approx 200$ MeV:

$$\alpha_s(\mu) = \frac{2\pi}{\beta_0\ln(\mu/\Lambda_{\text{QCD}})} \tag{15.4}$$

Key features:

- At $\mu \gg \Lambda_{\text{QCD}}$: $\alpha_s$ is small → perturbation theory works.

- At $\mu \sim \Lambda_{\text{QCD}}$: $\alpha_s$ becomes large → perturbation theory breaks down → confinement.

- At $\mu = \Lambda_{\text{QCD}}$: $\alpha_s$ formally diverges (the **Landau pole**) — signaling the onset of nonperturbative physics.

Experimental values: $\alpha_s(m_Z) \approx 0.118$ at $\mu = m_Z \approx 91.2$ GeV.

## 15.5 Visualization

```

α_s(μ)

│

│\

│ \

│ \

│ \__

│ \___

│ \________

└───────────────────── μ

Λ_QCD m_Z

(~200 MeV) (~91 GeV)

α_s large α_s ≈ 0.12

(confinement) (perturbative)

```

## 15.6 Anomalous Dimensions and Operator Running

Not only do coupling constants run — **operators** and their Wilson coefficients also run. If $\mathcal{O}$ is a composite operator and $C(\mu)$ its Wilson coefficient, then:

$$\mu\frac{dC}{d\mu} = \gamma_{\mathcal{O}}\, C \tag{15.5}$$

where $\gamma_{\mathcal{O}}$ is the **anomalous dimension** of $\mathcal{O}$.

This will be crucial for SMEFT: the Wilson coefficients of dimension-6 operators run with the energy scale, and we need RGEs to relate their values at different scales.

More generally, when there are multiple operators that mix under renormalization, we have:

$$\mu\frac{dC_i}{d\mu} = \gamma_{ij}C_j \tag{15.6}$$

where $\gamma_{ij}$ is the **anomalous dimension matrix**. Operator mixing is a key feature of SMEFT.

## 15.7 The Renormalization Group in Other Sectors

The SM has three gauge coupling constants, all of which run:

- $\alpha_1(\mu) = \frac{5}{3}\frac{g'^2}{4\pi}$: increases with $\mu$ (U(1) — no self-interactions).

- $\alpha_2(\mu) = \frac{g^2}{4\pi}$: decreases with $\mu$ (SU(2) — asymptotically free).

- $\alpha_3(\mu) = \frac{g_s^2}{4\pi}$: decreases with $\mu$ (SU(3) — asymptotically free).

The remarkable observation that these three couplings approximately converge to a single value at $\mu \sim 10^{16}$ GeV is suggestive of **grand unification** — though this is beyond our scope.

## Conceptual Summary

- Physical coupling constants depend on the energy scale at which they are measured: they "run."

- The beta function $\beta(g) = \mu\frac{dg}{d\mu}$ governs this running.

- QCD is asymptotically free: $\alpha_s$ decreases at high energy. This is driven by gluon self-interactions.

- At low energies, $\alpha_s$ grows large, leading to confinement.

- Not only couplings, but also Wilson coefficients and operators, run via anomalous dimensions.

- The anomalous dimension matrix describes operator mixing under renormalization.

## Exercises

**Exercise 15.1.** Verify that for $n_f = 6$, $\beta_0 = 7 > 0$, confirming asymptotic freedom. For how many flavors would asymptotic freedom be lost?

**Exercise 15.2.** Using $\alpha_s(m_Z) = 0.118$ and $\beta_0 = 7$ (6 flavors), estimate $\alpha_s$ at $\mu = 1$ TeV using the one-loop formula. Is perturbation theory reliable at this scale?

**Exercise 15.3.** In QED, the one-loop beta function is $\beta(\alpha) = +\frac{2\alpha^2}{3\pi}n_f$ (where $n_f$ counts charged fermion species). Explain why the sign is opposite to QCD and what this means physically for the running of $\alpha_{\text{em}}$.

---

# PART VI: EFFECTIVE FIELD THEORY AND SMEFT

---

# Chapter 16: Effective Field Theory

## Learning Objectives

After completing this chapter, the student will be able to:

1. Explain the philosophy of Effective Field Theory (EFT).

2. Understand the concepts of UV and IR physics, and scale separation.

3. Define operator dimension and power counting.

4. Understand the meaning of higher-dimensional operators.

5. Explain decoupling and matching.

6. Write a general EFT Lagrangian organized by operator dimension.

---

## 16.1 A Philosophical Shift

So far, we have treated the Standard Model as a **fundamental** theory — a Lagrangian valid at all energy scales. But this is an unrealistic expectation. We know there must be physics beyond the SM (dark matter, neutrino masses, gravity, ...), and that physics at very high energies is unknown to us.

**Effective Field Theory** takes a different, more mature, philosophical stance:

> *A theory need not be valid at all energies to be useful and predictive. A theory valid up to some energy scale $\Lambda$ is perfectly good for describing physics at energies $E \ll \Lambda$.*

This is not a sign of weakness but of wisdom. All physical theories are effective theories valid within some domain.

## 16.2 The EFT Framework

### 16.2.1 The Setup

Suppose there is "new physics" — heavy particles with mass $M \gg E$, where $E$ is the energy scale of our experiments. At energies $E \ll M$, these heavy particles cannot be produced on-shell (as real particles). But they still affect low-energy physics through **virtual effects** — they can appear in loops or be exchanged as virtual particles.

The key insight of EFT is: at low energies, the effects of heavy particles can be systematically captured by adding **higher-dimensional operators** to the low-energy Lagrangian.

### 16.2.2 The General EFT Lagrangian

$$\mathcal{L}_{\text{EFT}} = \mathcal{L}_{\text{SM}} + \sum_{d>4}\sum_i \frac{C_i^{(d)}}{\Lambda^{d-4}}\mathcal{O}_i^{(d)} \tag{16.1}$$

where:

- $\mathcal{L}_{\text{SM}}$ is the dimension-$\leq 4$ Standard Model Lagrangian (renormalizable part).

- $\mathcal{O}_i^{(d)}$ are **local operators** of mass dimension $d > 4$, built from SM fields and their derivatives.

- $C_i^{(d)}$ are dimensionless **Wilson coefficients** that encode the effects of the heavy particles.

- $\Lambda$ is the **new physics scale** — roughly the mass of the heavy particles that have been integrated out.

## 16.3 Operator Dimension and Power Counting

### 16.3.1 Mass Dimensions of Fields and Derivatives

Recall from Chapter 14:

| Object | Mass dimension |

|---|---|

| Scalar field $\phi$ | 1 |

| Fermion field $\psi$ | 3/2 |

| Gauge field $A_\mu$ | 1 |

| Field strength $F_{\mu\nu}$ | 2 |

| Derivative $\partial_\mu$ | 1 |

| Coupling constants (SM) | 0 |

### 16.3.2 Why Dimension 4 Is Special

The Lagrangian density has $[\mathcal{L}] = 4$. Operators of dimension $d$ require a coefficient with dimension $4-d$:

- $d = 4$: dimensionless coupling → renormalizable. These are the SM interactions.

- $d = 5$: coefficient has dimension $-1$, i.e., $C/\Lambda$. Suppressed by one power of $\Lambda$.

- $d = 6$: coefficient has dimension $-2$, i.e., $C/\Lambda^2$. Suppressed by $\Lambda^2$.

- $d > 6$: even more suppressed.

The effects of higher-dimensional operators are suppressed by powers of $(E/\Lambda)^{d-4}$. For $E \ll \Lambda$, higher-dimension operators give smaller and smaller corrections. This is the basis of **power counting** in EFT.

### 16.3.3 The EFT Expansion

At low energies $E \ll \Lambda$:

$$\mathcal{L}_{\text{EFT}} \approx \mathcal{L}_{\text{SM}} + \frac{1}{\Lambda}\sum_i C_i^{(5)}\mathcal{O}_i^{(5)} + \frac{1}{\Lambda^2}\sum_i C_i^{(6)}\mathcal{O}_i^{(6)} + \mathcal{O}\left(\frac{1}{\Lambda^3}\right)$$

This is a systematic expansion in powers of $1/\Lambda$ (or equivalently, $E/\Lambda$).

## 16.4 Decoupling and Matching

### 16.4.1 Decoupling

The **decoupling theorem** (Appelquist-Carazzone) states that heavy particles of mass $M$ contribute to low-energy observables only through terms suppressed by powers of $1/M$. In the limit $M \to \infty$, they completely decouple.

This justifies the EFT approach: at energies well below $M$, we can remove the heavy particle from the theory and capture its effects through local operators.

### 16.4.2 Matching

**Matching** is the procedure of determining the Wilson coefficients $C_i$ by requiring that the full theory (with the heavy particle) and the EFT (without it) give the same results for low-energy observables.

Schematically:

1. In the **full theory** (UV theory), compute a scattering amplitude at energies $E \ll M$.

2. In the **EFT**, compute the same amplitude using the operators $\mathcal{O}_i^{(d)}/\Lambda^{d-4}$.

3. Equate the two results to determine $C_i$.

The matching is typically done at the scale $\mu = M$ (the mass of the heavy particle being integrated out). Below this scale, the Wilson coefficients run according to the RGEs (Chapter 15).

### 16.4.3 A Concrete Example: Fermi Theory

The most famous example of an EFT is **Fermi's theory of weak interactions**. In the full SM, the weak interaction is mediated by the exchange of a $W$ boson:

```

νₑ ───╳~~~~W~~~~╳─── e⁻

│ │

└── e⁺ ────── ν̄_μ

```

At energies $E \ll m_W \approx 80$ GeV, the $W$ propagator $\frac{1}{q^2 - m_W^2} \approx \frac{-1}{m_W^2}$ can be approximated as a constant (the $W$ is too heavy to resolve). The diagram collapses to a point:

```

νₑ ───╳─── e⁻

│

└── e⁺ ── ν̄_μ

```

This is a four-fermion contact interaction, described by the dimension-6 operator:

$$\mathcal{L}_{\text{Fermi}} = -\frac{G_F}{\sqrt{2}}(\bar{\nu}_e\gamma^\mu P_L e)(\bar{\mu}\gamma_\mu P_L \nu_\mu) + \text{h.c.}$$

where $G_F/\sqrt{2} = g^2/(8m_W^2) = C/(m_W)^2$ is the Fermi constant. This is a dimension-6 operator with Wilson coefficient $C \sim g^2$ divided by $\Lambda^2 = m_W^2$.

Fermi's theory is an EFT of the electroweak sector, valid for energies $E \ll m_W$.

## 16.5 Why EFT Is Powerful

1. **Model independence:** The EFT parametrizes all possible effects of unknown heavy physics in a systematic way. We don't need to know the specific UV theory — only the symmetries of the low-energy theory.

2. **Predictive power:** At a given order in $1/\Lambda$, only a finite number of operators contribute. Measuring their Wilson coefficients gives predictions for all processes.

3. **Systematic improvability:** Including higher-dimensional operators improves accuracy systematically.

4. **Renormalizability is not required:** The EFT is non-renormalizable, but this is fine — new divergences at each order in $1/\Lambda$ are absorbed by the operators already present at that order.

## 16.6 The EFT Paradigm

The modern view in particle physics:

> **The Standard Model itself is an EFT** — the leading-order (dimension-4) part of a more general effective Lagrangian. Dimension-5 and dimension-6 operators encode the leading effects of whatever lies beyond the SM.

This paradigm is the foundation of the Standard Model Effective Field Theory (SMEFT), which we develop in the next two chapters.

## Conceptual Summary

- EFT is a framework for describing physics at energies $E \ll \Lambda$, where $\Lambda$ is the scale of heavy new physics.

- The EFT Lagrangian is the SM Lagrangian plus higher-dimensional operators suppressed by powers of $1/\Lambda$.

- Operator dimension determines the suppression: dimension-$d$ operators are suppressed by $\Lambda^{4-d}$.

- Matching determines Wilson coefficients by equating UV and EFT predictions at the scale $\Lambda$.

- Below $\Lambda$, Wilson coefficients run according to RGEs.

- Fermi theory is the classic example: a dimension-6 four-fermion operator from integrating out the $W$ boson.

- The SM itself is best viewed as the leading-order part of an EFT.

## Exercises

**Exercise 16.1.** An operator $\mathcal{O}$ has mass dimension 8. At what order in $1/\Lambda$ does it first contribute? If $E = 1$ TeV and $\Lambda = 10$ TeV, estimate the relative suppression $(E/\Lambda)^{d-4}$ compared to a dimension-4 SM operator.

**Exercise 16.2.** In Fermi theory, the Wilson coefficient is $G_F/\sqrt{2} = g^2/(8m_W^2)$. Verify the mass dimensions: $G_F$ should have dimension $-2$. What are the dimensions of $g$ and $m_W$?

**Exercise 16.3.** Explain why a non-renormalizable theory is acceptable as an EFT but problematic as a fundamental theory. What changes when we view it as valid only below a cutoff $\Lambda$?

---

# Chapter 17: The Standard Model Effective Field Theory (SMEFT)

## Learning Objectives

After completing this chapter, the student will be able to:

1. Define SMEFT and state its assumptions.

2. Understand the operator expansion in SMEFT.

3. Know why dimension 5 gives the unique Weinberg operator.

4. Understand the dimension-6 operator basis (Warsaw basis).

5. Classify dimension-6 operators by type.

6. Understand Wilson coefficients and their physical interpretation.

7. Explain operator mixing and running in the SMEFT context.

---

## 17.1 Definition of SMEFT

> **Definition 17.1 (SMEFT).** The Standard Model Effective Field Theory is the most general effective field theory built from Standard Model fields, respecting the gauge symmetry $SU(3)_C \times SU(2)_L \times U(1)_Y$, organized as an expansion in operator dimension.

$$\boxed{\mathcal{L}_{\text{SMEFT}} = \mathcal{L}_{\text{SM}} + \sum_i \frac{C_i^{(5)}}{\Lambda}\mathcal{O}_i^{(5)} + \sum_i \frac{C_i^{(6)}}{\Lambda^2}\mathcal{O}_i^{(6)} + \mathcal{O}\left(\frac{1}{\Lambda^3}\right)} \tag{17.1}$$

### Assumptions of SMEFT:

1. **The SM gauge symmetry is linearly realized.** The Higgs doublet $H$ is present as an elementary field in the EFT. (An alternative framework, HEFT — Higgs EFT — relaxes this assumption.)

2. **No new light particles.** The only light degrees of freedom are the SM fields. All new particles are heavy, with masses $\sim \Lambda$.

3. **Baryon and lepton number may or may not be conserved** (depending on which operators are included).

## 17.2 Dimension 5: The Weinberg Operator

At dimension 5, there is only one operator (up to flavor structure):

$$\mathcal{O}^{(5)} = \epsilon^{ij}\epsilon^{kl}(L_i^T C L_k)(H_j H_l) \tag{17.2}$$

This is the **Weinberg operator** (Weinberg, 1979). Here $C$ is the charge conjugation matrix, and $i,j,k,l$ are SU(2) indices.

After electroweak symmetry breaking, this operator generates:

$$\mathcal{O}^{(5)} \to \frac{v^2}{\Lambda}\nu_L^T C\nu_L = \frac{v^2}{\Lambda}m_\nu \bar{\nu}\nu$$

This is a **Majorana mass term for neutrinos**! It violates lepton number by two units ($\Delta L = 2$) and is the simplest explanation for why neutrinos have tiny masses: $m_\nu \sim v^2/\Lambda$. For $\Lambda \sim 10^{14}$ GeV and $v \sim 246$ GeV, we get $m_\nu \sim 0.1$ eV — in agreement with neutrino oscillation data.

## 17.3 Dimension 6: The Core of SMEFT Phenomenology

At dimension 6, the number of independent operators is much larger. This is where the bulk of SMEFT phenomenology lies, because:

1. Dimension-5 operators violate lepton number and are relevant mainly for neutrino physics.

2. Dimension-6 operators conserve baryon and lepton number (the most important ones) and contribute to a vast range of collider observables.

3. Dimension-7 and higher are further suppressed by additional powers of $1/\Lambda$.

### 17.3.1 How Many Operators?

The complete, non-redundant set of dimension-6 operators built from SM fields was classified by Buchmuller and Wyler (1986) and corrected/completed into the **Warsaw basis** by Grzadkowski, Iskrzyński, Misiak, and Rosiek (2010).

For one generation of fermions: **59 independent operators** (plus Hermitian conjugates for complex operators, totaling 76 operator structures).

Including all three generations with general flavor structure, the number of free parameters grows to **2499**.

### 17.3.2 The Warsaw Basis

The Warsaw basis organizes the 59 operators into eight classes:

| Class | Description | Schematic form | # |

|---|---|---|---|

| 1 | $X^3$ | Three field strengths | 4 |

| 2 | $H^6$ | Six Higgs fields | 1 |

| 3 | $H^4 D^2$ | Four Higgs + two derivatives | 2 |

| 4 | $X^2 H^2$ | Two field strengths + two Higgs | 8 |

| 5 | $\psi^2 H^3$ | Two fermions + three Higgs | 3 |

| 6 | $\psi^2 X H$ | Two fermions + field strength + Higgs | 8 |

| 7 | $\psi^2 H^2 D$ | Two fermions + two Higgs + derivative | 8 |

| 8 | $\psi^4$ | Four fermions | 25 |

Here $X$ denotes a gauge field strength ($G_{\mu\nu}$, $W_{\mu\nu}$, or $B_{\mu\nu}$), $H$ is the Higgs doublet, $D$ is the covariant derivative, and $\psi$ denotes a fermion field. Let us describe each class.

## 17.4 Operator Classes in Detail

### 17.4.1 Class 1: $X^3$ — Pure Gauge Operators

These operators involve three field strength tensors:

$$\mathcal{O}_G = f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu} \tag{17.3}$$

$$\mathcal{O}_{\tilde{G}} = f^{abc}\tilde{G}_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu} \tag{17.4}$$

$$\mathcal{O}_W = \epsilon^{abc}W_\mu^{a\nu}W_\nu^{b\rho}W_\rho^{c\mu} \tag{17.5}$$

$$\mathcal{O}_{\tilde{W}} = \epsilon^{abc}\tilde{W}_\mu^{a\nu}W_\nu^{b\rho}W_\rho^{c\mu} \tag{17.6}$$

There is no corresponding $B^3$ operator because $U(1)$ is Abelian ($f^{abc} = 0$).

The operator $\mathcal{O}_G$ is of central importance and will be discussed in detail in Chapter 18.

Note the notation: $G_\mu^{a\nu} \equiv \eta^{\nu\rho}G_{\mu\rho}^a$ is the field strength tensor with one index raised using the metric. The contraction pattern $G_\mu^{\ \nu} G_\nu^{\ \rho} G_\rho^{\ \mu}$ forms a "chain" of three field strength tensors.

### 17.4.2 Class 2: $H^6$

$$\mathcal{O}_H = (H^\dagger H)^3 \tag{17.7}$$

This modifies the Higgs self-coupling and the shape of the Higgs potential.

### 17.4.3 Class 3: $H^4 D^2$

$$\mathcal{O}_{H\Box} = (H^\dagger H)\Box(H^\dagger H) \tag{17.8}$$

$$\mathcal{O}_{HD} = (H^\dagger D_\mu H)^*(H^\dagger D^\mu H) \tag{17.9}$$

These modify the Higgs kinetic term and the relation between electroweak precision observables.

### 17.4.4 Class 4: $X^2 H^2$

Examples:

$$\mathcal{O}_{HG} = H^\dagger H\, G_{\mu\nu}^a G^{a\mu\nu} \tag{17.10}$$

$$\mathcal{O}_{H\tilde{G}} = H^\dagger H\, \tilde{G}_{\mu\nu}^a G^{a\mu\nu} \tag{17.11}$$

$$\mathcal{O}_{HW} = H^\dagger H\, W_{\mu\nu}^a W^{a\mu\nu} \tag{17.12}$$

$$\mathcal{O}_{HB} = H^\dagger H\, B_{\mu\nu}B^{\mu\nu} \tag{17.13}$$

$$\mathcal{O}_{HWB} = H^\dagger \sigma^a H\, W_{\mu\nu}^a B^{\mu\nu} \tag{17.14}$$

These operators modify the couplings of the Higgs to gauge bosons. $\mathcal{O}_{HG}$ modifies the Higgs coupling to gluons — crucial for Higgs production via gluon fusion at the LHC.

### 17.4.5 Class 5: $\psi^2 H^3$ (Yukawa-like)

$$\mathcal{O}_{uH} = (H^\dagger H)(\bar{Q}_L \tilde{H} u_R) \tag{17.15}$$

These modify the Yukawa couplings (and hence fermion masses) of the SM.

### 17.4.6 Class 6: $\psi^2 X H$ (Dipole operators)

$$\mathcal{O}_{uG} = (\bar{Q}_L \sigma^{\mu\nu} T^a u_R)\tilde{H}\, G_{\mu\nu}^a \tag{17.16}$$

$$\mathcal{O}_{uW} = (\bar{Q}_L \sigma^{\mu\nu} \sigma^a u_R)\tilde{H}\, W_{\mu\nu}^a \tag{17.17}$$

$$\mathcal{O}_{uB} = (\bar{Q}_L \sigma^{\mu\nu} u_R)\tilde{H}\, B_{\mu\nu} \tag{17.18}$$

These are the **chromomagnetic** and **electromagnetic dipole** operators. They generate anomalous magnetic moments and chromoelectric dipole moments for fermions.

### 17.4.7 Class 7: $\psi^2 H^2 D$

$$\mathcal{O}_{Hq}^{(1)} = (H^\dagger i\overset{\leftrightarrow}{D}_\mu H)(\bar{Q}_L \gamma^\mu Q_L) \tag{17.19}$$

These modify the couplings of fermions to gauge bosons.

### 17.4.8 Class 8: $\psi^4$ (Four-Fermion Operators)

$$\mathcal{O}_{qq}^{(1)} = (\bar{Q}_L\gamma^\mu Q_L)(\bar{Q}_L\gamma_\mu Q_L) \tag{17.20}$$

These describe direct four-fermion contact interactions, generalizing Fermi's theory.

## 17.5 Wilson Coefficients: Physical Meaning

Each Wilson coefficient $C_i/\Lambda^2$ parametrizes the strength of a particular type of new physics effect:

- **If $C_i = 0$**: the operator plays no role; the SM prediction is recovered.

- **If $C_i \neq 0$**: there is a deviation from the SM, potentially observable at colliders.

The Wilson coefficients are **a priori free parameters** in the EFT. Their values depend on the (unknown) UV completion — the specific model of new physics at scale $\Lambda$.

However:

- If we **know** the UV model, we can compute the $C_i$ by matching (Section 16.4).

- If we **don't know** the UV model, we can **measure** the $C_i$ from data and use them to constrain or identify the new physics.

This model-independent approach is one of the greatest strengths of SMEFT.

## 17.6 Operator Mixing and Running in SMEFT

As discussed in Section 15.6, Wilson coefficients run with the energy scale:

$$\mu\frac{dC_i}{d\mu} = \frac{1}{16\pi^2}\gamma_{ij}C_j + \mathcal{O}\left(\frac{1}{(16\pi^2)^2}\right) \tag{17.21}$$

The **anomalous dimension matrix** $\gamma_{ij}$ describes how operators mix under renormalization. This mixing is extensive in SMEFT: an operator generated at the high scale $\Lambda$ can induce other operators at lower scales through RG evolution.

The full one-loop anomalous dimension matrix for the dimension-6 SMEFT was computed by several groups (Alonso, Jenkins, Manohar, Trott, 2013-2014). It is a large matrix ($59 \times 59$ for one generation, much larger with flavor), but its structure reflects the gauge symmetry and has calculable, predictable features.

## 17.7 Equations of Motion and Operator Redundancy

Not all operators one can write down are independent. The **equations of motion (EOM)** can be used to eliminate redundant operators. For example, if $\phi$ satisfies $\Box\phi + m^2\phi = \cdots$, then $\Box\phi$ can be replaced by lower-order terms.

The Warsaw basis is defined precisely as the **non-redundant** set after all EOM relations, integration by parts, and Fierz identities have been used to eliminate dependent operators.

When using EOM to reduce operators, the resulting Wilson coefficients in the Warsaw basis encode the physics of both the original operator and its EOM-equivalent forms.

## 17.8 Notation Conventions

Some notation that appears in the thesis:

- $\overset{\leftrightarrow}{D}_\mu$: the Hermitian derivative, $H^\dagger \overset{\leftrightarrow}{D}_\mu H = H^\dagger D_\mu H - (D_\mu H)^\dagger H$.

- $\tilde{H} = i\sigma^2 H^*$: the conjugate Higgs doublet.

- $\sigma^{\mu\nu} = \frac{i}{2}[\gamma^\mu, \gamma^\nu]$: appears in dipole operators.

- Flavor indices are often suppressed; each operator implicitly carries flavor indices ($pr$, $prst$, etc.) when multiple generations are included.

## Conceptual Summary

- SMEFT is the most general EFT built from SM fields respecting the SM gauge symmetry.

- At dimension 5, there is a unique operator (Weinberg), generating neutrino masses.

- At dimension 6, there are 59 independent operators (Warsaw basis), classified into 8 types.

- Wilson coefficients $C_i/\Lambda^2$ parametrize deviations from the SM.

- Operators mix and run under the RGE, governed by the anomalous dimension matrix.

- The Warsaw basis is non-redundant after using EOM and integration by parts.

- SMEFT provides a model-independent framework for parametrizing and searching for new physics.

## Exercises

**Exercise 17.1.** Verify the mass dimension of the operator $\mathcal{O}_G = f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu}$. What are the dimensions of $G_{\mu\nu}^a$, $f^{abc}$, and the overall operator?

**Exercise 17.2.** Why is there no $B^3$ operator (three $U(1)_Y$ field strengths)? What mathematical property of $U(1)$ makes such an operator vanish?

**Exercise 17.3.** The Fermi constant $G_F \approx 1.166 \times 10^{-5}$ GeV$^{-2}$. Interpreting this as $C/\Lambda^2$ with $C \sim \mathcal{O}(1)$, estimate the scale $\Lambda$. Compare with $m_W \approx 80$ GeV.

---

# Chapter 18: The $O_G$ Operator — Structure, Meaning, and Phenomenology

## Learning Objectives

After completing this chapter, the student will be able to:

1. Write down the explicit form of the $O_G$ operator.

2. Explain its physical meaning: a triple gluon field strength interaction.

3. Understand why it has no analogue in the Abelian theory.

4. Describe its effects on physical observables.

5. Understand its renormalization group running and mixing with other operators.

6. Appreciate its role in constraining new physics at the LHC.

---

## 18.1 The Definition of $O_G$

The operator $O_G$ (also written as $\mathcal{O}_G$ or $\mathcal{O}_{3G}$) is the **CP-even triple gluon field strength operator** of mass dimension 6:

$$\boxed{O_G = f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu}} \tag{18.1}$$

Let us carefully unpack every piece:

- $G_{\mu\nu}^a$ is the **gluon field strength tensor** (Eq. 12.3), with color index $a = 1, \ldots, 8$ and Lorentz indices $\mu, \nu = 0, 1, 2, 3$.

- $G_\mu^{a\nu} = \eta^{\nu\rho}G_{\mu\rho}^a$ is the field strength with one index raised.

- $f^{abc}$ are the **SU(3) structure constants**, totally antisymmetric.

- The Lorentz index structure forms a chain: $\mu \to \nu \to \rho \to \mu$, creating a **trace over Lorentz indices**.

In matrix notation (using $G_{\mu\nu} = G_{\mu\nu}^a T^a$):

$$O_G = \text{Tr}(G_\mu^{\ \nu}G_\nu^{\ \rho}G_\rho^{\ \mu}) \tag{18.2}$$

(up to a normalization factor, using $f^{abc} = -2i\,\text{Tr}([T^a,T^b]T^c)$).

### 18.1.1 Verification of Mass Dimension

Each field strength tensor has mass dimension $[G_{\mu\nu}] = 2$ (since it contains one derivative of a dimension-1 field). The operator contains three field strengths: $[O_G] = 3 \times 2 = 6$. ✓

### 18.1.2 Verification of Gauge Invariance

Under an SU(3) gauge transformation, $G_{\mu\nu} \to UG_{\mu\nu}U^\dagger$ (the field strength in the adjoint representation). Therefore:

$$\text{Tr}(G_\mu^{\ \nu}G_\nu^{\ \rho}G_\rho^{\ \mu}) \to \text{Tr}(UG_\mu^{\ \nu}U^\dagger UG_\nu^{\ \rho}U^\dagger UG_\rho^{\ \mu}U^\dagger) = \text{Tr}(G_\mu^{\ \nu}G_\nu^{\ \rho}G_\rho^{\ \mu})$$

The invariance follows from the cyclicity of the trace and $U^\dagger U = \mathbb{I}$. ✓

### 18.1.3 CP Properties

Under charge conjugation and parity (CP), the gluon field strength transforms as:

$$G_{\mu\nu}^a \xrightarrow{CP} -G_{\mu\nu}^a$$

(the minus sign comes from the combination of charge conjugation and parity on gauge fields). Therefore:

$$O_G = f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu} \xrightarrow{CP} f^{abc}(-G_\mu^{a\nu})(-G_\nu^{b\rho})(-G_\rho^{c\mu}) = -O_G$$

Wait — three minus signs give an overall minus. But $O_G$ is defined to be **CP-even** in many references. Let us be careful.

Actually, the CP property depends on the convention. Under parity alone, $G_{0i} \to -G_{0i}$ and $G_{ij} \to G_{ij}$. The full analysis shows that $O_G$ is **CP-odd**. Its CP-even counterpart would use the dual field strength $\tilde{G}$.

More precisely:

- $O_G = f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu}$: **CP-odd** (contains an odd number of "chromoelectric" components)

- $O_{\tilde{G}} = f^{abc}\tilde{G}_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu}$: **CP-even**

The conventions vary in the literature. In some references the labels are swapped. What matters physically is: one of the pair $(O_G, O_{\tilde{G}})$ violates CP and the other preserves it. The thesis should specify which convention it uses.

## 18.2 Why $O_G$ Has No Abelian Analogue

Consider trying to construct a $B^3$ operator (using the U(1) field strength):

$$B_\mu^{\ \nu}B_\nu^{\ \rho}B_\rho^{\ \mu}$$

For an Abelian theory, there are no structure constants $f^{abc}$ (or equivalently, there is only one generator). But more fundamentally, $B_{\mu\nu}$ is gauge-invariant by itself (unlike the non-Abelian case), and one can check that $B_\mu^{\ \nu}B_\nu^{\ \rho}B_\rho^{\ \mu}$ is related to $(B_{\mu\nu}B^{\mu\nu})B_\rho^{\ \sigma}B_\sigma^{\ \rho}$-type structures that can be shown to vanish identically or reduce to other forms by the antisymmetry of $B_{\mu\nu}$.

In fact, for a single Abelian field strength, $\text{Tr}(F^3) = F_\mu^{\ \nu}F_\nu^{\ \rho}F_\rho^{\ \mu}$ vanishes identically in $d=4$ dimensions. This is because $F_{\mu\nu}$ is an antisymmetric $4\times 4$ matrix, and the trace of an odd power of an antisymmetric matrix vanishes.

Thus, the $X^3$ class of operators exists **only for non-Abelian gauge groups**: $SU(3)_C$ produces $O_G$ and $O_{\tilde{G}}$; $SU(2)_L$ produces $O_W$ and $O_{\tilde{W}}$.

## 18.3 The $O_G$ Operator in the SMEFT Lagrangian

In the full SMEFT Lagrangian, the $O_G$ contribution is:

$$\mathcal{L} \supset \frac{C_G}{\Lambda^2}O_G = \frac{C_G}{\Lambda^2}f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu} \tag{18.3}$$

where $C_G$ is the Wilson coefficient — a dimensionless number that parametrizes the strength of this interaction.

## 18.4 Physical Effects of $O_G$

### 18.4.1 Modified Multi-Gluon Vertices

The operator $O_G$ generates new three-gluon vertices beyond those present in QCD. In the SM, the three-gluon vertex comes from the Yang-Mills Lagrangian and has a specific momentum dependence. The $O_G$ operator modifies this vertex by adding terms with a different Lorentz structure (more powers of momenta, since $O_G$ contains three field strengths, each with one derivative).

Additionally, $O_G$ generates new **four-gluon**, **five-gluon**, and **six-gluon** contact vertices that are absent in the SM. This is because expanding $G_{\mu\nu}^a = \partial_\mu G_\nu^a - \partial_\nu G_\mu^a + g_s f^{abc}G_\mu^b G_\nu^c$, each field strength contains terms linear and quadratic in $G_\mu^a$. Substituting into $O_G = f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu}$:

- Three $G_{\mu\nu}$ each contributing $\partial G$: gives a **three-gluon vertex** with three momenta.

- Two $\partial G$ and one $gfGG$: gives a **four-gluon vertex**.

- One $\partial G$ and two $gfGG$: gives a **five-gluon vertex**.

- Three $gfGG$: gives a **six-gluon vertex**.

These vertices are suppressed by $1/\Lambda^2$ but can produce observable effects at high-energy colliders.

### 18.4.2 Multi-Jet Production

At the LHC, the $O_G$ operator contributes to multi-jet production processes:

$$pp \to \text{jets}$$

The new vertices change the angular distributions and cross sections for multi-jet events. Comparing LHC data with SM+SMEFT predictions constrains $C_G/\Lambda^2$.

### 18.4.3 Higgs Production (Indirect)

While $O_G$ does not directly involve the Higgs field, it can contribute indirectly to Higgs physics through operator mixing: under RG evolution, $O_G$ can mix with operators that do involve the Higgs (like $O_{HG} = H^\dagger H\, G_{\mu\nu}^aG^{a\mu\nu}$), which affects Higgs production via gluon fusion.

## 18.5 Renormalization Group Properties of $O_G$

### 18.5.1 Self-Renormalization

The one-loop anomalous dimension of $O_G$ is:

$$\mu\frac{dC_G}{d\mu} = \frac{1}{16\pi^2}\gamma_G C_G + \text{mixing terms} \tag{18.4}$$

The self-anomalous dimension $\gamma_G$ has been computed:

$$\gamma_G = g_s^2\left(N_c + n_f\right) \times (\text{numerical factor}) \tag{18.5}$$

where $N_c = 3$ for SU(3) and $n_f$ is the number of quark flavors. The precise numerical coefficients depend on the normalization conventions.

### 18.5.2 Operator Mixing

A key feature of $O_G$ in the SMEFT RG flow is its **mixing** with other operators. At one loop, $O_G$ mixes with and receives contributions from several classes of operators:

1. **Self-mixing**: $O_G$ renormalizes itself.

2. **Mixing with dipole operators**: Operators like $O_{uG} = (\bar{Q}_L\sigma^{\mu\nu}T^a u_R)\tilde{H}G_{\mu\nu}^a$ can mix into $O_G$.

3. **Mixing with $O_{HG}$**: The operator $O_{HG} = H^\dagger H\, G_{\mu\nu}^aG^{a\mu\nu}$ can mix with $O_G$ under certain conditions.

The mixing pattern is constrained by the symmetries of the theory: operators can only mix if they have the same quantum numbers (same mass dimension, same gauge representation, same CP properties, etc.).

The full anomalous dimension matrix connecting $O_G$ to other dimension-6 operators has been computed as part of the complete one-loop SMEFT running (Jenkins, Manohar, Trott, 2013-2014).

### 18.5.3 Physical Importance of Running

The running and mixing of $O_G$ have practical consequences:

- A Wilson coefficient $C_G$ generated at a high scale $\Lambda$ (from matching to a specific UV model) will evolve as it is run down to the experimental scale ($\sim m_Z$ or $\sim$ TeV).

- Even if $C_G = 0$ at the matching scale, it can be **generated at lower scales** by mixing from other operators that are nonzero.

- Conversely, $C_G \neq 0$ at the matching scale can **generate other operators** at lower scales.

This interconnection between operators through RG running is a fundamental feature of the SMEFT and must be accounted for in any rigorous phenomenological analysis.

## 18.6 Matching $O_G$ to UV Models

Different UV models generate different values of $C_G$. Some examples:

1. **Heavy scalar color octets:** A scalar field transforming in the adjoint (octet) representation of SU(3) can generate $O_G$ when integrated out at tree level.

2. **Heavy vector-like quarks:** Additional heavy quarks can generate $O_G$ at one loop.

3. **Supersymmetric models:** Gluinos and squarks contribute to $C_G$ when integrated out.

The value of $C_G$ is thus a diagnostic: measuring it (or constraining it) tells us about the nature of the heavy particles that exist above the energy scale $\Lambda$.

## 18.7 Current Experimental Bounds

At the LHC, $O_G$ is constrained primarily through:

- **Multi-jet production** at high invariant mass.

- **Inclusive jet cross sections** and angular distributions.

- **Dijet production** at high transverse momentum.

Current bounds on $C_G/\Lambda^2$ are roughly:

$$\frac{|C_G|}{\Lambda^2} \lesssim \mathcal{O}(10^{-2})\text{ TeV}^{-2}$$

This corresponds to a new physics scale $\Lambda \gtrsim$ several TeV for order-one Wilson coefficients.

## 18.8 $O_G$ in the Larger SMEFT Picture

$O_G$ is one of only four operators in Class 1 ($X^3$). It is special because:

1. It is a **purely gluonic operator** — no matter fields involved.

2. It exists only because of the **non-Abelian nature** of QCD.

3. It generates vertices with up to **six gluon legs** at tree level.

4. It modifies QCD interactions at high energy in a way that is characteristic of new colored particles.

5. Its Wilson coefficient is often zero at **tree-level matching** in many simple UV models (it typically requires colored particles in the adjoint or higher representations), making its detection a distinctive signal.

## 18.9 Connection to Sections 2 and 3 of the Thesis

The reader is now equipped with the full conceptual toolkit to understand Sections 2 and 3 of the thesis. Section 2 presents the theoretical framework: the Standard Model, its gauge symmetry, the concept of effective field theory, and the SMEFT expansion. Section 3 focuses on specific operators (including $O_G$), their renormalization group evolution, mixing patterns, and phenomenological implications.

With the knowledge from this book, the reader can:

1. Understand why the SM has the gauge structure $SU(3)_C \times SU(2)_L \times U(1)_Y$.

2. Recognize each term in the SM Lagrangian and know its physical origin.

3. Understand why and how the SMEFT extends the SM with higher-dimensional operators.

4. Read the Warsaw basis operator classification and understand each class.

5. Follow the derivation and interpretation of RGEs for Wilson coefficients.

6. Appreciate the physical meaning of $O_G$ and its role in collider phenomenology.

7. Understand operator mixing and why it is phenomenologically important.

## Conceptual Summary

- $O_G = f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu}$ is a dimension-6 operator built from three gluon field strengths.

- It exists only for non-Abelian gauge groups (needs structure constants $f^{abc}$).

- It generates new multi-gluon vertices not present in QCD.

- Its Wilson coefficient $C_G/\Lambda^2$ parametrizes new physics effects in the gluonic sector.

- Under RG evolution, $O_G$ mixes with other operators, especially dipole and Higgs-gluon operators.

- At the LHC, $O_G$ is constrained through multi-jet production and high-$p_T$ observables.

- Understanding $O_G$ requires the full conceptual apparatus developed in this book: Yang-Mills theory, QCD, renormalization, and EFT.

## Exercises

**Exercise 18.1.** Verify that $O_G$ has mass dimension 6 by counting the mass dimensions of each component. Then explain why it requires a coefficient $C_G/\Lambda^2$ in the SMEFT Lagrangian.

**Exercise 18.2.** Expand $O_G$ by substituting $G_{\mu\nu}^a = \partial_\mu G_\nu^a - \partial_\nu G_\mu^a + g_s f^{abc}G_\mu^b G_\nu^c$ and identify the terms that correspond to 3-gluon, 4-gluon, 5-gluon, and 6-gluon vertices. How does the power of $g_s$ increase with the number of gluon legs?

**Exercise 18.3.** Why can't $O_G$ be generated by a UV model containing only particles that are singlets under $SU(3)_C$ (colorless particles)? What does this tell us about the type of new physics that $O_G$ probes?

---

# Appendix A: Summary of Notation

| Symbol | Meaning |

|---|---|

| $x^\mu = (t, \vec{x})$ | Spacetime four-vector |

| $\eta_{\mu\nu} = \text{diag}(+,-,-,-)$ | Minkowski metric |

| $\partial_\mu = (\partial_t, \vec\nabla)$ | Four-derivative |

| $\slashed{A} = \gamma^\mu A_\mu$ | Feynman slash |

| $D_\mu = \partial_\mu - igA_\mu^a T^a$ | Covariant derivative |

| $F_{\mu\nu}^a$ | Field strength tensor (generic) |

| $G_{\mu\nu}^a$ | Gluon field strength |

| $W_{\mu\nu}^a$ | SU(2) field strength |

| $B_{\mu\nu}$ | U(1) field strength |

| $f^{abc}$ | Structure constants |

| $T^a$ | Lie algebra generators |

| $H$ | Higgs doublet |

| $v \approx 246$ GeV | Higgs VEV |

| $\Lambda$ | New physics scale |

| $C_i$ | Wilson coefficients |

| $\alpha_s = g_s^2/(4\pi)$ | Strong coupling constant |

| $\beta(g) = \mu\frac{dg}{d\mu}$ | Beta function |

| $\gamma_{ij}$ | Anomalous dimension matrix |

---

# Appendix B: The Warsaw Basis — Complete List of Dimension-6 Operators

For reference, the complete set of 59 independent dimension-6 operators (one generation, baryon-number-conserving) in the Warsaw basis:

**$X^3$:**

$O_G$, $O_{\tilde{G}}$, $O_W$, $O_{\tilde{W}}$

**$H^6$:**

$O_H$

**$H^4D^2$:**

$O_{H\Box}$, $O_{HD}$

**$X^2H^2$:**

$O_{HG}$, $O_{H\tilde{G}}$, $O_{HW}$, $O_{H\tilde{W}}$, $O_{HB}$, $O_{H\tilde{B}}$, $O_{HWB}$, $O_{H\tilde{W}B}$

**$\psi^2H^3$:**

$O_{eH}$, $O_{uH}$, $O_{dH}$

**$\psi^2XH$:**

$O_{eW}$, $O_{eB}$, $O_{uG}$, $O_{uW}$, $O_{uB}$, $O_{dG}$, $O_{dW}$, $O_{dB}$

**$\psi^2H^2D$:**

$O_{Hl}^{(1)}$, $O_{Hl}^{(3)}$, $O_{He}$, $O_{Hq}^{(1)}$, $O_{Hq}^{(3)}$, $O_{Hu}$, $O_{Hd}$, $O_{Hud}$

**$(\bar LL)(\bar LL)$:**

$O_{ll}$, $O_{qq}^{(1)}$, $O_{qq}^{(3)}$, $O_{lq}^{(1)}$, $O_{lq}^{(3)}$

**$(\bar RR)(\bar RR)$:**

$O_{ee}$, $O_{uu}$, $O_{dd}$, $O_{eu}$, $O_{ed}$, $O_{ud}^{(1)}$, $O_{ud}^{(8)}$

**$(\bar LL)(\bar RR)$:**

$O_{le}$, $O_{lu}$, $O_{ld}$, $O_{qe}$, $O_{qu}^{(1)}$, $O_{qu}^{(8)}$, $O_{qd}^{(1)}$, $O_{qd}^{(8)}$

**$(\bar LR)(\bar RL) + (\bar LR)(\bar LR)$:**

$O_{ledq}$, $O_{quqd}^{(1)}$, $O_{quqd}^{(8)}$, $O_{lequ}^{(1)}$, $O_{lequ}^{(3)}$

---

# Appendix C: Key Physical Constants

| Quantity | Value |

|---|---|

| Higgs VEV | $v \approx 246$ GeV |

| $W$ boson mass | $m_W \approx 80.4$ GeV |

| $Z$ boson mass | $m_Z \approx 91.2$ GeV |

| Higgs boson mass | $m_h \approx 125$ GeV |

| Top quark mass | $m_t \approx 173$ GeV |

| Strong coupling | $\alpha_s(m_Z) \approx 0.118$ |

| Fine structure constant | $\alpha_{\text{em}} \approx 1/137$ |

| Fermi constant | $G_F \approx 1.166 \times 10^{-5}$ GeV$^{-2}$ |

| $\Lambda_{\text{QCD}}$ | $\approx 200$ MeV |

---

# Appendix D: Glossary

**Abelian group:** A group whose elements all commute: $ab = ba$.

**Adjoint representation:** The representation of a Lie group on its own Lie algebra, with dimension equal to the number of generators.

**Anomalous dimension:** The quantity governing the scale dependence of an operator's normalization under renormalization.

**Asymptotic freedom:** The property that the coupling constant decreases at high energies, occurring in non-Abelian gauge theories like QCD.

**Beta function:** $\beta(g) = \mu\frac{dg}{d\mu}$; governs the running of a coupling constant.

**Chirality:** The property distinguishing left-handed ($P_L\psi$) from right-handed ($P_R\psi$) components of a fermion field.

**Color:** The gauge charge of QCD. Quarks carry three colors; gluons carry eight color combinations.

**Confinement:** The phenomenon that quarks and gluons cannot be isolated; they are always bound in hadrons.

**Covariant derivative:** $D_\mu = \partial_\mu - igA_\mu^aT^a$; a derivative that transforms covariantly under gauge transformations.

**Effective field theory (EFT):** A theoretical framework describing physics at energies below some scale $\Lambda$ by including all operators consistent with the symmetries, organized by dimension.

**Fock space:** The direct sum of Hilbert spaces with all possible particle numbers.

**Fundamental representation:** The smallest non-trivial representation of a Lie group, typically $N$-dimensional for SU(N).

**Gauge symmetry:** A local symmetry of the Lagrangian requiring the introduction of gauge fields to maintain invariance.

**Goldstone boson:** A massless scalar arising from spontaneous breaking of a continuous global symmetry.

**Higgs mechanism:** The process by which gauge bosons acquire mass when a gauge symmetry is spontaneously broken by a scalar field's vacuum expectation value.

**Lie algebra:** The tangent space to a Lie group at the identity, with the commutation relations $[T^a, T^b] = if^{abc}T^c$.

**Lie group:** A group whose elements form a smooth manifold.

**Matching:** The procedure of determining EFT Wilson coefficients by equating predictions of the full and effective theories at a common energy scale.

**Non-Abelian group:** A group with non-commuting elements: $ab \neq ba$ for some $a, b$.

**Operator mixing:** The phenomenon where renormalization causes one operator to generate others under scale evolution.

**Regularization:** A technique to make divergent integrals temporarily finite (e.g., dimensional regularization, cutoff).

**Renormalization:** The procedure of absorbing UV divergences into redefinitions of the bare parameters of the Lagrangian.

**Renormalization group equation (RGE):** Equations governing the scale dependence of couplings and Wilson coefficients.

**Running coupling:** A coupling constant that depends on the energy scale at which it is evaluated.

**SMEFT (Standard Model Effective Field Theory):** The EFT extension of the SM, including higher-dimensional operators built from SM fields.

**Spontaneous symmetry breaking (SSB):** A symmetry of the Lagrangian that is not a symmetry of the vacuum state.

**Structure constants:** The numbers $f^{abc}$ defining the Lie algebra: $[T^a, T^b] = if^{abc}T^c$.

**Warsaw basis:** The standard non-redundant basis of dimension-6 SMEFT operators.

**Wilson coefficient:** The dimensionless coupling multiplying a higher-dimensional operator in an EFT Lagrangian.

**Yang-Mills theory:** A gauge theory based on a non-Abelian Lie group.

---

# Index of Key Equations

| Equation | Description | Number |

|---|---|---|

| Klein-Gordon equation | $(\Box + m^2)\phi = 0$ | (3.3) |

| Euler-Lagrange (fields) | $\partial_\mu\frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)} - \frac{\partial\mathcal{L}}{\partial\phi} = 0$ | (3.1) |

| Noether current | $j^\mu = \frac{\partial\mathcal{L}}{\partial(\partial_\mu\phi)}\delta\phi$ | (4.1) |

| QED Lagrangian | $\bar{\psi}(i\slashed{D}-m)\psi - \frac{1}{4}F^2$ | (8.5) |

| Lie algebra | $[T^a, T^b] = if^{abc}T^c$ | (9.2) |

| Non-Abelian field strength | $F_{\mu\nu}^a = \partial_\mu A_\nu^a - \partial_\nu A_\mu^a + gf^{abc}A_\mu^bA_\nu^c$ | (10.6) |

| SM gauge group | $SU(3)_C \times SU(2)_L \times U(1)_Y$ | (11.1) |

| QCD Lagrangian | $-\frac{1}{4}G_{\mu\nu}^aG^{a\mu\nu} + \bar{q}(i\slashed{D}-m)q$ | (12.2) |

| QCD beta function | $\beta_0 = 11 - \frac{2n_f}{3}$ | (15.2) |

| SMEFT Lagrangian | $\mathcal{L}_{\text{SM}} + \sum_i \frac{C_i}{\Lambda^2}\mathcal{O}_i^{(6)} + \cdots$ | (17.1) |

| $O_G$ operator | $f^{abc}G_\mu^{a\nu}G_\nu^{b\rho}G_\rho^{c\mu}$ | (18.1) |

---

# Final Remarks

This book has constructed, from the foundation of undergraduate quantum mechanics and linear algebra, the complete conceptual and mathematical path to understanding the Standard Model Effective Field Theory at dimension 6, with particular focus on the $O_G$ operator.

The path we traveled:

1. **Why fields?** — Particles must be created and destroyed → quantum fields.

2. **How to describe fields?** — Lagrangian densities, action principles, equations of motion.

3. **What constrains the Lagrangian?** — Symmetries (Noether's theorem, internal symmetries).

4. **How to quantize fields?** — Fock space, creation/annihilation operators, Feynman diagrams.

5. **How to introduce forces?** — The gauge principle: promote global to local symmetry.

6. **How to go non-Abelian?** — Lie groups, structure constants, self-interacting gauge bosons.

7. **What is nature's Lagrangian?** — The Standard Model with $SU(3)_C \times SU(2)_L \times U(1)_Y$.

8. **How do quantum corrections work?** — Renormalization and running couplings.

9. **What if there's more?** — Effective field theory, SMEFT, dimension-6 operators.

10. **What is $O_G$?** — The triple gluon field strength operator, a window into new colored physics.

Each step was necessary. Each concept was introduced before it was used. The student who has worked through this material possesses not just familiarity with the relevant formulas but, more importantly, a coherent understanding of **why** the Standard Model and its EFT extension take the form they do.

The Standard Model is, as of this writing, the most precisely tested theory in the history of science. Yet we know it is incomplete. SMEFT provides the most systematic, model-independent framework for searching for and characterizing whatever lies beyond it. Understanding operators like $O_G$ — their structure, their running, their physical consequences — is at the frontier of this search.

---

*End of text.*
