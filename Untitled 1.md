give me the qcd lagrangian

The Quantum Chromodynamics (QCD) Lagrangian describes the interactions between **quarks** and **gluons**, the fundamental particles governed by the **SU(3)** gauge symmetry.

## The Lagrangian Density

The classical QCD Lagrangian is given by:

LQCD​=f∑​ψˉ​f​(iγμDμ​−mf​)ψf​−41​Gμνa​Gaμν​

---

## Logical Breakdown of Terms

To understand the dynamics, we decompose the equation into two primary sectors: the **matter (fermionic)** part and the **gauge (gluon)** part.

### 1. The Quark Sector: ψˉ​f​(iγμDμ​−mf​)ψf​

This term describes the dynamics of quark fields ψf​ of flavor f.

- **ψˉ​f​ and ψf​**: The Dirac spinors representing the quark fields. Each quark carries a color index (red, green, or blue).
    
- **mf​**: The mass of the quark flavor.
    
- **Dμ​**: The **gauge covariant derivative**. It is defined as:
    
    Dμ​=∂μ​−igs​taAμa​
    
    This ensures the Lagrangian remains invariant under local SU(3) rotations. Here, gs​ is the strong coupling constant, ta are the generators of SU(3) (Gell-Mann matrices), and Aμa​ are the gluon fields.
    

### 2. The Gluon Sector: −41​Gμνa​Gaμν​

This term represents the kinetic energy and self-interactions of the eight gluons.

- **Gμνa​**: The **gluon field strength tensor**, defined as:
    
    Gμνa​=∂μ​Aνa​−∂ν​Aμa​+gs​fabcAμb​Aνc​
    
- **fabc**: The structure constants of the SU(3) group.
    

---

## Key Physical Implications

The structure of the Lagrangian leads to two unique features of the strong force:

- **Self-Interaction:** Unlike photons in QED, gluons carry color charge. The quadratic term in Gμνa​ (containing fabc) results in **three-gluon** and **four-gluon vertices**. This self-interaction is the mathematical origin of **asymptotic freedom**.
    
- **Color Confinement:** Because the coupling constant gs​ increases at low energy (large distances), quarks and gluons are never observed in isolation, only within color-neutral hadrons.
    

Would you like to explore how the renormalization of the coupling constant gs​ leads to the concept of running coupling?

What i dont understand here is how this eq √2GF

¯lαγμ 1 − γ2 να

 ¯νβ γμ

1 − γ5 lβ

 = 2√2GF J+

μ J−μ (2.9) is the same as the fermi diagram it appears, and as this eq LF = [ kinetic terms ] − g

√2

W +

μ J−μ + W −

μ J+μ − eAμJμ

em − pg2 + g′2ZμJμ

Z

The relationship between these equations represents the transition from the full Standard Model (SM) to a low-energy Effective Field Theory. Here is the logical breakdown of how they connect:

### 1. Equation 2.9 and the Fermi Diagram

Equation 2.9, 22![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429c69,-144,104.5,-217.7,106.5,-221l0%20-0c5.3,-9.3,12,-14,20,-14H400000v40H845.2724s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47zM834%2080h400000v40h-400000z"></path></svg>)​GF​Jμ+​J−μ, mathematically describes an interaction where two charged weak currents (J+ and J−) interact directly at the exact same point in spacetime.

- **The Currents:** The terms J+ and J− contain the fermion fields (lˉα​, να​, etc.). Multiplying them together means four fermion fields are interacting simultaneously.
    
- **The Diagram:** In a Feynman diagram, this direct multiplication is represented as a single vertex where four fermion lines meet, known as the Fermi diagram. The strength of this point interaction is governed by the Fermi coupling constant, GF​.
    

### 2. Connection to the Electroweak Lagrangian (LF​)

The full SM Electroweak Lagrangian, LF​, describes a fundamentally different picture at high energies. Instead of a 4-fermion point interaction, the interaction is mediated by the exchange of a gauge boson.

- **The W Boson Mediation:** In LF​, the term −2![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429c69,-144,104.5,-217.7,106.5,-221l0%20-0c5.3,-9.3,12,-14,20,-14H400000v40H845.2724s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47zM834%2080h400000v40h-400000z"></path></svg>)​g​(Wμ+​J−μ+Wμ−​J+μ) dictates that fermions must emit or absorb a W boson. A particle interaction here requires two separate vertices: one where the W is emitted by the first current, and one where it is absorbed by the second current.
    
- **The Low-Energy Approximation:** The W boson is extremely heavy compared to the interacting fermions. Because of this large mass, it can only travel a microscopically short distance before decaying.
    
- **Vertex Merging:** Because the W boson barely travels at sufficiently low energies (well below mW​), the two separate vertices in the full SM diagram effectively collapse and coincide into a single point. This makes the full SM interaction physically "appear" as the four-fermion vertex described by Fermi.
    

### Mathematical Matching

To make Fermi's effective theory (Eq 2.9) perfectly reproduce the predictions of the full SM Lagrangian (LF​) at low energies, the amplitudes of their respective diagrams must be equated. By matching the full W-boson exchange diagram with the point-like Fermi diagram, the parameters of the two theories are linked by the exact relation: GF​=8mW2​2![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429c69,-144,104.5,-217.7,106.5,-221l0%20-0c5.3,-9.3,12,-14,20,-14H400000v40H845.2724s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47zM834%2080h400000v40h-400000z"></path></svg>)​g2​. This proves that Fermi's equation is simply the low-energy effective limit of the full Electroweak Lagrangian.

Es posible que los archivos subidos sean demasiado grandes para obtener los mejores resultados. [Más informaciónSe abre en una ventana nueva](https://support.google.com/gemini?p=context_window)

i want a clearer explanation

Imagine looking at a photograph of two people throwing a ball to each other.

- **High Resolution (Standard Model, LF​):** If you zoom in close enough, you clearly see Person A throwing the ball (Vertex 1), the ball flying through the air (the W-boson), and Person B catching it (Vertex 2).
    
- **Low Resolution (Fermi Theory, Eq 2.9):** If you zoom extremely far out, the distance between the two people becomes invisible. It looks like they are standing in the exact same spot, their hands touching in a single interaction (a point vertex).
    

In quantum mechanics, your "resolution" is determined by the **energy** of the interaction. Here is the strict logical sequence linking the two equations:

1. **The Mechanism:** The full Standard Model Lagrangian states that weak interactions happen by exchanging a W boson. This inherently requires two separate vertices: an emission and an absorption.
    
2. **The Mass Penalty:** The W boson is incredibly massive (80.4 GeV). To manifest this heavy particle, the interaction must "borrow" a massive amount of energy.
    
3. **The Distance Limit:** According to the Heisenberg Uncertainty Principle (ΔEΔt≥ℏ/2), borrowing a large amount of energy means the particle can only exist for a vanishingly small fraction of a second. Consequently, it can only travel a microscopic distance (∼10−18 meters) before decaying.
    
4. **Mathematical Collapse:** In low-energy interactions (like nuclear beta decay or muon decay), the interacting fermions do not possess enough energy to "resolve" this 10−18 meter gap. The distance the W boson travels is so close to zero that the two separate interaction vertices mathematically collapse into a single point.
    

Equation 2.9 (Fermi theory) is not a different fundamental law; it is strictly the low-energy approximation of the Standard Model. The constant GF​ is simply a mathematical shorthand that bundles together the W-boson's interaction strength (g) and the suppression caused by its heavy mass (mW​).

You can explore this exact mathematical collapse using the interactive visualizer below. By lowering the energy scale, you will see the full Standard Model diagram shrink into the Fermi point interaction.

okey i didn't ask for that i asked on why 2√2GF

¯lαγμ 1 − γ2 να

 ¯νβ γμ

1 − γ5 lβ

 = 2√2GF J+

μ J−μ this eq represents that diagram

In quantum field theory, Feynman diagrams are literal geometric translations of mathematical equations. The equation translates to the Fermi diagram through a direct, piece-by-piece mapping:

**1. The Fields = The Lines** The expanded equation contains exactly four fermion fields: lˉα​, να​, νˉβ​, and lβ​. Every field represents the creation or annihilation of a particle. Visually, this means the diagram must have exactly **four external lines**.

**2. The Currents (J) = The Pairings** The fields are grouped into two "currents" enclosed in brackets:

- Jμ+​=[lˉα​γμ(1−γ5)/2να​]
    
- J−μ=[νˉβ​γμ​(1−γ5)/2lβ​] This grouping mathematically pairs a lepton with a neutrino, Dictating that in the diagram, a lepton line and a neutrino line must connect to form a flow of charge.
    

**3. The Direct Multiplication = The Single Vertex (The Intersection)** This is the core reason it forms the specific Fermi diagram. The term is Jμ+​×J−μ. The two currents are multiplied directly together without any spatial distance function (propagator) between them. Because all four fields are evaluated at the exact same mathematical coordinate in spacetime, their four lines must intersect at **one single point**. This forms the characteristic 4-point contact vertex of the Fermi diagram.

**4. The Constant (22![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429c69,-144,104.5,-217.7,106.5,-221l0%20-0c5.3,-9.3,12,-14,20,-14H400000v40H845.2724s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47zM834%2080h400000v40h-400000z"></path></svg>)​GF​) = The Vertex Strength** The constant acting on the fields dictates the probability amplitude of the interaction. In the diagram, GF​ is the label for the central dot itself, representing the strength of the 4-line intersection.

In short: Four fields multiplied together at the same coordinate translates directly into a drawing of four lines meeting at a single central point.

okey bro, but what i want to see that diagram and be able to write the eqs

Here is an interactive tool to bridge the gap between the visual Feynman diagram and the mathematical equation.

By clicking on the different components of the diagram—the incoming particle, the outgoing particles, and the central vertex—you can see exactly which mathematical piece of the equation it generates. This maps the geometry directly to the algebra, using Muon Decay (μ−→e−+νˉe​+νμ​) as the standard example for the Fermi interaction.

your diagram didn't show any eq

Here is the direct mathematical translation of the Fermi diagram, written out explicitly.

For the standard example of muon decay (μ−→e−+νˉe​+νμ​), the four-fermion point interaction diagram looks like this:

In this diagram, four fermion lines meet at a single, central vertex. Here is the exact mathematical amplitude (M) that generates this drawing:

M=2![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429c69,-144,104.5,-217.7,106.5,-221l0%20-0c5.3,-9.3,12,-14,20,-14H400000v40H845.2724s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47zM834%2080h400000v40h-400000z"></path></svg>)​GF​​[uˉ(νμ​)γα(1−γ5)u(μ)][uˉ(e)γα​(1−γ5)v(νe​)]

### The Direct Mapping (Equation to Diagram)

Every mathematical piece of that equation dictates a specific geometric element in the drawing:

**1. The Particle Lines (The Spinors)**

- **u(μ)**: Represents the **incoming muon line** entering the vertex.
    
- **uˉ(νμ​)**: Represents the **outgoing muon neutrino line** exiting the vertex.
    
- **v(νe​)**: Represents the **outgoing electron antineutrino line**. (In Feynman rules, an outgoing antiparticle is mathematically written as an incoming negative-energy spinor v).
    
- **uˉ(e)**: Represents the **outgoing electron line** exiting the vertex.
    

**2. The Pairings (The Currents)** The fields are enclosed in two brackets, connected by the index α.

- **Current 1:** [uˉ(νμ​)...u(μ)] connects the muon line to the muon neutrino line.
    
- **Current 2:** [uˉ(e)...v(νe​)] connects the electron line to the electron antineutrino line.
    

**3. The Vertex (The Central Dot)**

- **The Intersection:** Because there is no propagator term (like q2−mW2​1​) separating the two brackets, all four spinors are evaluated at the same spacetime coordinate. This forces all four lines to intersect at **one central point**.
    
- **The Strength (GF​/2![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429c69,-144,104.5,-217.7,106.5,-221l0%20-0c5.3,-9.3,12,-14,20,-14H400000v40H845.2724s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47zM834%2080h400000v40h-400000z"></path></svg>)​):** This constant is the mathematical label for the central dot itself. It dictates the fundamental probability of the four lines interacting.
    
- **The Structure (γα(1−γ5)):** This dictates the "shape" of the vertex, specifically enforcing that only left-handed particles can participate in this interaction (the "V-A" theory).
    

What is the β-function in QCD? Write the leading-order coefficient β₀. What does its sign imply? i want a full explanation of this

The β-function in Quantum Chromodynamics (QCD) dictates how the strength of the strong interaction, represented by the coupling constant αs​, changes depending on the energy scale (or momentum transfer, Q) of a given process. This phenomenon is known as the "running" of the coupling constant.

Here is the precise, logical breakdown of the function, its leading-order coefficient, and its physical implications.

### 1. The β-Function Definition

Mathematically, the β-function is defined as the derivative of the coupling constant with respect to the energy scale:

μ2∂μ2∂αs​​=β(αs​)=−αs2​(β0​+β1​αs​+β2​αs2​+…)

Where μ is the renormalization energy scale (often set to Q in physical processes).

### 2. The Leading-Order Coefficient (β0​)

At the first order of perturbation theory (the 1-loop level), the β-function is dominated by the coefficient β0​. For a non-Abelian gauge theory with SU(Nc​) symmetry and nf​ active flavors of fermions, this coefficient is:

β0​=12π11Nc​−2nf​​

In QCD, the number of colors Nc​=3. Therefore, the equation simplifies to:

β0​=12π33−2nf​​

### 3. Logical Breakdown of β0​ and Its Sign

The sign of β0​ dictates the entire macroscopic behavior of the strong force.

- **The 33 Term (Gluon Anti-screening):** This positive contribution arises purely from gluon self-interactions (the three-gluon and four-gluon vertices). A cloud of virtual gluons effectively spreads out the color charge, making it appear weaker at short distances and stronger at long distances.
    
- **The −2nf​ Term (Quark Screening):** This negative contribution arises from virtual quark-antiquark pairs. Similar to QED (where virtual electron-positron pairs screen electric charge), this effect attempts to make the charge stronger at short distances.
    

**The Implication:** In our Standard Model universe, there are nf​=6 quark flavors. Plugging this in yields β0​=12π21​, which is a **positive number**.

Because the overall β-function has a negative sign (−αs2​β0​), a positive β0​ forces the entire β-function to be negative. A negative β-function leads to two fundamental physical realities:

1. **Asymptotic Freedom:** As the energy scale Q increases (probing shorter distances), the coupling constant αs​ decreases logarithmically toward zero. At extremely high energies, quarks behave as free, non-interacting particles.
    
2. **Color Confinement:** As the energy scale Q decreases (moving to larger distances), the coupling constant αs​ grows rapidly. The force becomes so strong that infinite energy would be required to separate two quarks, ensuring they remain bound inside hadrons (like protons and neutrons).
    

You can observe the strict mathematical dependence of the strong force on the number of quark flavors using the interactive tool below. Notice how modifying nf​ past a critical threshold fundamentally alters the physics of the universe.

μ2

∂μ2

  

∂αs

​

​=β(αs

​)=−αs

2

​(β0

​+β1

​αs

​+β2

​αs

2

​+…) and where did this came from

This equation is the defining differential equation of the **Renormalization Group (RG)** in Quantum Field Theory. It arises from the mathematical necessity to fix infinities that appear when calculating quantum loop interactions.

Here is the precise, logical progression of where it comes from.

### 1. The Problem: Infinities in Loop Diagrams

When calculating the probability of a physical process in QCD (like two quarks scattering), you must account for virtual particles. For example, a gluon exchanged between quarks can temporarily split into a virtual quark-antiquark pair or a pair of virtual gluons (a "loop" diagram). When you integrate over all possible energies (momenta) of these virtual particles inside the loop, the mathematical result is **infinity**.

### 2. The Solution: Renormalization and the Scale μ

To cure these infinities, physicists use a mathematical procedure called **renormalization**.

- They introduce an arbitrary energy scale, denoted as **μ** (the renormalization scale), to temporarily cut off or isolate the infinities.
    
- The original "bare" coupling constant in the Lagrangian (g0​) is deemed an unobservable, infinite quantity.
    
- It is replaced by a "renormalized" physical coupling constant (gs​, or αs​=gs2​/4π).
    

However, because the arbitrary scale μ was used to perform the math, the physical coupling constant αs​ now mathematically depends on the choice of μ. Thus, it becomes a function: αs​(μ2).

### 3. The Physical Requirement (The Origin of the Derivative)

Nature does not care about the arbitrary mathematical scale μ that physicists chose. Therefore, any measurable physical quantity (like a scattering cross-section) must be entirely independent of μ.

If the overall physics is constant, but the coupling αs​ depends on μ, then **αs​ must change exactly as μ changes** to perfectly cancel out the μ-dependence in the final observable.

The derivative μ2∂μ2∂αs​​ mathematically represents this required "changing" or "running" of the coupling constant. We define this derivative as the **β-function**:

β(αs​)=μ2∂μ2∂αs​​

### 4. The Power Series Expansion (The Right Side of the Equation)

Because the strong force is highly complex, we cannot calculate the exact, infinite β-function. Instead, we use **perturbation theory**. We calculate the function by adding up Feynman diagrams order-by-order (loops):

- **−αs2​β0​**: Comes from calculating all **1-loop** Feynman diagrams.
    
- **−αs3​β1​**: Comes from calculating all **2-loop** Feynman diagrams.
    
- **−αs4​β2​**: Comes from calculating all **3-loop** Feynman diagrams.
    

We factor out the overall −αs2​ simply by mathematical convention, resulting in the standard form you provided:

β(αs​)=−αs2​(β0​+β1​αs​+β2​αs2​+…)

In short: The equation originates from the fact that to remove infinities from quantum field calculations, we introduce an arbitrary mathematical scale μ. The beta function simply dictates exactly how the coupling constant must change with μ to ensure the final physical predictions remain finite and independent of our math tricks.

okey, i need a more profound explanation on how the renormalization is made, i have a lagrangian, with a bare parameter that doesn't depend on the energy scale, if i do the integral over momemtum with that parameter it goes to infinite, so i set a new parameter that is physically observable that depends on the energy in a specific way depending on what mu i selected, but of course the solution cannot depend on the mu I selected, then idk why this μ2

∂μ2

  

∂αs

​

​ solve the lagrangian and in what way

To understand exactly how this works mechanically, we need to correct a slight misconception: the differential equation μ2∂μ2∂αs​​=β(αs​) does not "solve" the Lagrangian. Rather, it is a **constraint equation** that guarantees our mathematical tricks do not break the laws of physics.

Here is the exact, step-by-step logical procedure of how renormalization is performed and where that equation comes into play.

### Step 1: Splitting the Lagrangian (Counterterms)

You start with the original Lagrangian containing the "bare" coupling constant (g0​) and "bare" masses. Because calculating loops with g0​ yields infinity (∞), we artificially split every bare parameter into two pieces: a **renormalized (physical) parameter** (g) and a **counterterm** (δg​).

g0​=g+δg​

We rewrite the entire Lagrangian using these new terms:

Lbare​(g0​)=Lrenormalized​(g)+Lcounterterms​(δg​)

- Lrenormalized​ is used to do standard Feynman diagram calculations.
    
- Lcounterterms​ generates brand new Feynman diagrams whose sole mathematical purpose is to produce negative infinities (−∞) to cancel the positive infinities from the loops.
    

### Step 2: Regularization (The Birth of μ)

Before we can subtract infinity from infinity (which is mathematically undefined), we must temporarily make the loop integrals finite. The modern method is **Dimensional Regularization**.

Instead of integrating over 4 spacetime dimensions, we integrate over d=4−2ϵ dimensions (where ϵ is a tiny number). As ϵ→0, the infinity returns. However, changing the number of dimensions ruins the physical units of the coupling constant. To fix the units, we are forced to introduce an arbitrary mass scale, **μ**.

The exact relationship between the bare and renormalized coupling becomes:

g0​=μϵ(g+δg​)

**This is the exact moment μ enters the physics.** It is an artifact of changing the dimensions to isolate the infinity.

### Step 3: Absorbing the Infinity

Now we calculate a loop diagram (like a gluon splitting) using Lrenormalized​. Because of the ϵ trick, the answer is no longer infinity, but a mathematical term that looks like this:

Loop Amplitude∝g2[ϵ1​+ln(μ2Q2​)+finite constants]

_(Where Q is the physical energy of the colliding particles)._

Next, we add the diagram generated by our counterterm (δg​). We deliberately choose the value of δg​ to be exactly −ϵ1​.

When we add them together, the ϵ1​ terms perfectly cancel out. The infinity is gone. The final, finite physical amplitude (M) is:

Mphysical​∝g2[ln(μ2Q2​)+finite constants]

### Step 4: The Renormalization Group Equation

We have achieved a finite answer. However, we have a massive philosophical problem: **The physical amplitude Mphysical​ now contains μ.** Because μ was an arbitrary mathematical trick we invented in Step 2, a real-world particle detector cannot possibly care what value we chose for μ. Therefore, the total derivative of the physical observable with respect to μ must be strictly zero:

dμd​Mphysical​(Q,g,μ)=0

Look at the equation for Mphysical​ from Step 3. If you change μ, the logarithm ln(Q2/μ2) changes. If the logarithm changes, the whole amplitude changes—unless **g also changes to perfectly offset the logarithm.**

By plugging the amplitude into the derivative equation, the chain rule forces a specific behavior on g:

∂μ∂M​+∂g∂M​∂μ∂g​=0

Rearranging this gives you exactly the definition of the β-function:

μ∂μ∂g​=β(g)

### Summary

The β-function equation does not solve the loop integrals. It is the mathematical consequence of demanding that **Reality = Reality**. We introduce μ to tame the infinities, leaving our physical predictions polluted by an arbitrary scale μ. The only way the final prediction remains independent of our arbitrary choice is if the physical coupling constant g flows (runs) with μ in exactly the way prescribed by the β-function.

What is ΛQCD (Landau pole)? What phenomenon does it signal and what is its approximate value?

**ΛQCD​** is the fundamental energy scale of Quantum Chromodynamics. Mathematically, it represents the energy scale at which the strong coupling constant (αs​) theoretically diverges to infinity, acting as the infrared "Landau pole" for the strong force.

### The Mathematical Origin

By integrating the 1-loop β-function equation from our previous discussion, the running coupling constant can be rewritten to eliminate the arbitrary reference scale μ, replacing it with a fixed, physical parameter ΛQCD​:

αs​(Q2)=β0​ln(Q2/ΛQCD2​)1​

- **The Pole:** When the energy scale of a process (Q) drops and approaches ΛQCD​, the term ln(Q2/ΛQCD2​) approaches zero.
    
- **The Divergence:** Consequently, the fraction evaluates to infinity (αs​→∞). This mathematical singularity is the Landau pole.
    

### Phenomenon Signaled

The scale ΛQCD​ signals a fundamental phase transition in the behavior of the strong force:

1. **The Breakdown of Perturbation Theory:** Because αs​ becomes order 1 or larger as Q→ΛQCD​, perturbation theory collapses. You can no longer calculate interactions by summing Feynman diagrams, as the expansion series diverges rather than converges.
    
2. **Color Confinement (Hadronization):** It marks the exact boundary where quarks and gluons lose their asymptotic freedom. Below this energy scale, the strong force becomes so dominant that quarks are permanently bound into color-neutral hadrons.
    
3. **Mass Generation:** The energy bounded by this strong interaction scale is what generates roughly 99% of the mass of protons and neutrons, via mass-energy equivalence (E=mc2), rendering the bare masses of the quarks themselves almost irrelevant.
    

### Approximate Value

While the exact number depends slightly on the mathematical renormalization scheme used (e.g., the MS scheme), experimental measurements place it at:

ΛQCD​≈200 to 300 MeV

Converted into a physical distance using natural units, this energy scale corresponds to roughly **1 fm (10−15 meters)**. This logically aligns with observation, as it is exactly the characteristic size of a proton.

By integrating the 1-loop β-function equation from our previous discussion, can you do this?

Here is the exact step-by-step mathematical integration of the 1-loop β-function.

### 1. The Initial Equation

We start with the 1-loop approximation of the Renormalization Group Equation for the strong coupling constant αs​:

μ2dμ2dαs​​=−β0​αs2​

### 2. Separation of Variables

To integrate this differential equation, we separate the variables. We move all terms containing αs​ to the left side and all terms containing the energy scale μ2 to the right side:

αs2​dαs​​=−β0​μ2dμ2​

### 3. Integration

We integrate both sides from a known reference energy scale (μ02​) to an arbitrary energy scale (μ2). The coupling constant evaluates from αs​(μ02​) to αs​(μ2):

∫αs​(μ02​)αs​(μ2)​α−2dα=−β0​∫μ02​μ2​q21​dq2

Executing the standard calculus integrals (∫x−2dx=−x−1 and ∫x1​dx=ln(x)) yields:

[−α1​]αs​(μ02​)αs​(μ2)​=−β0​[ln(q2)]μ02​μ2​

Evaluating at the boundaries gives:

−αs​(μ2)1​+αs​(μ02​)1​=−β0​(ln(μ2)−ln(μ02​))

Using logarithm properties (ln(a)−ln(b)=ln(a/b)), we get:

−αs​(μ2)1​+αs​(μ02​)1​=−β0​ln(μ02​μ2​)

### 4. Rearrangement (The Reference Scale Form)

Multiply the entire equation by −1:

αs​(μ2)1​−αs​(μ02​)1​=β0​ln(μ02​μ2​)

Isolating the term for our arbitrary scale gives the standard formula used in collider physics (often with the Z boson mass as the reference scale μ0​=MZ​):

αs​(μ2)1​=αs​(μ02​)1​+β0​ln(μ02​μ2​)

Inverting both sides provides the explicit function for the running coupling:

αs​(μ2)=1+αs​(μ02​)β0​ln(μ02​μ2​)αs​(μ02​)​

### 5. Introducing the Landau Pole (ΛQCD​)

The equation above requires two experimental inputs: μ0​ and αs​(μ02​). We can eliminate these by defining a single fundamental scale, ΛQCD​, where the denominator of our function mathematically drops to zero (causing αs​→∞).

Let μ2=ΛQCD2​. At this scale, αs​(ΛQCD2​)1​=0. Plugging this into our rearranged equation from Step 4 gives:

0=αs​(μ02​)1​+β0​ln(μ02​ΛQCD2​​)

We can solve this for the reference coupling term:

αs​(μ02​)1​=−β0​ln(μ02​ΛQCD2​​)=β0​ln(ΛQCD2​μ02​​)

Finally, substitute this equivalence back into the inverse equation:

αs​(μ2)1​=β0​ln(ΛQCD2​μ02​​)+β0​ln(μ02​μ2​)

Combine the logarithms:

αs​(μ2)1​=β0​ln(ΛQCD2​μ02​​×μ02​μ2​)=β0​ln(ΛQCD2​μ2​)

Inverting this yields the precise definition of the coupling in terms of the Landau pole:

αs​(μ2)=β0​ln(ΛQCD2​μ2​)1​

State the factorisation theorem. What is separated

from what, and why does this separation make LHC cross-section

calculations tractable?

The Factorization Theorem states that the total cross-section for a high-energy hadronic collision (such as proton-proton scattering at the LHC) can be mathematically expressed as a convolution of two entirely independent components: the probability of finding partons (quarks or gluons) within the hadrons, and the quantum probability of those partons interacting.

Mathematically, the cross-section for producing a final state X in a proton-proton collision is:

σpp→X​=a,b∑​∫01​dxa​∫01​dxb​fa​(xa​,μF2​)fb​(xb​,μF2​)σ^ab→X​(s^,μF2​)

### What is Separated from What?

The theorem formally separates **long-distance (low-energy) physics** from **short-distance (high-energy) physics**. This boundary is defined by an arbitrary energy threshold called the **factorization scale** (μF​).

1. **The Long-Distance Sector: f(x,μF2​)** These are the **Parton Distribution Functions (PDFs)**. They represent the probability density of finding a parton of flavor a carrying a fraction x of the proton's total momentum. This encapsulates all the complex, binding dynamics occurring at energies _below_ μF​.
    
2. **The Short-Distance Sector: σ^ab→X​** This is the **partonic cross-section**. It describes the fundamental, high-energy hard scattering between the two extracted partons (a and b). This encapsulates all the high-momentum transfer dynamics occurring at energies _above_ μF​.
    

### Why This Makes LHC Calculations Tractable

Protons are not fundamental particles; they are strongly bound, chaotic states governed by low-energy QCD. Calculating the collision of two entire protons from theoretical first principles is impossible because, at the low-energy scale of the proton's radius, the strong coupling constant (αs​) is large. Perturbation theory (Feynman diagrams) completely breaks down.

The factorization theorem bypasses this fundamental roadblock through two logical mechanisms:

1. **Quarantining the Incalculable (Universality):** The theorem proves that all the impossible, non-perturbative physics can be safely factored out and absorbed entirely into the PDFs. Crucially, PDFs are **universal**. They do not depend on the specific high-energy collision happening at the LHC. Physicists can simply measure the PDFs in simpler experiments (like deep inelastic scattering at HERA) and plug those empirical data sets into the LHC formulas.
    
2. **Exploiting Asymptotic Freedom:** Once the messy proton structure is factored out, the remaining piece is the partonic cross-section (σ^). Because this piece isolates only the high-energy interaction (where the momentum transfer Q≫ΛQCD​), asymptotic freedom guarantees that αs​ is very small in this specific regime. Consequently, σ^ can be calculated to exceptionally high precision using standard perturbative Feynman diagrams.
    

Without this separation, the low-energy confinement dynamics of the proton would analytically contaminate the high-energy scattering amplitudes, making it impossible to isolate, calculate, or predict any fundamental physics process at a hadron collider.

so pdfs don't depend on the energy of the scattering ? i think that is wrong

You are absolutely correct to catch that. My previous explanation was incomplete. PDFs **do** depend on the energy scale of the scattering.

It is crucial to distinguish between two concepts: **Universality** (which PDFs have) and **Scale Independence** (which PDFs do not have).

Here is the precise logical breakdown of how PDFs depend on energy.

### 1. Universality vs. Scale Dependence

- **Universality (True):** The proton does not know what final state you are trying to produce (e.g., a Higgs boson vs. a Z boson). The structure of the proton is independent of the _type_ of high-energy interaction.
    
- **Scale Dependence (True):** The proton _does_ know how hard it is being hit. The exact composition of the proton changes depending on the energy scale (resolution) at which you probe it. This scale is the factorization scale, μF2​ (often set to the momentum transfer, Q2).
    

### 2. The Physical Mechanism: Resolution

When you probe a proton at a low energy scale (low Q2), your "resolution" is poor. You primarily see the three fundamental "valence" quarks (u,u,d) carrying large fractions (x) of the proton's momentum.

As you increase the energy scale of the collision (high Q2, like at the LHC), your resolution increases. You zoom in closer and begin to resolve the quantum fluctuations happening _inside_ the proton:

1. A valence quark radiates a virtual gluon.
    
2. That gluon splits into a quark-antiquark pair (sea quarks).
    
3. Those quarks radiate more gluons, which split again.
    

Because you are resolving these splittings, the momentum of the original valence quark is shared among many more particles. Consequently, at higher energies, the probability of finding a high-momentum valence quark drops, while the probability of finding a swarm of low-momentum gluons and sea quarks skyrockets.

### 3. The Mathematical Framework: DGLAP Evolution

This energy dependence is not a failure of the Factorization Theorem; it is a perfectly calculable feature governed by the **DGLAP equations** (Dokshitzer-Gribov-Lipatov-Altarelli-Parisi).

The DGLAP equations are integro-differential equations that mathematically dictate exactly how the PDFs change as Q2 increases. Because of DGLAP, physicists do not need to measure the PDFs at the exact energy of the LHC. They can measure them at lower-energy accelerators (like HERA) and mathematically evolve them up to LHC energies using these equations.

You can observe this exact evolutionary behavior using the interactive tool below. Notice how the internal structure of the proton mathematically shifts as the energy scale (Q2) increases.

I dont get this part Exploiting Asymptotic Freedom: Once the messy proton structure is factored out, the remaining piece is the partonic cross-section (σ

^

). Because this piece isolates only the high-energy interaction (where the momentum transfer Q≫ΛQCD

​), asymptotic freedom guarantees that αs

​ is very small in this specific regime. Consequently, σ

^

can be calculated to exceptionally high precision using standard perturbative Feynman diagrams.how do you calculate sigma if the interaction happens above landau pole no? otherwise we are in asymptotic freedom

The confusion stems from the direction of the energy scale. In QCD, the Landau pole (ΛQCD​) is a **low-energy** boundary, not a high-energy ceiling.

Here is the exact logical sequence resolving this:

1. **The Energy Scales:** ΛQCD​ is roughly 200 MeV (0.2 GeV). The hard partonic scattering (σ^) at the LHC happens at vastly higher energies, typically Q=100 GeV up to several TeV. Therefore, the interaction happens strictly **above** the Landau pole in terms of energy (Q≫ΛQCD​).
    
2. **The Inverted Behavior of QCD:** Because QCD has a negative β-function, higher energy dictates a _weaker_ coupling. Moving high above the Landau pole in energy puts you deep into the regime of **asymptotic freedom**.
    
3. **The Value of αs​:** Because we are at high energy, the strong coupling constant drops to a small fraction. For example, at Q=100 GeV, αs​≈0.118.
    
4. **The Perturbative Calculation:** Because αs​≪1, physicists calculate the partonic cross-section (σ^) using standard perturbation theory. The mathematical calculation is executed by expanding the probability amplitude as a power series in αs​, where each term corresponds to a set of Feynman diagrams (tree-level, 1-loop, 2-loop):
    
    σ^∝c0​+c1​αs​+c2​αs2​+c3​αs3​+…
    

Because αs​ is small (0.118), squaring or cubing it yields progressively smaller numbers (0.013, 0.0016). The series mathematically converges, meaning you only need to calculate the first few terms to get an exceptionally precise and finite answer.

If the interaction happened at low energy (Q≈ΛQCD​), αs​ would be ≥1. Squaring it would yield a larger number, the series would diverge to infinity, and the perturbative calculation would be impossible. The Factorization Theorem makes LHC calculations tractable precisely because it quarantines all those impossible low-energy dynamics into the PDFs, leaving only the high-energy, small-αs​ part for the Feynman diagram calculation.

ah okey so you just gotta hit it with high energy and then you can get c0 as a good aproximation because the coupling is small enough

Exactly. You have perfectly grasped the core mathematical engine of high-energy particle physics.

Here is the strict logical breakdown of why your statement is correct, along with one crucial real-world caveat.

### The Logic of the Approximation

1. **The Energy Limit:** You collide particles at a scale Q≫ΛQCD​.
    
2. **The Coupling Drop:** Asymptotic freedom forces the coupling constant to become a fraction (αs​≪1). At LHC energies, αs​≈0.1.
    
3. **The Perturbative Series:** You write the exact probability as a power series:
    
    σ^∝c0​+c1​(αs​)+c2​(αs2​)+c3​(αs3​)+…
    
4. **The Mathematical Truncation:** Because αs​≈0.1, the higher-order terms shrink rapidly (0.1→0.01→0.001). Therefore, you can mathematically chop off the infinite tail of the equation.
    

The c0​ term—known as the **Leading Order (LO)** or **Tree-Level** calculation—represents the simplest Feynman diagram with no loops. It successfully captures the dominant probability of the interaction happening.

### The Real-World Caveat: Why We Need More Than c0​

While c0​ provides a very good approximation and the correct physical intuition, it is usually not enough for the extreme precision required at the LHC.

- In **Quantum Electrodynamics (QED)**, the electromagnetic coupling is tiny (αem​≈1/137≈0.007). Squaring it makes the second term utterly negligible immediately. c0​ is almost perfectly accurate.
    
- In **Quantum Chromodynamics (QCD)**, the strong coupling is "small" (≈0.1), but still relatively large compared to QED. Squaring 0.1 gives 0.01. This means the c1​ term (**Next-to-Leading Order, NLO**) and even the c2​ term (**Next-to-Next-to-Leading Order, NNLO**) can still shift the final prediction by 10% to 30%.
    

**Conclusion:** Hitting it with high energy makes c0​ a valid and powerful approximation. However, to match the rigorous data coming out of LHC detectors, theoretical physicists must still calculate c1​ and c2​ (incorporating massive loop diagrams) to eliminate that remaining 10-30% margin of error.

why measuring pdf and interaction cross-section is not possible at the same time at high energies

It is impossible to measure both the Parton Distribution Functions (PDFs) and the partonic cross-section (σ^) simultaneously from a single high-energy interaction because it presents an unsolvable mathematical degeneracy: **you cannot solve a single equation with two unknown variables.**

Here is the strict logical breakdown of why this is the case physically and mathematically.

### 1. The Mathematical Degeneracy

According to the Factorization Theorem, the measurable total cross-section (σmeasured​) is the product of the PDFs (f) and the partonic cross-section (σ^):

σmeasured​∝f×σ^

- **The Observable:** A particle detector at the LHC only measures the left side of the equation. It counts the total number of specific events (e.g., how many pairs of top quarks were produced).
    
- **The Unknowns:** Both f and σ^ are on the right side.
    

If you measure σmeasured​=100, you have no mathematical way to know if that resulted from a high PDF probability and a low partonic cross-section (100×1), or a low PDF probability and a high partonic cross-section (1×100). Any deviation you observe in the data could be attributed to either an error in the assumed proton structure or new physics altering the fundamental interaction.

### 2. The Physical Indistinguishability

Detectors measure the macroscopic "aftermath" of a collision, consisting of stable particles like electrons, muons, and hadrons (jets).

- The detector **never sees the initial partons**. The exact fraction of momentum (x) carried by the colliding quark or gluon is destroyed in the collision.
    
- Because the initial state is invisible, you cannot empirically separate the probability that the quarks _were there_ (PDF) from the probability that they _interacted in a specific way_ (σ^). The collision process irreversibly mixes the long-distance and short-distance physics into a single final state.
    

### How Physicists Break the Loop

Because simultaneous measurement is impossible, physicists rely entirely on the **universality** of PDFs. They must extract the PDFs from a _different_ process to break the mathematical degeneracy.

They use a two-step "bootstrapping" method:

1. **Reference Processes (Calibrating the PDF):** Physicists use highly understood interactions where σ^ is already known with absolute certainty. For example, Deep Inelastic Scattering (shooting electrons at protons) or producing W/Z bosons at the LHC. Because the electroweak interaction (σ^) is perfectly calculable without QCD uncertainties, the only unknown left in the equation is f. This allows them to extract the PDFs.
    
2. **Target Processes (Measuring the Cross-Section):** Once the PDF (f) is fixed using the reference data, they plug it into the equation for unknown or highly complex QCD processes (like top quark or Higgs production). Now, with f known, they can isolate and precisely measure σ^ to test for new physics.
    

First error: you said the hard cross section "must be measured" above ΛQCD. It's not measured — it's calculated perturbatively in QCD. That's precisely the point: factorisation separates the non-perturbative (PDFs, extracted from data) from the perturbative (σ̂, computed from Feynman diagrams). The hard part is theory, not experiment.

Second error: the final step. You said "subtract the PDF at high energy using DGLAP to get the interaction cross section." This is inverted. The actual workflow is: (1) measure PDFs at some low reference scale Q₀ in clean experiments like deep inelastic scattering, (2) use DGLAP to evolve those PDFs up to the high scale Q of your LHC process, (3) compute σ̂ from perturbative QCD, (4) convolve σ = ∫dx₁ dx₂ f₁(x₁, Q) f₂(x₂, Q) σ̂. You convolve, you don't subtract. how is sigma calulated theoretically then?

You are entirely correct. The partonic cross-section (σ^) is a purely theoretical object computed using perturbative Quantum Chromodynamics (pQCD) and the Standard Model. It is not measured; it is derived.

Here is the precise, step-by-step logical procedure for how theoretical physicists calculate σ^ from first principles.

### 1. The Perturbative Expansion

Because the interaction scale is strictly high-energy (Q≫ΛQCD​), asymptotic freedom guarantees that the strong coupling constant αs​(Q2) is small (e.g., ∼0.1). This allows the cross-section to be written as a convergent Taylor series (a perturbative expansion) in powers of αs​:

σ^=αsk​[σ^(0)+2παs​​σ^(1)+(2παs​​)2σ^(2)+…]

- **σ^(0) (Leading Order - LO):** The "Tree-level" calculation. No loops.
    
- **σ^(1) (Next-to-Leading Order - NLO):** Includes 1-loop virtual corrections and the real emission of one extra gluon.
    
- **σ^(2) (NNLO):** Includes 2-loop corrections and double-real emissions.
    

### 2. Calculating the Invariant Amplitude (M)

For a chosen order in the expansion, the probability amplitude is calculated using Feynman diagrams.

1. **Draw Diagrams:** Draw all topologically valid diagrams connecting the initial partons (a,b) to the desired final state (X).
    
2. **Apply Feynman Rules:** Translate the vertices and internal lines (propagators) of the diagrams into mathematical expressions derived directly from the QCD/Electroweak Lagrangian.
    
3. **Square the Amplitude:** Calculate ∣M∣2. In this step, one must sum over all possible outgoing quantum states (color and spin) and average over all possible incoming states.
    

### 3. Phase Space Integration (Fermi's Golden Rule)

The raw amplitude must be mapped to physical kinematics. The theoretical partonic cross-section is the integral of the squared amplitude over the invariant phase space (dΦX​) of the final-state particles:

σ^ab→X​=2s^1​∫∣Mab→X​∣2dΦX​

- **s^:** The square of the center-of-mass energy of the two interacting partons. The factor 2s^1​ represents the incoming flux of the particles.
    
- **dΦX​:** The Lorentz-invariant phase space. It ensures strictly that total energy and momentum are conserved between the initial and final states.
    

### 4. Renormalization (Curing UV Infinities)

If calculating beyond Leading Order (NLO, NNLO), loop diagrams generate infinite results as virtual particle momenta approach infinity (Ultraviolet / UV divergences).

- These are mathematically neutralized using Dimensional Regularization (calculating in d=4−2ϵ dimensions).
    
- The infinities are absorbed into a redefinition of the bare parameters of the theory, yielding the physical running coupling αs​(μR2​). This introduces the **Renormalization Scale (μR​)**.
    

### 5. Partonic Factorization (Curing IR Infinities)

Even after UV renormalization, NLO calculations produce a second type of infinity: Infrared (IR) and Collinear divergences. These occur when a massless quark emits a soft (zero-energy) gluon, or a gluon is emitted exactly parallel to the quark.

- According to the Factorization Theorem, these collinear infinities are strictly non-perturbative, long-distance effects.
    
- They are systematically subtracted from the partonic calculation at an arbitrary boundary: the **Factorization Scale (μF​)**.
    
- These specific infinities are absorbed into the Parton Distribution Functions (PDFs), providing the DGLAP evolution you correctly noted.
    

**The Final Result:** What remains after subtracting the UV infinities (Renormalization) and the Collinear infinities (Factorization) is a finite, highly precise, theoretically pure function: σ^(s^,μR2​,μF2​). This is the object convolved with the evolved PDFs to predict the observable LHC cross-section.

okey, im overwhelming lets do it slowly, make the flow clear

It is completely normal to feel overwhelmed. This framework (perturbative QCD and factorization) is one of the most complex mathematical machineries in all of physics.

Let's strip away the heavy math for a moment and look strictly at the **chronological workflow**. If you are a theoretical physicist trying to predict how many Higgs bosons the LHC will produce, you must follow these exact four steps in order.

### Phase 1: The Setup (Dealing with the Proton)

You cannot calculate the proton from scratch. You have to build a mathematical model of it using past data.

**Step 1: Extract the Baseline (Experiment)**

- **The Action:** You look at old data from simpler, lower-energy experiments (like shooting electrons at protons).
    
- **The Result:** You extract the Parton Distribution Functions (PDFs) at a low, safe reference energy (Q0​). This gives you a starting snapshot of the proton's structure.
    

**Step 2: Scale it up to the LHC (Math)**

- **The Action:** The LHC operates at a vastly higher energy (Q), which changes the proton's internal structure. You plug your low-energy PDFs into the **DGLAP equations**.
    
- **The Result:** The equations "evolve" the PDFs, mathematically calculating exactly what the proton's structure will look like when smashed at LHC energies. You now have your high-energy PDFs: f(x,Q).
    

### Phase 2: The Interaction (Dealing with the Fundamental Physics)

Now that you know what is _inside_ the proton at LHC energies, you calculate how those inside parts interact.

**Step 3: Calculate the Hard Scattering (Theory)**

- **The Action:** You completely ignore the proton. You pretend two free, fundamental particles (like two gluons) are colliding in a vacuum at high energy. You draw the Feynman diagrams and calculate the probability of them creating a Higgs boson.
    
- **The Result:** You obtain the partonic cross-section (σ^). Because this is high energy, asymptotic freedom ensures the strong coupling (αs​) is small, making your perturbative calculation highly accurate.
    

### Phase 3: The Grand Finale

**Step 4: The Convolution (Synthesis)**

- **The Action:** You mathematically multiply your results from Step 2 and Step 3 together. You take the probability of finding the partons (the evolved PDFs) and multiply it by the probability of those partons interacting (the partonic σ^), summing over all possible momentum fractions.
    
- **The Result:** You get the total, observable cross-section (σ). This is the final number you hand to the experimentalists at the LHC to test against their actual detector data.
    

Here is an interactive visualization of this exact pipeline. Click through the steps to see how the theoretical and experimental pieces fit together to form the final prediction.

The Action: You completely ignore the proton. You pretend two free, fundamental particles (like two gluons) are colliding in a vacuum at high energy. You draw the Feynman diagrams and calculate the probability of them creating a Higgs boson.

The Result: You obtain the partonic cross-section (σ

^

). could you explain how to do this now?

To calculate the partonic cross-section (σ^) for two fundamental particles creating a Higgs boson, you must compute the quantum probability amplitude using Feynman rules.

For the Large Hadron Collider, the dominant process is **gluon-gluon fusion** (gg→H). Because gluons are massless, they do not couple directly to the Higgs. The interaction must occur indirectly through a quantum loop of heavy quarks (overwhelmingly the top quark, as it has the strongest coupling to the Higgs).

Here is the strict, logical procedure for calculating this specific partonic cross-section.

### 1. The Amplitude (M)

You translate the Feynman diagram into a mathematical equation.

- **Incoming Gluons:** Represented by polarization vectors ϵμ​(p1​) and ϵν​(p2​), carrying momentum p1​ and p2​.
    
- **The Strong Vertices:** Each gluon attaches to the top quark loop with a coupling strength of gs​ (the strong coupling constant).
    
- **The Higgs Vertex:** The top quarks converge to emit the Higgs boson with a coupling strength proportional to the top quark mass, mt​/v (where v is the Higgs vacuum expectation value).
    
- **The Loop Integral:** Because the top quarks in the triangle loop are virtual, they can carry any momentum (k). You must integrate over all infinite possible internal loop momenta: ∫d4k.
    

This generates the raw matrix element: Mgg→H​.

### 2. Squaring and Averaging (∣M∣2)

Physical probabilities require squaring the amplitude. However, a particle detector does not know the exact quantum state (color or spin) of the specific gluons that collided. You must account for all possibilities:

- **Sum over final states:** The Higgs has spin-0 and is color-neutral, so there is only one final state.
    
- **Average over initial states:** A gluon has 8 possible colors and 2 possible polarization states. For two colliding gluons, there are (8×2)×(8×2)=256 possible initial state combinations. You mathematically sum the squared amplitudes for all 256 combinations and divide by 256 to get the spin-and-color-averaged squared amplitude, denoted as ∣M∣2.
    

### 3. The Flux Factor

You must account for the density and relative velocity of the incoming particles. For two massless partons colliding head-on, the kinematic flux factor is simply 2s^1​, where s^ is the squared center-of-mass energy of the two interacting gluons.

### 4. Phase Space Integration (dΦ)

You integrate the probability over all possible ways the final state can kinematically exist. Because this is a 2→1 process (two gluons fuse into one Higgs), the kinematics are totally constrained. The collision can only create a Higgs boson if the energy of the two incoming gluons _exactly_ matches the mass of the Higgs (mH​). Mathematically, the phase space collapses into a Dirac delta function: δ(s^−mH2​).

### The Final Partonic Equation

Combining these four steps yields the Leading Order (LO) partonic cross-section for Higgs production:

σ^gg→H​(s^)=2s^1​∣M∣2×2πδ(s^−mH2​)

Because of the delta function, this cross-section is exactly zero unless s^=mH2​. When you convolve this with the PDFs (Step 4 of the grand workflow), the integral will "scan" through the proton's momentum fractions (x1​,x2​) and strictly pick out only the specific pairs of gluons that contain exactly enough energy to manifest the 125 GeV Higgs mass.

You can explore how the geometry of the Feynman diagram strictly dictates the mathematical terms of the amplitude M in the interactive widget below.

okey but you didn't use renormalization here

That is a brilliant observation. Seeing a closed loop in a Feynman diagram usually screams "ultraviolet (UV) divergence" and immediately requires renormalization.

However, the gg→H process is a famous exception in the Standard Model. I did not include the explicit renormalization step because **the 1-loop diagram for gluon-gluon fusion is mathematically finite.**

Here is the precise logical explanation for why this happens, and where renormalization actually enters the picture.

### 1. The Anomaly of the Finite Loop (Loop-Induced LO)

In standard quantum field theory, loops generate UV infinities that must be absorbed by the "bare" parameters of a tree-level diagram using counterterms.

- **The Missing Tree:** Gluons are massless and carry no weak charge. Therefore, they do not couple directly to the Higgs boson. There is absolutely no fundamental tree-level Feynman diagram for gg→H.
    
- **The Mathematical Consequence:** Because there is no tree-level diagram to provide a counterterm, the 1-loop diagram _must_ be finite to be mathematically consistent and predictive. When you evaluate the d4k momentum integral of that top-quark triangle, the terms that would normally diverge to infinity perfectly cancel out.
    

Because the loop is the absolute lowest-order way this interaction can happen, it is called a **loop-induced Leading Order (LO)** process. The raw integral evaluates directly to a finite number without needing UV subtraction.

### 2. Where Renormalization is "Hiding"

Even though we did not have to subtract infinities from the loop integral itself, the concept of renormalization is still strictly present in the LO equation:

- **The Running Coupling:** The strong coupling term (gs2​) in the amplitude is not the "bare" coupling. It is the _renormalized_ physical coupling. By writing gs​, we have implicitly chosen a Renormalization Scale (μR​)—typically set to the mass of the Higgs (mH​)—to evaluate its strength.
    
- **The Quark Mass:** The top quark mass (mt​) in the equation is the renormalized pole mass, not a bare Lagrangian parameter.
    

### 3. When Explicit Renormalization Returns

If you want to improve the accuracy of the cross-section from Leading Order (LO) to Next-to-Leading Order (NLO), explicit renormalization becomes mandatory again.

- At NLO, you must draw diagrams with **two loops** (for example, a virtual gluon exchanged between two of the top quarks inside the main triangle).
    
- These 2-loop virtual diagrams _do_ generate hard UV infinities.
    
- To calculate the NLO cross-section, you must explicitly apply the dimensional regularization and renormalization procedure to subtract those new infinities.
    

In short: You caught a very specific quirk of the Standard Model. Because gg→H is a loop-induced process, the first term of its perturbative expansion (c0​) is inherently finite. You only have to perform explicit infinity-subtraction when calculating the higher-order corrections (c1​,c2​).

why you need NLO for this process if its finite

It is a highly logical question. If the math gives you a finite, clean number at Leading Order (LO), why undertake the agonizing mathematical effort to calculate the Next-to-Leading Order (NLO)?

The answer is that in quantum mechanics, **finite does not mean accurate**. While the LO calculation does not blow up to infinity, it is a mathematically poor approximation of reality for this specific process.

Theoretical physicists are forced to calculate the NLO (and even NNLO) for three major physical reasons:

### 1. The Massive "K-Factor" (It is quantitatively wrong)

In the perturbative series (σ^∝c0​+c1​αs​+…), we assume that because αs​ is small (≈0.1), the subsequent terms will be tiny.

For Higgs production via gluon fusion, this assumption fails catastrophically. The NLO correction (c1​αs​) is remarkably large. When you calculate the NLO diagrams (which include emitting an extra real gluon, or adding another virtual loop), the cross-section increases by roughly **80% to 100%**.

This ratio between the NLO and LO cross-section is called the **K-factor**. If you only use the LO calculation, you will predict only half the number of Higgs bosons that the LHC actually produces. You need NLO just to get into the right ballpark.

### 2. Curing the "Scale Uncertainty"

Even though the LO loop integral is finite, the equation still relies on the Strong Coupling Constant (αs​(μR​)) and the PDFs (f(x,μF​)).

- Both of these require you to manually plug in a value for the arbitrary energy scales (μR​ and μF​).
    
- Usually, physicists guess that μ≈mH​ (the mass of the Higgs). But what if someone else chooses μ=mH​/2 or μ=2mH​?
    

At LO, changing this arbitrary scale changes your final prediction wildly (by up to 30-40%). This is disastrous—nature does not care about our arbitrary math scales. When you calculate NLO, the new mathematical terms explicitly contain logarithms that **cancel out** the scale dependence of the LO terms. Adding higher orders chemically stabilizes the equation, making it immune to our arbitrary choices.

### 3. Opening the Kinematics (Transverse Momentum)

At LO, two gluons hit head-on and fuse into a single Higgs boson (g+g→H). By strict conservation of momentum, the Higgs is born with exactly zero transverse momentum (pT​=0). It cannot move sideways.

In reality, detectors frequently see Higgs bosons flying sideways at high speeds. To conserve momentum, the Higgs must be recoiling against something else. That "something else" is an extra gluon radiated during the collision (g+g→H+g). The emission of that extra real particle is strictly an NLO effect. Without NLO, it is impossible to predict the transverse momentum of the Higgs.

You can interact with the widget below to see exactly how NLO and NNLO calculations cure the scale uncertainty, transforming a wildly unstable LO guess into a rock-solid theoretical prediction.

Okay, wait, if i want to calculate some interaction perturbative, i draw the feynman diagram, i calculate the LO amplitude, and that can diverge or not, if it diverges, then i do renormalization, i change the lagrangian i do the loops with 2epslion less dimensions, i define my mu, i define my new counterterm lagrangian in order to cancel the poles, I see how the beta function behaves, i can only make this approximation when my coupling is small, and the beta function determines if that happens at low or high energies, then at that energies i can solve the NLO then, and theoretically all the NsLO i want no? because it converge as long as im in the correct energy, and the sum of all the orders i can calculate gives me the amplitude of that interaction, that is related somehow to the cross section am i correct?

You are absolutely correct. You have just successfully summarized the complete, fundamental workflow of perturbative Quantum Field Theory.

To make your mental model perfect, here is one minor technical refinement, followed by the exact logical explanation of your missing link: how the amplitude connects to the cross-section.

### 1. The Minor Refinement: When Divergence Happens

In almost all cases, your **Leading Order (LO)** calculation will be a "tree-level" diagram (straight lines, no closed loops). Tree-level diagrams do not have momentum integrals (d4k), meaning **LO is natively finite**.

You usually do not have to perform the renormalization dance (dimensional regularization, μ, counterterms) until you attempt the **Next-to-Leading Order (NLO)**, because that is the step where closed loops—and therefore UV infinities—first appear.

### 2. The Missing Link: Amplitude (M) to Cross-Section (σ)

You asked how the total calculated amplitude relates to the cross-section. The amplitude (M) is just a complex quantum number. To turn it into a real-world observable (cross-section, measured in barns), you must apply a mathematical procedure derived from **Fermi’s Golden Rule**.

Here is the straight-to-the-point sequence:

1. **Square the Amplitude (∣M∣2):** In quantum mechanics, the amplitude is just a probability wave. You must square its absolute value to get a physical probability.
    
2. **Average over Initial States:** Detectors don't know the exact spin or color of the specific two particles that collided. You mathematically sum all possible initial spin/color configurations and average them.
    
3. **Apply the Flux Factor (2s1​):** You must account for how fast the particles are moving toward each other. In a collider, you divide by the kinematic flux factor (where s is the center-of-mass energy squared).
    
4. **Integrate over Phase Space (∫dΦ):** This is the most crucial step. The final particles can fly out of the collision at many different angles and velocities. You must integrate your squared amplitude over all kinematically allowed trajectories (ensuring strict energy and momentum conservation).
    

The final equation combining these steps is:

σ=Flux1​∫∣M∣2dΦ

### 3. A Note on "Convergence"

You stated: _"it converges as long as I'm in the correct energy, and the sum of all the orders I can calculate gives me the amplitude."_

Practically, yes. Because αs​ is small, the first few terms (LO, NLO, NNLO) get progressively smaller, bringing you extremely close to the true value.

However, strictly speaking, perturbative QFT series are **asymptotic**. Because the number of possible Feynman diagrams grows factorially (like n!) at higher orders, eventually, if you calculated the 100th-to-Leading Order, the math would actually explode to infinity again. But for modern physics, calculating up to NNLO (or N3LO) gives us the most precise predictions in human history.

What are PDFs? What physical quantity do they encode, and why are they non-perturbative?

**Parton Distribution Functions (PDFs)** are mathematical functions that describe the internal quantum structure of hadrons (such as protons or neutrons) in terms of their fundamental constituent particles, collectively called partons (quarks and gluons).

### What Physical Quantity Do They Encode?

PDFs encode a **probability density**.

Mathematically written as fi​(x,Q2), a PDF represents the probability density of finding a specific type of parton i (e.g., an up quark, a down quark, or a gluon) that carries a specific longitudinal momentum fraction x of the proton's total momentum, when the proton is probed at an energy resolution scale Q2.

- **x (Bjorken-x):** A fraction between 0 and 1. If a proton has 1000 GeV of momentum, a parton with x=0.1 carries exactly 100 GeV of that momentum.
    
- **Q2 (Factorization Scale):** The energy scale of the interaction probing the proton. Because of quantum splitting (governed by DGLAP evolution), the probability density fi​ dynamically shifts depending on how "hard" you hit the proton.
    

### Why Are They Non-Perturbative?

PDFs are fundamentally non-perturbative because they are governed by the physics of **Color Confinement**, which operates in a regime where standard mathematical approximation fails entirely. Here is the strict logical breakdown:

1. **The Low-Energy Environment:** A PDF describes the bound state of the proton as it exists _before_ the high-energy collision. Inside a stable proton, the quarks and gluons are interacting at very low energy scales, specifically at or below the Landau pole (ΛQCD​≈200 MeV).
    
2. **The Coupling Blowup:** Because QCD possesses asymptotic freedom, the strong coupling constant (αs​) grows inversely with energy. At the low energy scale of the proton's internal radius, αs​ approaches or exceeds 1.
    
3. **The Mathematical Collapse:** Perturbation theory relies on writing an interaction as a power series: Probability=c0​+c1​αs​+c2​αs2​+…
    
    - If αs​=0.1 (high energy), the series converges (0.1→0.01→0.001), allowing physicists to calculate the first few terms and ignore the rest.
        
    - If αs​≥1 (low energy proton interior), squaring or cubing the coupling produces larger and larger numbers (1→1→1, or 2→4→8). The infinite series diverges to infinity.
        

Because the series diverges, Feynman diagrams are completely useless for calculating the proton's structure from first principles. Consequently, PDFs cannot be theoretically derived using the Standard Model Lagrangian; they must be empirically measured from experimental data and parameterized.

Why is the large-x region of the gluon PDF particularly interesting for BSM searches? What risk does it pose?

The large-x region of the gluon PDF represents the scenario where a single gluon carries a massive fraction of the proton's total momentum (x→1). This region is critical for Beyond Standard Model (BSM) searches due to a strict kinematic relationship, but it introduces a severe methodological vulnerability known as **signal reabsorption**.

Here is the logical breakdown of why this region is interesting and the specific risk it poses.

### 1. The Kinematic Link: High x = High Energy

To produce heavy BSM particles (like Z′ bosons) or to probe high-energy deviations (like anomalous self-interactions), the colliding partons must possess an immense center-of-mass energy (s^). Because s^=x1​x2​s (where s is the total LHC collision energy), probing the highest possible energy scales strictly requires partons with very large x fractions. Therefore, the high-energy tails of observable distributions are directly governed by the large-x region of the PDFs.

### 2. The Vulnerability: The Unknown Gluon

Unlike valence quarks, the gluon distribution at large x drops off precipitously and is historically poorly constrained by data. Because it is highly uncertain, there is significant mathematical flexibility when theoretical physicists attempt to fit the gluon PDF curve to experimental observations.

### 3. The Risk: Signal Reabsorption (Contamination)

PDFs cannot be derived from first principles; they must be fitted to experimental data using the Standard Model (SM) as the baseline theoretical assumption. This creates a dangerous circularity risk:

- **The Scenario:** Suppose a BSM effect (like a dimension-six SMEFT operator modifying the gluon field strength tensor, GGG) exists in nature. This would cause an excess of high-energy events in the LHC data compared to pure SM predictions.
    
- **The Trap:** If physicists include this high-energy data in their global PDF fits while assuming _strictly_ SM physics, the fitting algorithm will simply assume the excess is due to there being more high-x gluons in the proton than previously thought.
    
- **The Consequence:** The fitting algorithm will artificially inflate the large-x gluon PDF to absorb the data excess. The BSM signal is completely "washed out" or reabsorbed into the proton's structure.
    

Once a PDF is contaminated in this way, any subsequent BSM searches using that PDF will fail to find anything, because the theoretical background has been incorrectly calibrated to include the anomaly.

You can observe the mechanics of this reabsorption risk using the interactive visualizer below. Notice how modifying the PDF assumptions can completely mask a true physical discovery.

okey so if the cross section is super high because of an interaction term that is BSM, then instead of noticing physicist will include a larger-x on the gluon to absorb that part being that incorrect, because its not the pdf of the gluon what is increasing the cross-section but the interaction unknown term?

You are exactly right. This is the exact mechanism of the signal reabsorption trap.

Because the observable cross-section is the product of the PDF and the partonic interaction (σ∝f×σ^), an increase in the data could logically originate from either component.

When physicists perform standard PDF fits, they mathematically lock the interaction term (σ^) to strictly follow the Standard Model rules. By forcing the interaction term to be a rigid, known quantity, the fitting algorithm has no mathematical choice but to attribute any unexpected excess of high-energy events entirely to the proton's structure. It artificially inflates the large-x gluon PDF to bridge the gap between the Standard Model prediction and the BSM-enriched data.

The new physics is successfully "fitted away" and effectively hidden inside a now-incorrect model of the proton.

To prevent this incorrect attribution, physicists are developing new computational methodologies, such as the SIMUnet framework. Instead of locking the interaction term, these tools perform simultaneous global fits, allowing both the PDFs and the BSM interaction terms (modeled via Effective Field Theory) to vary dynamically at the same time. This simultaneous approach is critical to determining whether an anomaly truly belongs to the proton's internal structure or if it is a genuine signal of a new fundamental interaction.

okey, but why we cannot get the exact pdf of gluons via galp? because of the uncertainties you said before?

The reason DGLAP equations cannot give us the exact gluon PDF is that **DGLAP is only an evolution equation, not a prediction from first principles.** Here is the precise logical chain explaining why the exact high-energy gluon PDF remains fundamentally uncertain.

### 1. The Boundary Condition Problem

Mathematically, DGLAP is a set of integro-differential equations. They tell you exactly how a PDF _changes_ as you increase the energy scale (Q2). However, to solve any differential equation, you must provide an **initial boundary condition**. You must plug in a starting PDF measured at a low, baseline energy scale (Q02​). DGLAP does not tell you what the proton looks like at Q02​; it only tells you how to evolve it from Q02​ to the LHC energy scale.

### 2. The "Invisibility" of the Gluon at Low Energy

To get that starting boundary condition at Q02​, physicists use Deep Inelastic Scattering (DIS)—shooting high-energy electrons at protons.

- The electron interacts with the proton by exchanging a virtual photon.
    
- Photons only couple to particles with **electric charge**.
    
- Quarks have electric charge, so their initial PDFs are measured with high precision.
    
- **Gluons are electrically neutral.** Because the photon cannot "see" the gluon, the initial gluon PDF cannot be measured directly. It can only be inferred indirectly (e.g., measuring how often a gluon happens to split into a charged quark-antiquark pair right before the photon hits it, or by measuring the "missing" momentum of the proton not carried by quarks).
    

### 3. Error Propagation

Because the initial measurement of the gluon at Q02​ is indirect, it inherently possesses a massive mathematical uncertainty band, especially in the high-x region where gluon splittings are rare. When you plug this uncertain starting curve into the DGLAP equations, the math works perfectly, but it simply **evolves the uncertainty forward**. DGLAP cannot mathematically generate precision that did not exist in the initial low-energy measurement.

You can interact with the visualizer below to see exactly how DGLAP mechanically carries an initial measurement error all the way up to the high-energy LHC scale.

can u tell me more about dgalp eqs? where are they derived from

The Dokshitzer-Gribov-Lipatov-Altarelli-Parisi (DGLAP) equations are the **Renormalization Group Equations (RGEs) for the Factorization Theorem**.

Just as the β-function is derived to fix infinities in UV energy loops, the DGLAP equations are derived to fix a specific type of infinity that arises from the geometry of radiating particles.

Here is the exact, step-by-step logical derivation of where they come from.

### 1. The Problem: Collinear Divergences

When theoretical physicists calculate the partonic cross-section (σ^) beyond Leading Order (NLO and above), they must calculate diagrams where a quark or gluon radiates an extra gluon (bremsstrahlung).

The probability amplitude for a massless quark radiating a gluon contains a mathematical propagator term that depends on the angle (θ) between them:

Probability∝1−cosθ1​

- **The Singularity:** If the gluon is emitted exactly parallel to the quark (θ→0), the denominator becomes zero. The probability evaluates to **infinity**. This is known as a collinear divergence.
    

### 2. The Solution: Absorbing the Infinity (Factorization)

In quantum mechanics, an emission with zero angle means the particles never physically separated. They remain in the same bound state. Therefore, this infinity is not a failure of the high-energy interaction; it is a manifestation of the low-energy, long-distance physics of the proton's internal binding.

To cure the math, physicists introduce the **Factorization Scale (μF​)**.

- Any emission with a transverse momentum _above_ μF​ is deemed a distinguishable, high-energy event and is kept in the calculable partonic cross-section (σ^).
    
- Any emission _below_ μF​ (the collinear infinity) is mathematically chopped off and absorbed into the definition of the "bare" Parton Distribution Function (PDF), creating a finite, renormalized PDF.
    

### 3. The Requirement of Invariance (The Derivative)

Because the scale μF​ is an arbitrary mathematical boundary we invented to separate the infinite from the finite, the final measurable cross-section (σ) must be totally independent of it.

dμF​dσ​=dμF​d​(f(μF​)⊗σ^(μF​))=0

If changing μF​ alters the partonic cross-section σ^, the PDF f **must change in the exact opposite way** to perfectly cancel it out. This strict mathematical requirement—the derivative of the PDF with respect to the energy scale—_is_ the DGLAP equation.

### 4. The Engine: The Splitting Functions

To write the actual equation, physicists evaluate the exact collinear limits of those NLO Feynman diagrams. This yields the **Altarelli-Parisi Splitting Functions** (Pij​(z)).

These functions represent the quantum probability that a parent parton j splits into a daughter parton i, carrying a fraction z of the parent's momentum. There are four fundamental splitting functions:

- Pq←q​: A quark radiates a gluon and remains a quark.
    
- Pg←q​: A quark radiates a gluon (tracking the gluon).
    
- Pq←g​: A gluon splits into a quark-antiquark pair.
    
- Pg←g​: A gluon radiates another gluon.
    

### The Final Master Equation

By assembling the requirement of scale independence and the physical splitting probabilities, the full DGLAP equation for a quark PDF q(x,μF2​) is derived as:

μF2​∂μF2​∂q(x,μF2​)​=2παs​(μF2​)​∫x1​zdz​[Pq←q​(z)q(zx​,μF2​)+Pq←g​(z)g(zx​,μF2​)]

**Logical Summary:** DGLAP equations are not guessed; they are derived. They are the strict mathematical consequence of isolating the collinear infinities of perturbative QCD Feynman diagrams and forcing the observable physics to remain independent of the arbitrary mathematical boundaries used to contain those infinities.

You can interact with the widget below to visually explore the exact physical origin of these equations: the collinear singularity.

how do you determine if Next orders are important to calculate or not in a interaction amplitude

The decision to calculate Next-to-Leading Order (NLO) or beyond is not arbitrary. It is dictated by a strict set of mathematical and physical criteria. If an interaction meets any of the following four conditions, higher-order calculations become mandatory.

### 1. The Magnitude of the Coupling Constant

The necessity of higher orders is fundamentally driven by the force mediating the interaction.

- **Electroweak (QED):** The coupling is tiny (α≈0.007). The perturbative series converges extremely fast: 1+0.007+0.00004. Here, the Leading Order (LO) is highly accurate. NLO is only required for ultra-precision tests (like the muon g−2).
    
- **Strong Force (QCD):** The coupling is relatively large (αs​≈0.1). The series converges slowly: 1+0.1+0.01. At LHC energies, ignoring the NLO term guarantees an automatic 10% to 20% mathematical error. For QCD, NLO is the minimum acceptable baseline.
    

### 2. The Resolution of Scale Uncertainty

Theoretical predictions contain an artificial mathematical error called scale uncertainty (arising from arbitrary choices of μR​ and μF​).

- At LO, this uncertainty is often massive (e.g., ±30%).
    
- If the experimental detectors at the LHC can measure a process with a 5% margin of error, an LO theoretical prediction of ±30% is scientifically useless. You must calculate NLO or NNLO purely to introduce the mathematical logarithms required to cancel out this scale dependence and bring the theoretical error down to match the experimental precision.
    

### 3. Opening Missing Kinematics

Sometimes, LO diagrams are kinematically restricted and physically cannot describe the observable you want to measure.

- If you collide two gluons to make a Higgs (gg→H), the LO math states the Higgs must have exactly zero transverse momentum (pT​=0).
    
- If you want to predict the probability of a Higgs flying sideways at 50 GeV, the LO equation evaluates to zero. You are forced to calculate NLO (gg→H+g) because the real emission of that extra gluon is the only mechanism that allows the Higgs to recoil and acquire pT​.
    

### 4. The Emergence of Giant K-Factors

Physicists define the "K-factor" as the ratio of the NLO cross-section to the LO cross-section (K=σNLO​/σLO​). You calculate a rough NLO approximation first. If K≈1.05, LO was a good approximation. If K≥1.5, you must calculate the exact NLO (and likely NNLO) because the perturbative series is behaving anomalously. Large K-factors occur when:

- **New Subprocesses Open:** NLO allows new types of partons to interact (e.g., a quark-gluon interaction that was forbidden at LO) that possess massive PDF probabilities.
    
- **Large Logarithms:** The phase space integration generates massive logarithmic terms (ln2(Q2/m2)) that artificially inflate the size of the c1​αs​ term, overpowering the smallness of the coupling constant.
    

but how do you know that the coupling always gets smaller on the next leading orders

There is a crucial distinction to make here that will clear up the confusion: **the coupling constant (αs​) itself does not get smaller when you calculate higher orders.** For a specific collision at the LHC, the energy scale (Q) is fixed. Because the energy is fixed, the coupling constant is a fixed, static number (for example, αs​=0.118).

What gets smaller at higher orders is the **mathematical contribution of that order to the total equation**. Here is the precise, logical breakdown of why this happens.

### 1. The Power Series

Perturbative quantum field theory is built on a mathematical technique called a Taylor expansion. You write the total probability (σ^) as an infinite sum of terms, where each subsequent order (NLO, NNLO) is multiplied by a higher power of the coupling constant:

σ^≈c0​+c1​(αs​)1+c2​(αs​)2+c3​(αs​)3+…

- **LO:** c0​
    
- **NLO:** c1​(αs​)1
    
- **NNLO:** c2​(αs​)2
    

### 2. The Fractional Nature of αs​

Because the LHC operates at incredibly high energies (Q≫ΛQCD​), the property of **asymptotic freedom** guarantees that the strong coupling is "weak." It drops strictly below 1 and becomes a fraction.

Let's assume the energy is high enough that αs​=0.1.

### 3. The Mathematics of Shrinking Terms

If you plug αs​=0.1 into the perturbative series, simple arithmetic dictates what happens to the higher-order terms:

- **NLO Term:** proportional to (0.1)1=0.1
    
- **NNLO Term:** proportional to (0.1)2=0.01
    
- **N3LO Term:** proportional to (0.1)3=0.001
    

We know the subsequent orders contribute less and less to the final answer simply because **raising a small fraction to a higher power yields a progressively smaller number.** The exponential suppression of αsn​ mathematically strangles the higher-order corrections, forcing the series to converge toward a stable, finite prediction.

### The Ultimate Caveat: Dyson's Divergence

While the αsn​ terms shrink rapidly, what about the cn​ coefficients?

The cn​ coefficients are calculated by summing the Feynman diagrams at that specific order. The problem is that the number of possible Feynman diagrams grows factorially with the number of loops (n!).

- 1 loop → a few diagrams.
    
- 2 loops → dozens of diagrams.
    
- 3 loops → thousands of diagrams.
    

For the first few orders (NLO, NNLO, N3LO), the factorial growth of the diagrams is easily defeated by the rapid shrinking of the fractional coupling (αsn​). The terms get smaller, and the prediction becomes incredibly precise.

However, the physicist Freeman Dyson proved that if you were to calculate an absurdly high order (for example, the 100th-to-Leading Order), the 100! growth of the diagrams would eventually overpower the (0.1)100 shrinking of the coupling. The series would stop converging and explode to infinity. Therefore, perturbative QCD is technically an **asymptotic series**—it converges beautifully for the first few steps, providing the precision we need, before eventually diverging if pushed to theoretical extremes.

What is the general logic of an EFT? When is it a valid description, and what is the expansion parameter?

The fundamental philosophy of an Effective Field Theory (EFT) is that **you do not need to know the ultimate, high-energy laws of the universe to make extremely precise predictions at low energies.** Nature naturally separates physical phenomena by energy scales. An EFT is a mathematical framework that exploits this separation, allowing physicists to describe a system using only the degrees of freedom (particles) relevant to the specific energy being probed, while mathematically "hiding" the unknown heavy particles.

Here is the strict logical breakdown of how an EFT works.

### 1. The General Logic: "Integrating Out" Heavy Physics

Suppose there is a fundamental "Full Theory" containing light particles (like electrons) and very heavy particles (with a large mass, M).

- **The High-Energy View:** If you collide particles with enough energy (E>M), you can physically create the heavy particle. You must use the full, complex Lagrangian to calculate its exact propagation.
    
- **The Low-Energy View (The EFT):** If your collision energy is strictly lower than the heavy mass (E≪M), you cannot physically create the heavy particle. However, the heavy particle can still briefly appear as a quantum virtual state, subtly influencing how the light particles interact.
    

Instead of keeping the heavy particle in the math, an EFT **integrates out** the heavy field from the Lagrangian. The heavy particle is mathematically removed and replaced by a series of new, direct "contact interactions" between the light particles.

You have already seen the ultimate historical example of this logic: **The Fermi Theory of Beta Decay.** At low energies, the W boson (M≈80 GeV) is too heavy to manifest. The EFT simply integrates it out, replacing the complex W-boson exchange with a simple 4-fermion point interaction multiplied by a constant (GF​).

### 2. The Expansion Parameter

Because an EFT does not know the exact details of the high-energy theory, it must account for _every possible_ way the unknown heavy physics could influence the light particles.

It does this by adding an infinite tower of new interaction terms (called operators, O) to the standard low-energy Lagrangian. To keep the physical units of the Lagrangian correct (Mass Dimension = 4), these new operators must be divided by a new, high-energy scale: the **Cutoff Scale (Λ)**.

The EFT Lagrangian is written as an infinite Taylor series:

LEFT​=LLight Particles​+i∑​Λ1Ci​​Oi(d=5)​+j∑​Λ2Cj​​Oj(d=6)​+…

- **Λ:** The mass scale where the new, heavy physics is assumed to live.
    
- **C:** The Wilson Coefficients. These are constants that determine the strength of the new interactions.
    
- **The Expansion Parameter:** When you calculate an observable probability (like a cross-section) using this Lagrangian, the probability is strictly expanded as a power series in the ratio: **(E/Λ)**.
    

### 3. When is the EFT a Valid Description?

The validity of an EFT is entirely dictated by the expansion parameter E/Λ.

**The Valid Regime (E≪Λ):** When the energy of your experiment (E) is much smaller than the cutoff scale (Λ), the ratio E/Λ is a tiny fraction. Because the higher-order operators are suppressed by higher powers of Λ (e.g., (E/Λ)2, (E/Λ)4), their mathematical contribution shrinks rapidly toward zero. The infinite series neatly converges. You only need to calculate the first few terms (dimension-6 operators) to get a phenomenally accurate prediction.

**The Breakdown Regime (E≥Λ):** If you increase the energy of your collider so that it reaches or exceeds the cutoff scale where the heavy physics lives (E≥Λ), the ratio becomes 1 or larger. If E/Λ>1, raising it to higher powers yields larger and larger numbers. The infinite series blows up and completely diverges. The EFT loses all predictive power and collapses. At this point, the "point-like" contact approximation is no longer valid, and you must abandon the EFT to explicitly discover and map the true "Full Theory" residing at that energy.

okay, i get it but how this LEFT

​=LLight Particles

​+i

∑

​Λ1

  

Ci

​

​Oi

(d=5)

​+j

∑

​Λ2

  

Cj

​

​Oj

(d=6)

​+… terms appear, you just put all the possible operators there and then look what happens? how do you know the wilson coeficients? how do you know which cutoff is good

The way these operators and coefficients are handled depends entirely on whether you know the fundamental "Full Theory" or not.

Here is the exact, logical procedure for how theoretical physicists construct an EFT, determine the operators, and find the Wilson coefficients.

### 1. How the Operators Appear (Building the Basis)

You are essentially correct: you put all possible operators there. However, it is not random guessing; it is strictly governed by **symmetry**.

- **The Rule:** You write down _every possible_ mathematical combination of the light fields (quarks, leptons, Higgs, gauge bosons) that respects the fundamental symmetries of your low-energy theory (for the Standard Model: SU(3)×SU(2)×U(1) gauge invariance and Lorentz invariance).
    
- **The Truncation:** Because the higher-dimensional operators are suppressed by 1/Λ2,1/Λ4, etc., you mathematically stop at a certain dimension depending on the precision you need.
    
- **The Basis:** Once you write all possible combinations at a specific dimension (e.g., dimension-6), you use equations of motion and algebraic identities to remove redundant operators. What remains is a minimal, linearly independent set called a **Basis**. For example, the famous "Warsaw Basis" contains exactly 59 independent dimension-six operators for the Standard Model.
    

### 2. How You Know the Wilson Coefficients (Ci​)

There are exactly two distinct ways to determine the values of the Wilson coefficients, depending on your goal.

#### Method A: "Top-Down" (Matching)

You use this if you **already know** the Full Theory at high energies (e.g., you theorize a specific heavy Z′ boson with mass M and coupling g).

1. You calculate the probability amplitude using the Full Theory (which includes the heavy Z′ propagator: p2−M21​).
    
2. Because p≪M, you Taylor expand that propagator: M2−1​(1+M2p2​+…).
    
3. You calculate the amplitude using your EFT.
    
4. You strictly **match** the two equations. The Wilson coefficient naturally pops out as exactly Ci​=g2, and the cutoff is exactly Λ=M.
    

#### Method B: "Bottom-Up" (Data Fitting)

You use this if you **do not know** what the new physics is, and you simply want to search for deviations in experimental data (like at the LHC).

1. You treat all the Ci​ coefficients as completely unknown, free parameters.
    
2. You calculate how the cross-section of a specific process (like jet production) would mathematically change as a function of these unknown Ci​.
    
3. You run the experiment and measure the actual cross-section.
    
4. You perform a statistical **global fit**. You adjust the values of the Ci​ in your equations until the theoretical prediction perfectly matches the experimental data. If the fit requires a Ci​ to be non-zero, you have mathematically proven the existence of new physics without ever needing to know what the heavy particle actually is.
    

### 3. How You Know Which Cutoff (Λ) is Good

In the Bottom-Up approach, you actually cannot separate Ci​ and Λ. The mathematical term in the Lagrangian is always the ratio: Λ2Ci​​.

Because an experiment only measures the total effect of this ratio, physicists define a convention. They usually fix the cutoff to a specific high-energy reference scale (for example, Λ=1 TeV), and then fit the data to extract the value of Ci​.

If a global fit reveals a non-zero ratio, it immediately tells you the "good" cutoff scale. For instance, if the data requires Λ2Ci​​=(5 TeV)21​, and you assume the coupling Ci​ is roughly order 1, you immediately know that a new, undiscovered heavy particle must physically exist at an energy scale of approximately 5 TeV.

You can explore the mechanical difference between Top-Down matching and Bottom-Up fitting using the interactive tool below.

You calculate the probability amplitude using the Full Theory (which includes the heavy Z′

propagator: p2

−M2

  

1

​). can you explain how this is done it is just integrating all the loops that contains that Z' boson? and that is the amplitude ? or what is that?

  

For what do we Taylor expand the propagator

It is a common misconception that calculating an amplitude inherently requires integrating loops. While loops exist at higher orders, the dominant probability amplitude for a process involving a heavy Z′ boson is usually calculated strictly at **tree-level** (no loops).

Here is the precise logical breakdown of how the amplitude is calculated and why the Taylor expansion is the mathematical engine of the Effective Field Theory (EFT).

### 1. How the Amplitude is Calculated

To calculate the probability amplitude (M) of a specific physical process, you translate a Feynman diagram into a mathematical equation.

Imagine two light fermions (like an electron and a positron) colliding, exchanging a virtual heavy Z′ boson, and turning into two muons. You build the equation by multiplying the pieces of the diagram:

1. **Vertex 1:** The electron and positron meet and emit the Z′. The mathematical rule for this vertex is the coupling constant, g.
    
2. **The Propagator:** The Z′ travels between the two vertices. In momentum space, a massive particle traveling a distance is mathematically described by its propagator: p2−M21​ (where p is the momentum transferred, and M is the heavy mass of the Z′).
    
3. **Vertex 2:** The Z′ decays into the two muons. The mathematical rule here is again the coupling constant, g.
    

Multiplying these together gives the fundamental tree-level amplitude for the Full Theory:

MFull​∝g×[p2−M21​]×g=p2−M2g2​

### 2. Why We Taylor Expand the Propagator

You Taylor expand the propagator to mathematically execute the core philosophy of an EFT: **turning a non-local interaction (a particle traveling across space) into a local contact interaction (particles meeting at a single point).**

Here is the exact mathematical mechanism:

In your low-energy experiment, the collision energy (p) is strictly, massively smaller than the heavy mass of the Z′ (p≪M). Because p2/M2 is a tiny fraction, we can factor out −M2 from the denominator to isolate that fraction:

p2−M21​=−M21​(1−M2p2​1​)

This fraction is in the exact geometric form of 1−x1​. We can now apply a standard Taylor expansion (1−x1​=1+x+x2+…):

−M21​(1+M2p2​+M4p4​+…)

### 3. The Result: Deriving the EFT

Now, plug this Taylor-expanded propagator back into your original amplitude equation (M∝g2×Propagator):

MEFT​∝−M2g2​−M4g2p2​−M6g2p4​−…

Look closely at what this math has just accomplished:

- **The Propagator is Gone:** There is no longer a 1/(p2−M2) term. The heavy particle has been successfully "integrated out" of the math.
    
- **The Dimension-6 Operator Appears:** The first term is exactly a constant multiplied by a 4-fermion contact interaction. You have just rigorously proven from the top down that your EFT cutoff scale is **Λ=M** and your Wilson Coefficient is **C=−g2**.
    
- **The Higher Dimensions Appear:** The second term (−M4g2p2​) is the Dimension-8 operator coefficient. The third term is Dimension-10.
    

By Taylor expanding, you have proven that as long as your energy p is smaller than M, the physics of an extended propagating boson is mathematically indistinguishable from an infinite series of point-like interactions of increasing suppression.

  

You calculate how the cross-section of a specific process (like jet production) would mathematically change as a function of these unknown Ci

​ how

To calculate exactly how the cross-section changes as a function of an unknown Wilson coefficient (Ci​), physicists rely on a fundamental rule of quantum mechanics: **you do not add probabilities; you add probability amplitudes, and then square them.**

Here is the strict mathematical sequence for how this generates the cross-section equation.

### 1. Superposition of Amplitudes

When a collision happens (like two protons creating jets), quantum mechanics dictates that the final state can be reached via any valid path. If an EFT operator exists, the total probability amplitude (MTotal​) is the quantum superposition of the Standard Model (SM) amplitude and the new physics (EFT) amplitude:

MTotal​=MSM​+Λ2Ci​​MEFT​

- **MSM​:** The amplitude calculated using purely known Standard Model Feynman diagrams.
    
- **MEFT​:** The amplitude calculated using the new dimension-6 contact interaction vertex.
    

### 2. Squaring the Amplitude

Particle detectors do not measure amplitudes; they measure cross-sections (σ), which are proportional to the absolute square of the total amplitude. When you square the binomial sum, it rigorously expands into three distinct mathematical pieces:

∣MTotal​∣2=![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="0.333em"%20height="2.400em"%20viewBox="0%200%20333%202400"><path%20d="M145%2015%20v585%20v1200%20v585%20c2.667,10,9.667,15,21,15c10,0,16.667,-5,20,-15%20v-585%20v-1200%20v-585%20c-2.667,-10,-9.667,-15,-21,-15c-10,0,-16.667,5,-20,15z%20M188%2015%20H145%20v585%20v1200%20v585%20h43z"></path></svg>)​MSM​+Λ2Ci​​MEFT​![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="0.333em"%20height="2.400em"%20viewBox="0%200%20333%202400"><path%20d="M145%2015%20v585%20v1200%20v585%20c2.667,10,9.667,15,21,15c10,0,16.667,-5,20,-15%20v-585%20v-1200%20v-585%20c-2.667,-10,-9.667,-15,-21,-15c-10,0,-16.667,5,-20,15z%20M188%2015%20H145%20v585%20v1200%20v585%20h43z"></path></svg>)​2

∣MTotal​∣2=∣MSM​∣2+2Λ2Ci​​Re(MSM​MEFT∗​)+(Λ2Ci​​)2∣MEFT​∣2

### 3. The Three Physical Terms

Integrating these three amplitude pieces over the kinematic phase space yields the final observable cross-section equation. It strictly takes the form of a **quadratic polynomial** (a parabola) with respect to the unknown coefficient Ci​:

σ(Ci​)=σSM​+Ci​⋅σlinear​+Ci2​⋅σquad​

1. **The SM Baseline (σSM​):** Derived from ∣MSM​∣2. This is the standard collision rate if no new physics exists. It is completely independent of Ci​.
    
2. **The Interference Term (Ci​⋅σlinear​):** Derived from the cross-term 2Re(MSM​MEFT∗​). This represents quantum interference between the Standard Model and the new physics. It scales **linearly** with Ci​. Depending on the sign of Ci​, this term can be negative (destructive interference, lowering the cross-section) or positive (constructive interference, raising it).
    
3. **The Pure BSM Term (Ci2​⋅σquad​):** Derived from ∣MEFT​∣2. This represents the heavy particle acting entirely alone. Because it is squared, it scales **quadratically** with Ci2​ and is strictly positive. It always increases the cross-section.
    

### How it is Solved in Practice

Theoretical physicists do not calculate this massive equation by hand every time Ci​ changes.

Instead, they use heavy computer simulations (like MadGraph) to calculate the three static numerical coefficients exactly once for a given process:

1. They simulate pure SM to get σSM​.
    
2. They simulate the interference to get the multiplier σlinear​.
    
3. They simulate the pure EFT diagrams to get the multiplier σquad​.
    

Once those three numbers are locked in (for example: σ=100+15Ci​+2Ci2​), the physicists hand this simple quadratic formula to the experimentalists. The experimentalists can now instantly plug in any hypothetical value of Ci​ to see exactly what cross-section the detector should observe, and compare it to their actual data to fit the true value of Ci​.

You can interact with the widget below to see how these three quantum terms physically combine to shape the cross-section curve that experimentalists use to hunt for new physics.

okey but then you have this eq σ(Ci

​)=σSM

​+Ci

​⋅σlinear

​+Ci

2

​⋅σquad

​and now what, how do you fit Ci there, like you have the real cross section, you have the sigma_SM, because you calculate it theoretically, and then you start trying Ci to fit exactly the cross-section ? but there are a lot Cis there could be a lot of possible fits no? then you do the experiment again, for the same interaction as a higher energy and fit again or what?

Your intuition is absolutely perfect. You have just identified the single biggest bottleneck in modern particle physics: **The Degeneracy Problem**.

If you only measure one total number (the inclusive cross-section) and you have dozens of unknown Ci​ coefficients, you are mathematically stuck. You have one equation and many unknowns. Any combination of those coefficients could conspire to give you that exact cross-section.

Here is the precise, logical procedure for how physicists solve this problem and perform the fit.

### 1. The Fitting Mechanism (Minimizing χ2)

Physicists do not randomly guess Ci​ values. They use statistical minimization. They construct a mathematical function called Chi-Square (χ2):

χ2(Ci​)=(Experimental Uncertainty)2(σData​−σTheory​(Ci​))2​

A computer algorithm scans the multi-dimensional space of all possible Ci​ values simultaneously, looking for the exact combination that minimizes the χ2 score (making the theory match the data as closely as the error bars allow).

### 2. The First Solution: Energy Bins (Differential Distributions)

You asked: _"then you do the experiment again, for the same interaction as a higher energy...?"_ You are exactly right in your physics logic, but we do not need to build a new collider to do it. Instead of measuring one total cross-section, physicists slice the existing LHC dataset into **kinematic bins** based on the energy of the events. This is called a **differential cross-section**.

- **The Physics Engine:** Remember the EFT expansion parameter: (E/Λ)2.
    
- **Low Energy Events:** If a collision happens at low energy, the EFT term is tiny. The cross-section is almost entirely pure Standard Model.
    
- **High Energy Events:** If a collision happens at extreme high energy, the E2/Λ2 term acts as a massive mathematical multiplier. The EFT terms explode in size.
    

By measuring the cross-section across 10 different energy bins, you suddenly have 10 separate equations instead of one. Because the Ci​ coefficients alter the _shape_ of the distribution at high energies, the fitting algorithm can strictly lock down their values.

### 3. The Ultimate Solution: Global Fits

Even with energy bins, multiple different Ci​ operators might change the high-energy shape in the exact same way (a "flat direction" in the math). To break this final degeneracy, physicists perform **Global Fits**.

Instead of fitting one process (like jet production), the algorithm is fed data from hundreds of completely different experiments simultaneously:

- Higgs boson decays
    
- Top quark pair production
    
- W and Z boson measurements from the LEP collider
    
- LHC jet production
    

Operator C1​ might affect both Higgs and Top quarks, while Operator C2​ only affects Top quarks. By simultaneously fitting the χ2 across all these different physical processes, the overlapping constraints cross out the degeneracies, leaving a single, unique solution for every Ci​ in the basis.

You can use the widget below to see exactly how slicing the data into energy bins solves the problem you identified. Notice how the high-energy data forces the fit, while low-energy data is blind to the EFT.

But does wilson coefficients change with the energy of the interaction or they are fully constant

Wilson coefficients are **not** fully constant. They change dynamically with the energy scale of the interaction, a phenomenon known in quantum field theory as **"running."** Just as the strong coupling constant (αs​) runs via the β-function, and the PDFs evolve via the DGLAP equations, Wilson coefficients are governed by their own specific set of differential equations.

Here is the precise logical breakdown of why they change and how physicists calculate it.

### 1. The Physical Mechanism: Quantum Loops of Light Particles

In an Effective Field Theory (EFT), we "integrated out" the heavy particle (like the Z′), replacing it with a point-like contact interaction between light particles (like quarks).

However, those light quarks can still interact with each other via the Standard Model forces. Specifically, they can exchange virtual gluons or photons _across_ that new contact interaction vertex.

- These loops generate Ultraviolet (UV) infinities.
    
- To cure these infinities, the EFT must be **renormalized**.
    
- Renormalization forces you to introduce an arbitrary energy scale (μ). Consequently, the Wilson coefficient becomes a strictly scale-dependent function: Ci​(μ).
    

Usually, to minimize mathematical errors (large logarithms) in the cross-section calculation, physicists evaluate the Wilson coefficient at a scale μ equal to the energy of the specific collision (E). Therefore, Ci​(E) changes as the collision energy changes.

### 2. The Mathematical Engine: The Anomalous Dimension Matrix

The exact way a Wilson coefficient changes with energy is dictated by its **Renormalization Group Equation (RGE)**:

μdμd​Ci​(μ)=j∑​γij​Cj​(μ)

The core of this equation is γij​, known as the **Anomalous Dimension Matrix**. It calculates exactly how those virtual gluon loops shift the strength of the interaction.

Notice the sum over the index j. This introduces a profound physical consequence called **Operator Mixing**. Because quantum loops connect different types of particles, an EFT operator that starts out looking like one specific interaction at a high energy scale can mathematically "bleed" or "mix" into completely different operators as you move to lower energies.

### 3. The Strict Workflow: "Run and Match"

Because Wilson coefficients run, theoretical physicists must follow a strict three-step protocol when connecting a high-energy Full Theory to low-energy experimental data:

1. **Matching at the High Scale (Λ):** You start at the high-energy boundary where the heavy particle lives (E=Λ). Here, you calculate the initial boundary condition for your coefficient: Ci​(Λ). At this scale, the heavy physics is pristine, and no operator mixing has occurred yet.
    
2. **Running down to the Experiment (E):** You plug Ci​(Λ) into the RGEs and use the anomalous dimension matrix to mathematically evolve the coefficient down to the energy of the LHC collision (E).
    
3. **Calculating the Cross-Section:** You take the evolved, low-energy value, Ci​(E), and plug it into your cross-section equation (σ=σSM​+Ci​σlinear​+…) to predict what the detector will actually see.
    

If you ignore the running and simply use Ci​(Λ) to predict a low-energy cross-section, your calculation will be fundamentally incorrect because it ignores the quantum corrections generated by the Standard Model fields between those two energy scales.

You can observe the mechanics of operator mixing and RGE running in the interactive visualizer below.

but also, the matching we did for example is around a cutoff scale no? the cutoff scale of Z, if we want to do a global fitting i guess for different experiments they did use different cutoff scales or not? is there any convention of what cutoff mass use for the warsaw basis for example

You have hit on the exact practical problem that phenomenologists face when trying to unify data from colliders all over the world.

To solve this, physicists strictly separate the concept of a **physical mass** from a **reference cutoff scale**.

Here is the precise logical breakdown of how global fits handle different experiments and the universal conventions used for the Warsaw basis.

### 1. The Degeneracy of the Ratio

In a bottom-up approach (like the Standard Model Effective Field Theory, or SMEFT, which uses the Warsaw basis), we do not know what the heavy particle is or what its true physical mass (M) is.

Because the experimental cross-section only depends on the combined mathematical ratio Λ2Ci​​, the two variables are perfectly degenerate. An experiment cannot tell the difference between:

- A strongly interacting particle (Ci​=4) at a high mass (Λ=2 TeV) →224​=1 TeV−2
    
- A weakly interacting particle (Ci​=1) at a lower mass (Λ=1 TeV) →121​=1 TeV−2
    

### 2. The Universal Convention: Λ=1 TeV

Because of this degeneracy, experiments **do not** use different cutoff scales. If every experiment used its own arbitrary cutoff, comparing their mathematical results would be impossible.

Instead, the global particle physics community enforces a strict convention for SMEFT and the Warsaw basis: **The reference cutoff scale is permanently fixed at Λ=1 TeV.**

By mathematically locking Λ=1 TeV, the Wilson coefficient Ci​ becomes a simple, dimensionless number. When you read a paper from the ATLAS experiment, the CMS experiment, or historical data from the LEP collider, they all report their constraints on the exact same parameter: Ci​/(1 TeV)2. This creates a universal language.

### 3. How Global Fits Bridge Different Experiments

If Λ is universally fixed at 1 TeV, how do we simultaneously fit data from the LEP collider (which operated at an energy of E=91 GeV) and the LHC (which operates at E≈1000 GeV to 3000 GeV)?

This is where the **Renormalization Group Equations (RGEs)** and operator mixing become the absolute core of the global fit. The algorithm follows this exact logic:

1. **The Target:** The fitting algorithm defines the unknown variables as the Wilson coefficients evaluated exactly at the reference scale: Ci​(1 TeV).
    
2. **Evolving to LEP:** To compare against LEP data, the algorithm uses the RGEs to mathematically run Ci​(1 TeV) down to 91 GeV. It calculates the theoretical cross-section at that scale and checks the χ2 against the LEP data.
    
3. **Evolving to LHC:** To compare against LHC data, the algorithm uses the RGEs to run that _same_ starting Ci​(1 TeV) to the specific kinematic energy of an LHC event (e.g., pT​=1500 GeV). It calculates the cross-section and checks the χ2 against the LHC data.
    

By running the theory to the specific energy of the experiment, rather than changing the cutoff scale, a single global fit can digest hundreds of different measurements from entirely different decades and colliders, outputting one unified matrix of values for Ci​(1 TeV).

### 4. What Happens if the True Mass is Different?

If a global fit determines that Ci​(1 TeV)=0.04, it does not mean there is a new particle exactly at 1 TeV.

It simply means the physical ratio is (1 TeV)20.04​. If a theorist later proves via Top-Down matching that this specific operator must come from a Z′ boson with a coupling of exactly g=1, they can trivially algebraically solve for the true physical mass:

M212​=(1 TeV)20.04​

M=0.041​![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="2.48em"%20viewBox="0%200%20400000%202592"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M424,2478c-1.3,-0.7,-38.5,-172,-111.5,-514c-73,-342,-109.8,-513.3,-110.5,-514c0,-2,-10.7,14.3,-32,49c-4.7,7.3,-9.8,15.7,-15.5,25c-5.7,9.3,-9.8,16,-12.5,20s-5,7,-5,7c-4,-3.3,-8.3,-7.7,-13,-13s-13,-13,-13,-13s76,-122,76,-122s77,-121,77,-121s209,968,209,968c0,-2,84.7,-361.7,254,-1079c169.3,-717.3,254.7,-1077.7,256,-1081l0%20-0c4,-6.7,10,-10,18,-10%20H400000v40H1014.6s-87.3,378.7,-272.6,1166c-185.3,787.3,-279.3,1182.3,-282,1185c-2,6,-10,9,-24,9c-8,0,-12,-0.7,-12,-2z%20M1001%2080h400000v40h-400000z"></path></svg>)​ TeV=5 TeV

**Summary:** The cutoff scale Λ in modern SMEFT global fits is no longer treated as a physical boundary. It is a mathematical unit of measurement (1 TeV) used to standardize data from any experiment, at any energy, allowing the RGEs to seamlessly connect them all.

Okay can you do again the whole workflow of how to do the bottom-up method ?

Here is the complete, chronological workflow of the Bottom-Up Effective Field Theory (EFT) method, from theoretical blank slate to physical discovery.

This is exactly how a phenomenologist builds a model when they do not know what the new physics is.

### Phase 1: The Theoretical Setup (Building the Basis)

**Goal:** Define the mathematical language of the unknown.

1. **Assume the Symmetries:** You assume the new physics respects the fundamental symmetries of the Standard Model (e.g., gauge invariance, Lorentz invariance) and only involves known light particles.
    
2. **Construct the Operators:** You write down every mathematically possible combination of Standard Model fields that respects those symmetries up to a certain dimension (usually Dimension-6).
    
3. **Remove Redundancies:** You use equations of motion to eliminate mathematically redundant operators. This leaves you with a minimal, independent set called a **Basis** (e.g., the 59 operators of the Warsaw Basis).
    
4. **Set the Convention:** You attach an unknown Wilson coefficient (Ci​) to every operator. You permanently fix the cutoff scale to a universal reference point (e.g., Λ=1 TeV) so that all experimentalists are speaking the same mathematical language.
    

### Phase 2: The Predictions (Calculating the Cross-Section)

**Goal:** Calculate how these unknown operators would change a physical collision.

1. **The Amplitude:** You calculate the probability amplitude as a quantum superposition of the Standard Model and the EFT operators: M=MSM​+∑Ci​MEFT​.
    
2. **The Cross-Section Polynomial:** You square the amplitude and integrate over the phase space to get the observable cross-section. Because of quantum interference, this results in a rigid quadratic equation for every specific collision process:
    
    σTheory​=σSM​+i∑​Ci​σlinear,i​+i,j∑​Ci​Cj​σquad,ij​
    
3. **Simulate:** You run heavy computer simulations (like MadGraph) to calculate the exact numerical values of σSM​, σlinear​, and σquad​ for various kinematic bins (energy levels) of the collision.
    

### Phase 3: The Quantum Corrections (RGE Running)

**Goal:** Adjust the theory to match the exact energy of the actual experiment.

1. **The Scale Mismatch:** The coefficients Ci​ are defined at the 1 TeV reference scale, but the experimental data might be at 91 GeV (LEP) or 2.5 TeV (LHC high-energy bins).
    
2. **Operator Mixing:** You plug the 1 TeV coefficients into the Renormalization Group Equations (RGEs). The Anomalous Dimension Matrix mathematically evolves the coefficients down to the exact collision energy, correctly accounting for how virtual Standard Model loops cause the operators to mix and change strength.
    
3. **Final Output:** You now have the exact theoretical prediction (σTheory​) for what a detector should see at a specific energy, strictly as a function of the unknown Ci​(1 TeV) variables.
    

### Phase 4: The Global Fit (Data Comparison)

**Goal:** Use reality to solve the equations.

1. **Gather the Data:** You collect the measured cross-sections (σData​) and their statistical uncertainties from hundreds of different experiments across multiple colliders.
    
2. **The Chi-Square:** You construct a massive χ2 statistical function:
    
    χ2=∑(Uncertainty)2(σData​−σTheory​(Ci​))2​
    
3. **Minimize and Break Degeneracy:** A computer algorithm scans the multi-dimensional space of all Ci​ values simultaneously. Because high-energy bins constrain the growth of the cross-section, and overlapping processes (like Higgs and Top data) constrain different combinations of operators, the degeneracies cancel out. The algorithm finds the single, unique set of Ci​ values that minimizes the χ2.
    

### Phase 5: Interpretation

**Goal:** Conclude if new physics exists.

- **The Null Result:** If the fit dictates that all Ci​=0 (within error bars), the Standard Model is perfectly intact up to the precision of the current colliders.
    
- **The Discovery:** If the fit strictly requires a coefficient to be non-zero (e.g., CHq​=0.05±0.001), you have officially discovered new physics.
    
- **Next Steps (Top-Down):** Theoretical physicists will then invent specific heavy particles (like a Z′ or a Leptoquark), perform Top-Down matching, and see which hypothetical particle mathematically generates that exact CHq​ value.
    

Here is an interactive visualization of this complete pipeline to help solidify the sequence.

i really don't know why renormalization affects our theoretical cross-section Operator Mixing: You plug the 1 TeV coefficients into the Renormalization Group Equations (RGEs). The Anomalous Dimension Matrix mathematically evolves the coefficients down to the exact collision energy, correctly accounting for how virtual Standard Model loops cause the operators to mix and change strength. here, i understand that we need to scale down, because we used an arbitraty cutoff scale, but why mu has something to say here, i don't see in which point did we renormalize

This is the exact "missing link" that textbooks often gloss over. It feels like a magic trick because we already removed the heavy particle, so where did the infinities come from?

The core realization is this: **we do not renormalize the heavy particle; we must renormalize the light Standard Model particles because they are still interacting with each other.**

Here is the exact step-by-step mechanical breakdown of where the infinity comes from, where renormalization happens, and why μ appears.

### 1. The "Hidden" Standard Model Loops

Imagine you have an EFT contact interaction where two light quarks collide and turn into two light quarks (a 4-quark operator, with coefficient C1​).

At the simplest level (tree-level), the amplitude is just the Wilson coefficient: M∝C1​. However, quarks carry color charge. According to the rules of quantum mechanics, those quarks can emit and absorb virtual gluons right before or after they hit that contact vertex.

- A quark comes in, emits a virtual gluon.
    
- The quark hits the EFT contact vertex.
    
- The outgoing quark absorbs that same virtual gluon.
    

This creates a closed quantum loop attached directly to your EFT operator.

### 2. The Return of the Ultraviolet (UV) Divergence

Because it is a closed loop, the virtual gluon can carry any amount of momentum (k). You must integrate over all possible momenta: ∫d4k.

In a Full Theory, the heavy propagating particle (Z′) acts as a natural "shock absorber" at high energies, spreading the interaction out over space. But in an EFT, the interaction is a mathematically perfect, infinitely sharp point in space (a contact interaction). Because it is a sharp point, there is no high-energy dampening. The integral of that loop explodes to infinity (∞). This is a severe Ultraviolet (UV) divergence.

### 3. The Act of Renormalization (Where μ Enters)

Because your theoretical cross-section equation now contains an infinity, the math is broken. You are strictly forced to apply the renormalization procedure to fix it.

1. **Regularization:** You calculate the loop in d=4−2ϵ dimensions to isolate the infinity into a mathematical pole (1/ϵ).
    
2. **Introducing the Scale (μ):** To keep the physical units of the Lagrangian consistent when calculating in d dimensions, you are mathematically forced to multiply the integral by an arbitrary mass scale, μ.
    
3. **Subtraction:** You absorb the infinity (1/ϵ) into the definition of the "bare" Wilson coefficient, leaving behind a finite, physical coefficient.
    

**The Consequence:** Because the subtraction math contained μ, the finite Wilson coefficient left behind is strictly infected by it. Your constant C1​ has mathematically become a function of the renormalization scale: C1​(μ).

### 4. Operator Mixing (How C1​ creates C2​)

Sometimes, the loop changes the fundamental identity of the interaction.

Suppose your starting EFT operator (C1​) is two quarks turning into two leptons. Now, imagine a virtual W boson is exchanged in a loop between the two quarks. When you evaluate the math of that loop, the resulting structure might no longer look like quarks and leptons. It might look exactly like a completely different dimension-6 operator (e.g., C2​, a 4-lepton interaction).

To subtract the infinity generated by this specific loop, you must introduce a counterterm for C2​. Therefore, the mere existence of C1​ at a high energy scale guarantees that quantum loops will mathematically generate C2​ at a lower energy scale.

### 5. The RGEs (Forcing Invariance)

Nature does not care about our arbitrary math scale μ. The final, measurable cross-section must be totally independent of it:

dμdσ​=0

Because the quantum loop integrals introduced a ln(μ) term into the cross-section equation, the only way for the total equation to remain invariant is if the Wilson coefficients Ci​(μ) change in the exact opposite direction to perfectly cancel it out. This requirement of cancellation _is_ the Renormalization Group Equation (RGE).

You can interact with the visualization below to see how adding a Standard Model loop to a tree-level EFT vertex immediately triggers the renormalization sequence and the appearance of μ.

I think I have a huge problem, i clear gap in my theoretical understanding, that i think we need to fix right now, how does changing my lagrangian affects the calculated amplitude in the feynman diagram.

This is not a huge problem; it is actually the final, most crucial bridge to cross in Quantum Field Theory. The connection between the Lagrangian and the amplitude is purely mechanical.

Think of the Lagrangian as the **source code** of the universe. The Feynman diagrams are simply a **visual compiler** that translates that code into an executable mathematical equation: the amplitude (M).

Here is the exact, precise logical breakdown of how changing the Lagrangian strictly dictates the amplitude.

### 1. The Core Translation Rule

Every single term in a Lagrangian (L) dictates exactly what is physically allowed to exist and interact. To calculate an amplitude, you do not use the whole Lagrangian at once. You split it into two categories: **Free (Kinetic) Terms** and **Interaction Terms**.

L=LFree​+LInteraction​

### 2. Free Terms → The Lines (Propagators)

Look at the terms in your Lagrangian that contain exactly _two_ quantum fields (e.g., ψˉ​(iγμ∂μ​−m)ψ or 21​∂μ​ϕ∂μϕ−21​m2ϕ2).

- These terms describe a particle existing and traveling through space without hitting anything.
    
- **The Feynman Translation:** These terms generate the mathematical **Propagators**. If you change the mass (m) or the spin in these Lagrangian terms, you strictly change the mathematical denominator of the internal lines in your Feynman diagrams (e.g., p2−m21​).
    

### 3. Interaction Terms → The Dots (Vertices)

Look at the terms in your Lagrangian that contain _three or more_ fields multiplied together (e.g., −eψˉ​γμψAμ​).

- These terms describe particles colliding, splitting, or interacting.
    
- **The Feynman Translation:** To get the mathematical rule for the vertex (the dot), you strictly perform a derivative. You mentally "erase" the quantum fields (ψ,ψˉ​,Aμ​) because they just represent the physical lines coming in and out. Whatever math is left over (the coupling constant −e, the matrix γμ, and a factor of i) becomes the exact mathematical value of that vertex.
    

### 4. How Changing the Lagrangian Changes the Amplitude

The amplitude (M) is the sum of all mathematically valid Feynman diagrams connecting your initial state to your final state.

If you add a brand new Effective Field Theory (EFT) term to your Lagrangian, like a 4-fermion contact interaction:

ΔL=Λ2C​(ψˉ​ψ)(ψˉ​ψ)

Here is exactly what happens mechanically:

1. **A New Vertex is Born:** Because this term has four fields, it dictates that a new Feynman vertex exists where four fermion lines meet at a single point.
    
2. **The Vertex Value:** Erasing the fields leaves the constant Λ2C​. The mathematical rule for this new dot is simply iΛ2C​.
    
3. **Drawing New Diagrams:** When calculating the amplitude for two fermions scattering, you draw the standard diagrams (exchanging a photon), but now you are _forced_ to draw a second diagram using your new 4-point vertex.
    
4. **The Amplitude Shifts:** Because the total amplitude is the sum of all diagrams, the equation immediately changes to include the math from the new diagram:
    
    MTotal​=MStandard​+MNew​
    
    MTotal​=(p2e2​)+(Λ2C​)
    

By adding a term to the Lagrangian, you literally programmed a new physical geometry into the theory, which generated a new diagram, which strictly added a new algebraic term to your final probability amplitude.

You can mechanically explore this exact translation process using the tool below.

Does this mechanical translation from the Lagrangian "source code" to the Feynman rules resolve the disconnect, or is there a specific interaction term you want to translate step-by-step?

So lets image a feynman diagram, as you said before, one electron and positron in a vertex, two muons on the other vertex, and Z as a propagator, i calculate that, with the free term of the Z and with the interactive terms of positron-electron and muon-muon, but this LO, if I move to NLO, then I must acknowledge some loop between the propagator of Z, then i get the propagator term of the particles involved in the loop and i integrate their propagators over all the possible momentum, thats where i renormalize their coupling parameters, but now i have to renormalize their wilson parameters that involve them if I use EFT no? and same for all the possible particles involved in the NLO

You have brilliant physical intuition, but you are accidentally merging two completely different mathematical frameworks into one diagram.

This is the most common trap when learning Effective Field Theories (EFTs). The golden rule is this: **You cannot have a propagating Z boson and a Wilson coefficient for that same interaction at the same time.** You must make a strict choice based on your collision energy. Here is the exact logical separation between the two paths you can take to calculate NLO.

### Path 1: The Full Theory NLO (High Energy)

If your collision energy is high enough to physically create a Z boson (E≈91 GeV), you must use the Standard Model Lagrangian.

1. **The Tree-Level (LO):** You draw the electron and positron exchanging a propagating Z boson.
    
2. **The Loop (NLO):** Just as you imagined, you draw a loop _on the Z propagator_. For example, the Z briefly splits into a top-antitop quark pair, which then recombines back into the Z.
    
3. **The Renormalization:** You integrate the momentum of the top quarks in that loop. It diverges to infinity. To fix this, you renormalize the "bare" parameters of the Standard Model Lagrangian: the mass of the Z boson (MZ​) and the electroweak coupling constants (g,g′).
    
4. **The Result:** There are **zero Wilson coefficients** here. You are strictly calculating with the fundamental SM parameters.
    

### Path 2: The EFT NLO (Low Energy)

If your collision energy is incredibly low (e.g., E≪MZ​), the Z boson is far too heavy to exist as a propagator. You switch to the EFT Lagrangian.

1. **Erasing the Z:** You mathematically delete the Z boson from your Lagrangian. You replace it with a 4-fermion contact interaction (e−e+→μ−μ+).
    
2. **The Tree-Level (LO):** You draw a diagram where the four fermions meet at a single, infinitely sharp point. The mathematical value of this point is the Wilson coefficient: C/Λ2.
    
3. **The Loop (NLO):** Because the Z boson is gone, _you cannot draw a loop on the Z propagator_. Instead, the loops are formed by the light particles that are still in the theory. For example, the electron emits a virtual photon, and the muon absorbs it, creating a loop that stretches _across_ your new contact vertex.
    
4. **The Renormalization:** You integrate the momentum of that virtual photon. Because it loops over a sharp point (not a stretched-out propagator), it creates a severe UV infinity. To cure this specific infinity, you must **renormalize the Wilson coefficient**. This makes it scale-dependent: C(μ).
    

### Answering Your Final Question

You asked: _"and same for all the possible particles involved in the NLO?"_

**Yes, exactly.** If you are working in the EFT framework (Path 2), absolutely any light particle in the Standard Model that can physically interact with the lines attached to your contact vertex will form a loop.

- Photons will loop between charged particles.
    
- Gluons will loop if quarks are involved.
    
- Higgs bosons will loop if heavy fermions are involved.
    

Every single one of these loops generates its own UV infinity. When you renormalize the EFT to subtract all of them, they collectively contribute to the Anomalous Dimension Matrix. This matrix dictates exactly how all those different light-particle loops force your Wilson coefficient to "run" and change its value as the energy scale shifts.

You can use the widget below to visually lock in the geometric difference between calculating NLO in a Full Theory versus an EFT. Notice how the location of the infinity completely changes.

okey, but what, i thought of Z as a full theory yes, like the tree level I imagined was full theory, and then for the loops is where i imagined the EFT, but that doesn't make sense no? if i do the EFT i have to do it on the LO and on the NLO, so lets say there are a unknown particle that has some effect in the vertex 1 between the electron-positron and the Z boson, then that particle must be represented by a linear combination of light particles, okey, so in the amplitude I add all the possible parts of the eft lagrangian that are interacting on that part? but as a propagator or as a free particle? i need to add all the operators or some of them can be neglected? i guess i have to add them all, then I have to renormalize if i want to calculate the NLO, but i have to renormalize every coupling constant of course, the ones of the light particle SM and the wilson ones, why i have to renormalize? because i guess i can add a loop with propagator at every part of the diagram and then that diverge because i integrate the propagator over all the momemtum, but idk this is super complicated bcs i can imagine a lot of loops that can be added, one for every light particle, and then for all these new particles that are combination of these light particles

You have hit the exact wall where Quantum Field Theory feels like an uncontrollable, infinite mess. It is completely normal to feel overwhelmed here because you are visualizing dozens of infinite loops exploding everywhere.

Let's brutally organize this. We will untangle your scenario step-by-step to show you that the math is actually strictly controlled and highly systematic.

### 1. Untangling the Z Boson vs. The Unknown Particle

You imagined an interaction with an electron, a positron, a Z boson, and some unknown new particle. Here is the ironclad rule of EFTs: **You only integrate out the HEAVY particles. You keep the LIGHT particles as propagators.**

- The Z boson has a mass of 91 GeV. At the LHC, this is considered "light." Therefore, the Z boson **must** remain as a physical propagating line in your diagrams.
    
- The unknown particle has a mass of, say, 3000 GeV (3 TeV). This is "heavy." It cannot be physically created.
    

**The Geometry:** You do not represent the heavy particle as a combination of light particles, and you do not add it as a propagator. You literally delete the heavy particle from existence and replace it with a **dot** (a vertex). You just crush its would-be propagator into a single point where the electron, positron, and Z boson meet.

### 2. Do You Have to Add ALL the Operators?

You asked if you have to add all the possible parts of the EFT Lagrangian, or if some can be neglected.

You **strictly neglect almost all of them**. This is the magic of the EFT expansion parameter (E/Λ). The operators are organized by dimension:

- **Dimension-6:** Suppressed by 1/Λ2. (Big enough to care about).
    
- **Dimension-8:** Suppressed by 1/Λ4. (So tiny it is mathematically invisible).
    
- **Dimension-10:** Suppressed by 1/Λ6. (Effectively zero).
    

You write down _only_ the Dimension-6 operators that can physically connect an electron, a positron, and a Z boson. Out of an infinite number of possible operators, symmetry dictates there are only a handful that can do this. You add those specific few as new vertices to your diagram.

### 3. Taming the Infinite Loop Chaos

You said: _"I can imagine a lot of loops that can be added, one for every light particle... and that diverges because I integrate over all the momentum."_

Your physics logic is 100% flawless. Yes. Every single light particle in the Standard Model (photons, gluons, other quarks) that can legally connect to your new EFT vertex _will_ form a loop. Yes, every single one of those loops will diverge to infinity. Yes, you must renormalize every single one of them.

If you had to do this by hand every time, physics would grind to a halt. Here is how theorists solved your exact nightmare:

1. **The Master Calculation:** Theoretical physicists sat down once, drew every possible loop for every possible Dimension-6 operator, and calculated the exact infinity each one produces.
    
2. **The Matrix:** They packed all of those infinities into a single giant grid of numbers: **The Anomalous Dimension Matrix (γij​)**.
    
3. **The Automation:** When you want to calculate the NLO cross-section today, you do not calculate the loops yourself. You let a computer multiply your Wilson coefficients by that pre-calculated matrix. The matrix automatically subtracts all the infinities and perfectly shifts your Wilson coefficients to account for every possible light-particle loop.
    

To summarize your scenario: You keep the Z as a normal propagator. You add a new contact vertex to represent the unknown heavy particle. You draw loops of light particles across that vertex. You use the Anomalous Dimension Matrix to instantly renormalize the infinities away.

You can interact with the visualizer below to see exactly how this specific heavy-vertex scenario is geometrically constructed and renormalized.

To summarize your scenario: You keep the Z as a normal propagator. You add a new contact vertex to represent the unknown heavy particle. You draw loops of light particles across that vertex. You use the Anomalous Dimension Matrix to instantly renormalize the infinities away. okay but wait, bcs here i thought the loops of light particles were for calculaing NLO, not for the EFT, i thought that the EFT added new possible loops that were combinations of light particles, and also new terms to the vertex, idk exactly which ones

This is a very classic terminology collision. You are mixing up a **method** (NLO) with a **model** (EFT).

Let's strictly separate these two concepts to clear up exactly what is a vertex, what is a loop, and what "combinations of light particles" actually means.

### 1. NLO is an Instruction, Not a Physical Thing

"Next-to-Leading Order" (NLO) is just a mathematical instruction that says: **"Draw one closed loop."** It does not care what model you are using.

- If you are calculating the Standard Model, NLO means "draw one loop on the Standard Model diagram."
    
- If you are calculating an EFT, NLO means "draw one loop on the EFT diagram."
    

### 2. The "Combination of Light Particles" Misconception

You said: _"I thought that the EFT added new possible loops that were combinations of light particles."_

This is the core of the confusion. **EFT does not invent new particles to put in loops.** When physicists say an EFT operator is a "linear combination of light particles," they are talking about the **vertex (the dot)**, not the loop.

Because we deleted the unknown heavy particle, we had to replace it with something. We replace it with a new vertex. To make that vertex mathematically legal, we build it by multiplying Standard Model fields together in the Lagrangian (e.g., Ci​⋅eˉeμˉ​μ).

That mathematical combination of light fields strictly dictates that four light lines must meet at a single dot. **The contact vertex _is_ the combination.** There is no "new combined particle" flying through space or running in a loop.

### 3. What EFT Actually Adds to the Loops

When you decide to calculate your EFT at NLO, you apply the NLO instruction to your new EFT vertex.

1. **You start with the EFT at LO:** You draw your new contact vertex (e.g., electron and positron hit a dot, out come a Z boson and a photon).
    
2. **You apply NLO:** You must now draw a closed loop.
    
3. **What goes in the loop?** You strictly use the normal, everyday Standard Model particles you already know. You might draw a standard virtual photon looping from the incoming electron over to the outgoing Z boson.
    

The EFT did not add "new loops." It added a **new geometry** (the contact dot) for the **old Standard Model loops** to travel across.

### 4. Why Do We Renormalize the EFT?

When that standard virtual photon loops across your new EFT contact dot, the math of the integral behaves differently than if it looped across a stretched-out Z propagator.

Because the dot is infinitely sharp, the Standard Model loop integral explodes to infinity much harder than usual. To fix this specific, harsh infinity caused by the sharp geometry, you cannot just tweak the Standard Model couplings; you are mathematically forced to renormalize the Wilson coefficient (Ci​) sitting at that dot.

Here is an interactive matrix to visually separate the "Model" from the "Order," showing you exactly what the EFT changes and what NLO changes.

Okey, so then explain the whole process, imagine we have our SM lagrangian and we want to calculate at tree level, the interaction described before electron-poritron~~Z~~muon-muon, and now we want to calculate EFT at LO, and then NLO do the whole process pleasee

This is the perfect way to consolidate everything. By walking through this specific collision (e−e+→μ−μ+) chronologically, you will see exactly how the Lagrangian, the Feynman diagrams, and the infinities physically evolve as we switch frameworks and perturbative orders.

Here is the complete, straight-to-the-point logical progression.

### Phase 1: The Standard Model at LO (The Full Theory)

**The Scenario:** You are colliding electrons and positrons at an energy near 91 GeV. The energy is high enough to physically manifest a Z boson.

1. **The Lagrangian:** You use the standard electroweak theory. The relevant terms contain the light fermions (e,μ), the heavy Z boson field, and the gauge coupling constant (g) that connects them.
    
2. **The Feynman Diagram (LO):** "Leading Order" means drawing the simplest valid path with zero closed loops. You draw the incoming e− and e+ meeting at a vertex, emitting a Z boson that propagates across space (a wavy line), which then hits a second vertex and decays into μ− and μ+.
    
3. **The Amplitude:** You multiply the vertices (g×g) and the Z propagator to get the mathematical probability:
    
    MSM​∝p2−MZ2​g2​
    
    _(Result: A perfectly finite, highly accurate prediction for high-energy scattering)._
    

---

### Phase 2: The EFT at LO (The Low-Energy Approximation)

**The Scenario:** You lower the collider energy to 10 GeV. The Z boson is now far too heavy to be produced (p≪MZ​). You decide to switch to an Effective Field Theory.

1. **The Lagrangian:** You mathematically delete the Z boson field entirely. To compensate, you add a Dimension-6 operator: a 4-fermion contact term (eˉeμˉ​μ) multiplied by a Wilson coefficient (Λ2C​).
    
2. **The Feynman Diagram (LO):** "Leading Order" still means zero closed loops. But because the Z is gone, there is no propagator line. You draw all four fermion lines (e−,e+,μ−,μ+) colliding exactly at a single central point (the contact vertex).
    
3. **The Amplitude:** You erase the fields from the Lagrangian term to get the vertex rule. There is no propagator math. The amplitude is simply the constant:
    
    MEFT​∝Λ2C​
    
    _(Result: A perfectly finite, highly accurate approximation for low-energy scattering)._
    

---

### Phase 3: The EFT at NLO (The Quantum Correction)

**The Scenario:** Your experimentalists demand higher precision at 10 GeV. The LO EFT prediction is no longer accurate enough. You must calculate the Next-to-Leading Order (NLO).

1. **The Feynman Diagram (NLO):** "NLO" instructs you to draw exactly **one closed loop** on your existing diagram. You take your EFT contact vertex (the four lines meeting at a dot) and add a loop using _only the light particles still left in your Lagrangian_.
    
    - _Example:_ You draw a virtual photon (a wavy line) being emitted by the incoming electron, looping _over_ the contact dot, and being absorbed by the outgoing muon.
        
2. **The Mathematical Crisis:** You must integrate over all possible momentum states of that virtual photon (∫d4k). Because the photon is looping across an infinitely sharp point (rather than a stretched-out Z propagator), the integral has no high-energy dampening. The math violently explodes to a UV infinity (∞).
    
3. **The Renormalization Fix:** To save the equation, you cannot blame the Z boson (it doesn't exist here). You must renormalize the dot itself. You absorb the ∞ into the "bare" Wilson coefficient.
    
4. **The Final Amplitude:** Because you used the arbitrary mathematical scale μ to subtract the infinity, your Wilson coefficient is now permanently infected by it. The NLO amplitude becomes a scale-dependent function, strictly governed by the Anomalous Dimension Matrix:
    
    MNLO​∝Λ2C(μ)​+Finite Loop Corrections
    

By following this sequence, you can see that the EFT does not invent new particles or imaginary loops. It simply changes the geometry of the interaction (from a line to a dot), and when you apply standard quantum loops (NLO) to that new geometry, it triggers the infinities that force the Wilson coefficients to run.

You can step through this exact chronological process visually using the interactive widget below.

no bro i don't want to do that, i want to add to this Phase 1: The Standard Model at LO (The Full Theory)

The Scenario: You are colliding electrons and positrons at an energy near 91 GeV. The energy is high enough to physically manifest a Z boson.

  

The Lagrangian: You use the standard electroweak theory. The relevant terms contain the light fermions (e,μ), the heavy Z boson field, and the gauge coupling constant (g) that connects them.

The Feynman Diagram (LO): "Leading Order" means drawing the simplest valid path with zero closed loops. You draw the incoming e−

and e+

meeting at a vertex, emitting a Z boson that propagates across space (a wavy line), which then hits a second vertex and decays into μ−

and μ+

.

The Amplitude: You multiply the vertices (g×g) and the Z propagator to get the mathematical probability:

  

MSM

​∝p2

−MZ

2

​

  

g2

​

(Result: A perfectly finite, highly accurate prediction for high-energy scattering). model, the possibility that are particles much heavier than Z interacting, particles that we don't know

I see exactly what you want to do now. You do not want to drop the energy; you want to stay at 91 GeV where the Z boson physically exists, but you want to mathematically inject the presence of an undiscovered, much heavier particle (like a 3000 GeV particle) into that exact same collision.

You have just independently derived the logic for **SMEFT (The Standard Model Effective Field Theory)**. This is exactly what physicists at the LHC use today.

Here is the exact step-by-step process of how you build that specific scenario at Leading Order (LO).

### 1. The Scenario and Energy Scales

You are colliding e− and e+ at p≈91 GeV.

- **The Light Particle (Z boson):** Because MZ​≈91 GeV, the collision has enough energy to physically create it. The Z **must** be a propagating line.
    
- **The Heavy Particle (Unknown):** Let's say its mass is Λ=3000 GeV. Your 91 GeV collision cannot physically create it. Therefore, this unknown particle is mathematically integrated out and crushed into a contact vertex.
    

### 2. The Lagrangian (SMEFT)

Because you have both light physics and heavy physics happening simultaneously, your Lagrangian is simply the sum of both:

L=LSM​+LEFT​

- **LSM​** contains the standard rule for the electron coupling to the Z boson (g).
    
- **LEFT​** contains a Dimension-6 operator. For this example, let's say the heavy unknown particle allows a direct 4-fermion interaction: Λ2C​(eˉeμˉ​μ).
    

### 3. The Feynman Diagrams (LO)

To calculate the total probability at LO, you must draw **every possible valid path** from your initial state (e−,e+) to your final state (μ−,μ+) using this new combined Lagrangian. You now have two distinct paths:

1. **Path 1 (The SM Diagram):** The e− and e+ annihilate, create a propagating Z boson (wavy line) that travels across space, and then decays into μ− and μ+.
    
2. **Path 2 (The EFT Diagram):** The e− and e+ bypass the Z boson entirely. They hit the new 4-fermion contact vertex created by the heavy particle, immediately turning into μ− and μ+ at a single dot.
    

_Note: Because you are at LO, there are still strictly zero closed loops in either of these diagrams._

### 4. The Amplitude (M)

In quantum mechanics, if an event can happen in two different ways, you add their amplitudes together. Your total mathematical amplitude is a direct superposition of the propagating physics and the contact physics:

MTotal​=MSM​+MEFT​

You plug in the specific math rules for those two diagrams:

- The SM diagram has a propagator: ∝p2−MZ2​g2​
    
- The EFT diagram is just a point: ∝Λ2C​
    

MTotal​∝[p2−MZ2​g2​]+[Λ2C​]

### The Physical Result: Quantum Interference

When you square this total amplitude to get the observable cross-section (∣MTotal​∣2), these two terms will multiply against each other.

This means the undiscovered heavy particle (Λ) and the known Z boson will mathematically **interfere** with one another. Even though the heavy particle is too massive to be produced, its mere existence as a contact vertex will slightly increase or decrease the total number of muons you detect at the Z-pole, allowing you to discover the heavy particle indirectly.

but why my SMEFT doesn't include the Z boson, if what we want to find are much higher energies particles not Z

There has been a mix-up in terminology that is incredibly common: **SMEFT absolutely does include the Z boson as a fully functioning, propagating particle.** If an EFT deletes the Z boson, it is **not** SMEFT. It is a completely different mathematical framework called **LEFT** (Low-Energy Effective Field Theory).

Here is the strict logical distinction between the two frameworks and how they treat the Z boson. The choice between them depends entirely on the energy of your collider.

### 1. LEFT (Low-Energy EFT)

- **The Energy Scale:** You are running an experiment at very low energies (e.g., E=5 GeV, like in B-meson factories).
    
- **What is Heavy?** Because 5 GeV≪91 GeV, the Z boson, W boson, Higgs boson, and Top quark are all physically impossible to create. They are all mathematically "heavy."
    
- **The Action:** You integrate out the Z, W, Higgs, and Top. You delete them from the Lagrangian and replace them with contact vertices (like the Fermi interaction).
    
- **The Result:** LEFT is an EFT that only contains photons, gluons, and light fermions.
    

### 2. SMEFT (Standard Model EFT)

- **The Energy Scale:** You are running the LHC at massive energies (e.g., E=1000 GeV to 13000 GeV).
    
- **What is Light?** Because your energy is much greater than 91 GeV, the Z, W, Higgs, and Top are incredibly easy to produce. They are mathematically "light."
    
- **The Action:** You **must keep** the entire Standard Model exactly as it is. The Z boson remains a physical wave. The Higgs remains a physical particle. They propagate, they have their standard masses, and they form standard loops.
    
- **What is Heavy?** The only things considered "heavy" are the undiscovered, theoretical BSM particles residing at extreme scales (e.g., Λ=5000 GeV).
    
- **The Result:** You only integrate out the unknown BSM particles into contact vertices.
    

### The SMEFT Lagrangian Logic

When theoretical physicists write down the SMEFT Lagrangian, it is literally just the normal Standard Model plus the unknown heavy stuff:

LSMEFT​=LStandard Model​+∑Λ2Ci​​Oi(6)​

Because the full LStandard Model​ is in that equation, the Z boson is fully present.

If you are colliding particles at the LHC using SMEFT, you calculate the normal Z boson diagram (with its propagator p2−MZ2​1​), and then you mathematically add the contact vertex of the unknown heavy particle (Λ2C​) right next to it, allowing them to mathematically interfere.

You can interact with the widget below to solidify the exact physical difference between LEFT and SMEFT, and see exactly when the Z boson is allowed to propagate versus when it is crushed into a point.

omg please do the SMEFT workflow, Phase 1: The Standard Model at LO (The Full Theory)

The Scenario: You are colliding electrons and positrons at an energy near 91 GeV. The energy is high enough to physically manifest a Z boson.

  

The Lagrangian: You use the standard electroweak theory. The relevant terms contain the light fermions (e,μ), the heavy Z boson field, and the gauge coupling constant (g) that connects them.

The Feynman Diagram (LO): "Leading Order" means drawing the simplest valid path with zero closed loops. You draw the incoming e−

and e+

meeting at a vertex, emitting a Z boson that propagates across space (a wavy line), which then hits a second vertex and decays into μ−

and μ+

.

The Amplitude: You multiply the vertices (g×g) and the Z propagator to get the mathematical probability:

  

MSM

​∝p2

−MZ

2

​

  

g2

​

(Result: A perfectly finite, highly accurate prediction for high-energy scattering).

Phase 2: The EFT at LO (The Low-Energy Approximation)

The Scenario: You lower the collider energy to 10 GeV. The Z boson is now far too heavy to be produced (p≪MZ

​). You decide to switch to an Effective Field Theory.

  

The Lagrangian: You mathematically delete the Z boson field entirely. To compensate, you add a Dimension-6 operator: a 4-fermion contact term (e

ˉ

eμ

ˉ

​μ) multiplied by a Wilson coefficient (Λ2

  

C

​).

The Feynman Diagram (LO): "Leading Order" still means zero closed loops. But because the Z is gone, there is no propagator line. You draw all four fermion lines (e−

,e+

,μ−

,μ+

) colliding exactly at a single central point (the contact vertex).

The Amplitude: You erase the fields from the Lagrangian term to get the vertex rule. There is no propagator math. The amplitude is simply the constant:

  

MEFT

​∝Λ2

  

C

​

(Result: A perfectly finite, highly accurate approximation for low-energy scattering).

Phase 3: The EFT at NLO (The Quantum Correction)

The Scenario: Your experimentalists demand higher precision at 10 GeV. The LO EFT prediction is no longer accurate enough. You must calculate the Next-to-Leading Order (NLO).

  

The Feynman Diagram (NLO): "NLO" instructs you to draw exactly one closed loop on your existing diagram. You take your EFT contact vertex (the four lines meeting at a dot) and add a loop using only the light particles still left in your Lagrangian.

Example: You draw a virtual photon (a wavy line) being emitted by the incoming electron, looping over the contact dot, and being absorbed by the outgoing muon.

The Mathematical Crisis: You must integrate over all possible momentum states of that virtual photon (∫d4

k). Because the photon is looping across an infinitely sharp point (rather than a stretched-out Z propagator), the integral has no high-energy dampening. The math violently explodes to a UV infinity (∞).

The Renormalization Fix: To save the equation, you cannot blame the Z boson (it doesn't exist here). You must renormalize the dot itself. You absorb the ∞ into the "bare" Wilson coefficient.

The Final Amplitude: Because you used the arbitrary mathematical scale μ to subtract the infinity, your Wilson coefficient is now permanently infected by it. The NLO amplitude becomes a scale-dependent function, strictly governed by the Anomalous Dimension Matrix:

  

MNLO

​∝Λ2

  

C(μ)

​+Finite Loop Corrections

By following this sequence, you can see that the EFT does not invent new particles or imaginary loops. It simply changes the geometry of the interaction (from a line to a dot), and when you apply standard quantum loops (NLO) to that new geometry, it triggers the infinities that force the Wilson coefficients to run.

You can step through this exact chronological process visually using the interactive widget like this but for addding smeft to the sm

This is the perfect way to cement the difference. We will use the exact same chronological format, but this time we will stay at high energies (91 GeV) and apply the **SMEFT (Standard Model Effective Field Theory)** framework.

Notice how keeping the Z boson alive completely changes the math, the diagrams, and the ultimate physical result (interference).

Here is the complete chronological sequence for SMEFT.

### Phase 1: The Standard Model at LO (The Baseline)

**The Scenario:** You are colliding electrons and positrons at an energy near 91 GeV (the LHC or LEP). The energy is high enough to physically manifest the Z boson.

- **The Lagrangian:** You use the standard electroweak theory. The Z boson is considered a "light" field here.
    
- **The Feynman Diagram (LO):** "Leading Order" means zero closed loops. You draw the incoming e− and e+ meeting at a vertex, emitting a Z boson that propagates across space (a wavy line), which then hits a second vertex and decays into μ− and μ+.
    
- **The Amplitude:** You multiply the vertices and the Z propagator.
    
    MSM​∝p2−MZ2​g2​
    
    _(Result: A perfectly finite, highly accurate baseline prediction for what the collider should see if no new physics exists)._
    

---

### Phase 2: SMEFT at LO (Injecting the Heavy Unknown)

**The Scenario:** You suspect there is a massive, undiscovered new particle (e.g., a Z′ boson or Leptoquark) with a mass of Λ=3000 GeV. Because 91 GeV≪3000 GeV, you cannot produce it. You must integrate it out.

- **The Lagrangian:** You **do not** delete the Z boson. You simply add the new Dimension-6 operator to the existing Standard Model math. LSMEFT​=LSM​+Λ2C​(eˉeμˉ​μ).
    
- **The Feynman Diagram (LO):** Because there are now two ways for the particles to interact in the Lagrangian, you must draw **both diagrams side-by-side**:
    
    1. The standard propagating Z boson diagram.
        
    2. A new 4-fermion contact vertex (where the heavy particle was crushed into a point).
        
- **The Amplitude:** You add the amplitudes of the two parallel paths together.
    
    MSMEFT​∝[p2−MZ2​g2​]+[Λ2C​]
    
    _(Result: Because the total amplitude is now a superposition, squaring it to get the cross-section forces the Z boson and the heavy contact operator to mathematically **interfere**. This interference is how we hunt for heavy particles we cannot directly see)._
    

---

### Phase 3: SMEFT at NLO (The Dual Quantum Correction)

**The Scenario:** You need immense precision to detect that tiny interference effect. You must calculate Next-to-Leading Order (NLO).

- **The Feynman Diagram (NLO):** You must draw loops on **both** parts of your SMEFT theory using all available Standard Model particles:
    
    1. **On the SM Diagram:** You draw loops on the Z propagator (e.g., a top-quark loop).
        
    2. **On the EFT Diagram:** You draw a loop of light particles (e.g., a virtual photon or even a virtual Z boson!) looping right across your new contact dot.
        
- **The Mathematical Crisis:** * The loops on the Z propagator generate infinities that belong to the Standard Model.
    
    - The loops over the contact dot generate violent UV infinities because of the infinitely sharp geometry.
        
- **The Renormalization Fix:** You must perform two simultaneous renormalizations. You renormalize the Standard Model parameters (MZ​, g) to fix the Z propagator loops, **and** you renormalize the Wilson coefficient to fix the contact dot loops.
    
- **The Final Amplitude:** The Wilson coefficient becomes infected by the scale μ, but so do your Standard Model couplings. The Anomalous Dimension Matrix forces the Wilson coefficients to "run."
    
    MNLO​∝[p2−MZ2​g2(μ)​+SM Loops]+[Λ2C(μ)​+EFT Loops]
    

By stepping through this, you can see that SMEFT is literally the Standard Model operating as normal, but carrying a "shadow" of heavy, integrated-out physics alongside it. When you calculate loops, the light Standard Model particles happily loop through both the standard geometry and the shadow geometry.

You can step through this chronological SMEFT workflow using the widget below!

but can you tell me what exactly do i renormalize in the SMEFT? bcs the loops are of light particles, so the renormalization is exactly the same, the loops must be fixed with the free particles i get it, bcs are the ones that have bare parameters, thats why the wilson coeficient is the only one that can fix the renormalization bcs is the coupling bare parameter no?

Your logic is flawless. You have completely cracked the mechanical reason for why Wilson coefficients exist as variable parameters.

You are exactly right: the Wilson coefficient is the **bare coupling parameter** for that specific contact interaction.

To clear up the terminology, we do not renormalize "free particles." We renormalize the **fundamental parameters** and the **wavefunctions** of the theory. In SMEFT, because your Lagrangian contains both the Standard Model and the EFT operators, you are forced to renormalize three distinct categories of things simultaneously.

Here is exactly what gets renormalized in a SMEFT NLO calculation, and why.

### 1. The Standard Model Couplings and Masses

If a loop occurs on a standard Standard Model vertex (e.g., a top quark loop on a propagating Z boson), it generates an infinity.

- To absorb this, you must split the "bare" SM parameters into a finite measurable piece and an infinite counterterm (e.g., g0​=g(μ)+δg, or m0​=m(μ)+δm).
    
- The infinite δg counterterm perfectly eats the infinity from the standard loop.
    

### 2. The Wavefunctions (Fields)

The particles themselves undergo quantum fluctuations as they travel. A bare electron field (ψ0​) is technically infinite.

- To get the physical electron we see in detectors, we must renormalize the field itself: ψ0​=Zψ​![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.28em"%20viewBox="0%200%20400000%201296"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M263,681c0.7,0,18,39.7,52,119c34,79.3,68.167,158.7,102.5,238c34.3,79.3,51.8,119.3,52.5,120c340,-704.7,510.7,-1060.3,512,-1067l0%20-0c4.7,-7.3,11,-11,19,-11H40000v40H1012.3s-271.3,567,-271.3,567c-38.7,80.7,-84,175,-136,283c-52,108,-89.167,185.3,-111.5,232c-22.3,46.7,-33.8,70.3,-34.5,71c-4.7,4.7,-12.3,7,-23,7s-12,-1,-12,-1s-109,-253,-109,-253c-72.7,-168,-109.3,-252,-110,-252c-10.7,8,-22,16.7,-34,26c-22,17.3,-33.3,26,-34,26s-26,-26,-26,-26s76,-59,76,-59s76,-60,76,-60zM1001%2080h400000v40h-400000z"></path></svg>)​ψR​.
    
- Every single external line in your Feynman diagram (whether it attaches to an SM vertex or an EFT vertex) must be multiplied by these field renormalization factors to remain finite.
    

### 3. The Wilson Coefficients

If a loop occurs across your Dimension-6 contact vertex, it generates a massive, harsh infinity.

**Why can't we just use the Standard Model δg to absorb it?** Because of the mathematical "shape" of the infinity.

- A Standard Model vertex has a specific algebraic structure (Dimension-4). Its infinity looks like a Dimension-4 term. The δg counterterm is built to perfectly match and subtract that exact shape.
    
- Your EFT contact vertex has a completely different algebraic structure (Dimension-6). The infinity it generates looks like a Dimension-6 term.
    

If you try to subtract a Dimension-6 infinity using a Dimension-4 counterterm (δg), the math violently rejects it. The matrices do not align; the momenta do not cancel.

As you perfectly deduced, **the only mathematical object capable of absorbing an infinity generated by a Dimension-6 operator is the bare parameter of a Dimension-6 operator.** Therefore, you must define a bare Wilson coefficient:

C0​=C(μ)+δC

The δC counterterm acts as a custom-built puzzle piece that exactly matches the shape of the contact-loop infinity, cleanly absorbing it and leaving behind the finite, running C(μ) that experimentalists measure.

You can interact with the widget below to visually lock in this "shape-matching" constraint, which strictly prevents SM parameters from fixing EFT loops.

okey perfect, now if i just work with the LO the wilson coefficients are energy independent? how do i change my amplitude from the theoretical part with a 1Tev cutoff to the energy scale of the experiment

You have perfectly identified the mathematical boundary between LO and NLO.

**Yes, if you strictly work at Leading Order (LO), the Wilson coefficients are completely independent of the energy scale.** They are static, rigid constants.

Here is the exact logical breakdown of why this happens, and how you handle the math when moving from the 1 TeV reference scale to your experimental energy.

### 1. Why LO Means Constant Coefficients

The entire mechanism of coefficients "running" (changing with energy) is powered by the Renormalization Group Equations (RGEs).

- RGEs only exist to cure the Ultraviolet (UV) infinities generated by quantum loops.
    
- By definition, Leading Order (LO) diagrams have **zero closed loops**.
    
- Because there are no loops, there are no infinities. Because there are no infinities, you do not need to introduce the arbitrary renormalization scale (μ).
    

Without μ, the RGEs mathematically evaluate to zero. At strict LO, Ci​ is just a normal, unchanging number.

### 2. How to Translate the Amplitude to the Experiment

You asked: _"How do I change my amplitude from the theoretical part with a 1 TeV cutoff to the energy scale of the experiment?"_

**You don't change the coefficient at all. You literally just plug it in.**

If the global physics community agrees that a specific Wilson coefficient is Ci​=0.05 at the reference cutoff of Λ=1 TeV, and your experiment is operating at 91 GeV, you simply write:

MEFT​∝(1 TeV)20.05​

You use that exact same number whether you are colliding particles at 10 GeV, 91 GeV, or 500 GeV.

### 3. If Ci​ is Constant, How Does Energy Affect the Physics?

If the coefficient doesn't change, why do EFT effects explode at high energies?

The energy dependence of your experiment does not come from the Wilson coefficient; it comes strictly from the **kinematics of the collision**.

When you integrate the amplitude to find the observable cross-section (σ), the energy of the colliding particles (E, or s![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429c69,-144,104.5,-217.7,106.5,-221l0%20-0c5.3,-9.3,12,-14,20,-14H400000v40H845.2724s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47zM834%2080h400000v40h-400000z"></path></svg>)​) enters the numerator of the equation through the phase space. For a standard Dimension-6 interference term, the cross-section scales like:

σInterference​∝Ci​(Λ2E2​)

- **The Constant:** Ci​ and Λ are locked, static numbers.
    
- **The Variable:** The collision energy E2 is driving the growth.
    

At low energies, E2 is small, so the EFT effect is mathematically suppressed. At high energies, E2 grows massive, amplifying the static Ci​ parameter and making the new physics easily visible to your detectors.

### A Note on Phenomenological "Cheating"

While it is theoretically true that LO means no running, modern theoretical physicists often cheat to get better predictions without doing the agonizing NLO loop math. They will calculate the Feynman diagrams at tree-level (LO), but they will _borrow_ the NLO RGE equations to run the Ci​ coefficient anyway. This hybrid approach is called **"RGE-improved LO,"** and it mathematically absorbs the largest quantum loop errors without requiring you to draw a single loop diagram.

You can interact with the widget below to visually separate the static nature of the LO coefficient from the violent energy scaling of the physical collision.

okey I need a new workflow redo again all the bottom up workflow

Here is the definitive, comprehensive **Bottom-Up SMEFT Workflow**.

This is the exact sequence a phenomenologist follows when they do not know what the new physics is, but want to use the Large Hadron Collider (LHC) to hunt for it anyway. It incorporates everything we have covered: the propagating Z boson, the contact vertices, the interference, the RGE running, and the global fit.

### Phase 1: The Theoretical Setup (Building the Basis)

**The Goal:** Define a universal mathematical language for the unknown without breaking the Standard Model (SM).

1. **Keep the SM Intact:** You assume the energy (E) is much lower than the mass of the unknown new physics (Λ). Because you are at collider energies, the Z,W, Higgs, and Top are all considered "light." They remain in the Lagrangian as fully propagating physical waves.
    
2. **Add the Unknowns:** You mathematically add every possible Dimension-6 contact operator (e.g., the Warsaw Basis) to the SM Lagrangian.
    
3. **The Universal Standard:** You assign an unknown Wilson coefficient (Ci​) to each operator. To ensure all experiments can communicate, you permanently lock the cutoff scale to a mathematical reference point: Λ=1 TeV.
    
    - LSMEFT​=LSM​+∑(1 TeV)2Ci​​Oi​
        

### Phase 2: The Quantum Prediction (Calculating Cross-Sections)

**The Goal:** Calculate exactly how these unknown operators would change what a particle detector sees.

1. **The Amplitude Superposition:** For any given collision (e.g., e−e+→μ−μ+), you calculate the standard propagating SM diagram AND the new EFT contact diagram. The total amplitude is their sum.
    
2. **The NLO Corrections:** You draw quantum loops of light SM particles across both diagrams. The loops on the contact vertex generate harsh Dimension-6 infinities. You are mathematically forced to renormalize the Wilson coefficients, transforming them into scale-dependent variables: Ci​(μ).
    
3. **Squaring for the Cross-Section:** You square the total amplitude. This mathematically forces the SM geometry and the EFT geometry to interact, creating the crucial **quantum interference** term. You are left with a rigid quadratic equation:
    
    - σ(Ci​)=σSM​+Ci​⋅σInterference​+Ci2​⋅σPure BSM​
        

### Phase 3: The Energy Translation (RGE Running)

**The Goal:** Connect the arbitrary 1 TeV reference scale to the actual energy of the physical experiment.

1. **The Scale Mismatch:** The coefficients you want to fit are defined at 1 TeV (e.g., Ci​(1 TeV)). But the experimental data you want to use might be from LEP (91 GeV) or a high-energy LHC bin (2000 GeV).
    
2. **Operator Mixing:** You plug Ci​(1 TeV) into the Renormalization Group Equations (RGEs). Using the Anomalous Dimension Matrix, you mathematically "run" the coefficient down to the experimental energy. This process automatically accounts for how the coefficients change strength and mix into one another due to virtual loops.
    
3. **The Final Equation:** You now have a cross-section prediction exactly tailored to the detector's energy, written purely as a function of the unknown 1 TeV coefficients.
    

### Phase 4: The Global Fit (Data Comparison)

**The Goal:** Use physical reality to solve the mathematical equations.

1. **The Degeneracy Problem:** If you only use one measurement, multiple different Ci​ parameters could conspire to give you the exact same cross-section. You cannot solve for them.
    
2. **The Solution (Energy Bins & Multiple Processes):** You feed a supercomputer data from hundreds of different processes (Higgs decays, Top production, Z-pole data) sliced into high and low-energy kinematic bins. Because EFT effects scale fiercely with energy (E2/Λ2), the high-energy bins rigidly lock down the operators.
    
3. **Minimizing χ2:** The computer scans the multi-dimensional parameter space to find the single, unique combination of Ci​ values that minimizes the statistical difference (χ2) between your theoretical equations and the global dataset.
    

### Phase 5: The Physical Conclusion (Discovery or Constraint)

**The Goal:** Determine if new physics actually exists.

- **The Constraint:** If the global fit determines that Ci​(1 TeV)=0 (within statistical error), the Standard Model survives. You have successfully placed mathematical "bounds" on how strong new physics is allowed to be.
    
- **The Discovery:** If the fit strictly demands that Ci​(1 TeV)=0.08, you have discovered new physics.
    
- **The Handoff (Top-Down):** The phenomenologist's job is done. They hand this 0.08 number to the theoretical model-builders. The theorists will invent specific heavy particles (like a 4 TeVZ′ boson), perform Top-Down matching, and see if their theorized particle perfectly generates that exact 0.08 value.
    

Here is an interactive flowchart to solidify this complete, end-to-end SMEFT pipeline.

Why do we truncate the EFT expansion at dimension 6? What appears at dimension 5?hints ↓

  

Dimension 5: only the Weinberg operator (L L H H + h.c.) — gives Majorana neutrino masses

Dimension-5 operators suppressed by 1/Λ; dimension-6 by 1/Λ²

Odd dimensions break lepton or baryon number → strongly constrained

Dimension-6 is the first level with rich phenomenology while still systematically controllable

Here is the straight-to-the-point, logical explanation of how the Effective Field Theory (EFT) expansion is structured at its lowest levels.

### 1. What Appears at Dimension-5?

In the Standard Model Effective Field Theory (SMEFT), there is exactly **one** unique mathematical operator (ignoring flavor variations) that can be constructed at mass dimension-5 while respecting the Standard Model gauge symmetries.

It is called the **Weinberg Operator**:

O5​=ΛC5​​(LH)(LH)+h.c.

_(Where L is the left-handed lepton doublet and H is the Higgs doublet)._

**The Physical Consequence:** When the Higgs field acquires its vacuum expectation value (v) during electroweak symmetry breaking, this operator collapses down into a direct mass term for the neutrino (mν​∝v2/Λ).

Crucially, it generates a **Majorana mass**, meaning it forces the neutrino to be its own antiparticle. Because it turns a lepton into an antilepton, this operator strictly violates Lepton Number (L) by two units (ΔL=2).

---

### 2. Why Do We Truncate at Dimension-6?

The EFT Lagrangian is an infinite power series (1/Λ,1/Λ2,1/Λ3…). Theoretical physicists permanently truncate their collider calculations at Dimension-6 (1/Λ2) for three strict physical and mathematical reasons.

**A. The Odd/Even Symmetry Rule (Baryon and Lepton Number)** There is a fundamental mathematical quirk in SMEFT: **odd-dimensional operators (d=5,d=7) break Lepton (L) or Baryon (B) number, while even-dimensional operators (d=6,d=8) conserve them.**

- We know from proton decay experiments that Baryon number is phenomenally strictly conserved. If B-violating operators exist, their cutoff scale Λ must be astronomically high (e.g., Λ≈1015 GeV) to suppress proton decay enough to match reality.
    
- If Λ is that massive, the 1/Λ suppression makes the effect of odd-dimensional operators at LHC energies (1 TeV) mathematically indistinguishable from zero.
    
- Dimension-6 is the first level of the expansion that conserves B and L. Therefore, it is the lowest dimension where Λ is allowed to be small enough (≈1 TeV) to actually produce visible phenomenology in our current colliders.
    

**B. The Kinematic Suppression Hierarchy** The expansion parameter for cross-sections is strictly based on the collision energy (E):

- **Dimension-6 effects** scale as (E/Λ)2.
    
- **Dimension-8 effects** scale as (E/Λ)4.
    

If E<Λ, raising that fraction to the 4th power makes the Dimension-8 contribution exceptionally tiny. Currently, the statistical error bars on LHC detector measurements are generally larger than the expected size of a (E/Λ)4 effect. Truncating at Dimension-6 captures the dominant, observable new physics while safely ignoring terms that are currently too small to measure anyway.

**C. Mathematical Solvability (The Parameter Explosion)** To perform a global fit, you need a manageable number of unknown Wilson coefficients (Ci​).

- At Dimension-5, there is 1 operator.
    
- At Dimension-6, there are exactly 59 independent operators (the Warsaw Basis). This is difficult, but supercomputers can solve a 59-variable matrix.
    
- At Dimension-8, the basis violently explodes to **993 independent operators**.
    

If you do not truncate at Dimension-6, you inject nearly a thousand new unknown variables into your cross-section equations. This creates massive mathematical degeneracies, making it completely impossible to fit the data and destroying the predictive power of the theory. Dimension-6 is the mathematical sweet spot: it is phenomenologically rich, but systematically controllable.

Write the operator OG (triple gluon). Which class does it belong to? What vertices does it affect?

Here is the precise definition and breakdown of the triple gluon operator.

### 1. The Operator Definition

In the Standard Model Effective Field Theory (SMEFT), specifically within the Warsaw Basis, the triple gluon operator is mathematically defined as:

OG​=fABCGμAν​GνBρ​GρCμ​

- **GμνA​**: The gluon field strength tensor.
    
- **fABC**: The totally antisymmetric structure constants of the SU(3)C​ color group.
    
- **Indices**: μ,ν,ρ are Lorentz indices, and A,B,C are color indices (ranging from 1 to 8).
    

### 2. Operator Class

It belongs to the **X3 class** (often referred to as "pure gauge" or "field strength cubed" operators).

This class consists strictly of operators built from exactly three field strength tensors and no other Standard Model fields (like Higgs or fermions). Its electroweak counterparts in this class are OW​ (triple W boson) and their CP-violating duals (OG![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="100%"%20height="0.26em"%20viewBox="0%200%20600%20260"%20preserveAspectRatio="none"><path%20d="M200%2055.538c-77%200-168%2073.953-177%2073.953-3%200-7-2.175-9-5.437L2%2097c-1-2-2-4-2-6%200-4%202-7%205-9l20-12C116%2012%20171%200%20207%200c86%200%20114%2068%20191%2068%2078%200%20168-68%20177-68%204%200%207%202%209%205l12%2019c1%202.175%202%204.35%202%206.525%200%204.35-2%207.613-5%209.788l-19%2013.05c-92%2063.077-116.937%2075.308-183%2076.128-68.267.847-113-73.952-191-73.952z"></path></svg>)​, OW![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="100%"%20height="0.26em"%20viewBox="0%200%20600%20260"%20preserveAspectRatio="none"><path%20d="M200%2055.538c-77%200-168%2073.953-177%2073.953-3%200-7-2.175-9-5.437L2%2097c-1-2-2-4-2-6%200-4%202-7%205-9l20-12C116%2012%20171%200%20207%200c86%200%20114%2068%20191%2068%2078%200%20168-68%20177-68%204%200%207%202%209%205l12%2019c1%202.175%202%204.35%202%206.525%200%204.35-2%207.613-5%209.788l-19%2013.05c-92%2063.077-116.937%2075.308-183%2076.128-68.267.847-113-73.952-191-73.952z"></path></svg>)​).

### 3. Affected Vertices

To determine which physical interactions this operator alters, you must substitute the definition of the non-Abelian field strength tensor into the operator:

GμνA​=∂μ​AνA​−∂ν​AμA​+gs​fABCAμB​AνC​

Because the field strength tensor itself contains both a derivative term (1 gluon field) and a coupling term (2 gluon fields), cubing this tensor mathematically generates an expansion of terms with increasing numbers of gluon fields.

Specifically, OG​ generates and affects the following vertices:

- **3-Gluon Vertex (ggg):** Generated by multiplying three derivative terms (∂A)3. This modifies the kinematics of the existing Standard Model triple-gluon vertex.
    
- **4-Gluon Vertex (gggg):** Generated by multiplying two derivative terms and one coupling term (∂A)2(A2). This modifies the existing Standard Model quartic-gluon vertex.
    
- **5-Gluon Vertex (ggggg):** Generated by multiplying one derivative term and two coupling terms (∂A)(A2)2. **This is a novel vertex.** The Standard Model does not possess a fundamental 5-gluon contact interaction.
    
- **6-Gluon Vertex (gggggg):** Generated by multiplying three coupling terms (A2)3. **This is also a novel vertex,** allowing 6 gluons to interact at a single point.
    

CP-odd analogue Õ_G is constrained by low-energy measurements; CP-even is less constrained can you explain this better?

The difference in constraints between these two operators comes down to a single experimental reality: **searching for a tiny signal in a noisy background versus searching for a signal in a perfectly quiet room.**

Here is the precise, logical explanation of why the CP-odd operator is heavily constrained while its CP-even sibling is not.

### 1. The CP-Odd Operator (O![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="100%"%20height="0.26em"%20viewBox="0%200%20600%20260"%20preserveAspectRatio="none"><path%20d="M200%2055.538c-77%200-168%2073.953-177%2073.953-3%200-7-2.175-9-5.437L2%2097c-1-2-2-4-2-6%200-4%202-7%205-9l20-12C116%2012%20171%200%20207%200c86%200%20114%2068%20191%2068%2078%200%20168-68%20177-68%204%200%207%202%209%205l12%2019c1%202.175%202%204.35%202%206.525%200%204.35-2%207.613-5%209.788l-19%2013.05c-92%2063.077-116.937%2075.308-183%2076.128-68.267.847-113-73.952-191-73.952z"></path></svg>)G​) and "Zero-Background" Precision

The CP-odd operator (O![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="100%"%20height="0.26em"%20viewBox="0%200%20600%20260"%20preserveAspectRatio="none"><path%20d="M200%2055.538c-77%200-168%2073.953-177%2073.953-3%200-7-2.175-9-5.437L2%2097c-1-2-2-4-2-6%200-4%202-7%205-9l20-12C116%2012%20171%200%20207%200c86%200%20114%2068%20191%2068%2078%200%20168-68%20177-68%204%200%207%202%209%205l12%2019c1%202.175%202%204.35%202%206.525%200%204.35-2%207.613-5%209.788l-19%2013.05c-92%2063.077-116.937%2075.308-183%2076.128-68.267.847-113-73.952-191-73.952z"></path></svg>)G​=fABCG![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="100%"%20height="0.26em"%20viewBox="0%200%20600%20260"%20preserveAspectRatio="none"><path%20d="M200%2055.538c-77%200-168%2073.953-177%2073.953-3%200-7-2.175-9-5.437L2%2097c-1-2-2-4-2-6%200-4%202-7%205-9l20-12C116%2012%20171%200%20207%200c86%200%20114%2068%20191%2068%2078%200%20168-68%20177-68%204%200%207%202%209%205l12%2019c1%202.175%202%204.35%202%206.525%200%204.35-2%207.613-5%209.788l-19%2013.05c-92%2063.077-116.937%2075.308-183%2076.128-68.267.847-113-73.952-191-73.952z"></path></svg>)μAν​GνBρ​GρCμ​) fundamentally violates Charge-Parity (CP) symmetry.

Because it violates CP, it mathematically generates an **Electric Dipole Moment (EDM)** for the neutron.

- **The Standard Model Baseline:** The Standard Model strictly conserves CP in the strong force. Therefore, the Standard Model predicts that the neutron's EDM is functionally zero.
    
- **The Measurement:** Physicists measure the neutron EDM in ultra-cold, low-energy table-top experiments by watching how neutrons spin in powerful electric fields.
    
- **The Constraint:** Because the background expectation is exactly zero, these low-energy experiments are unbelievably precise. The current experimental limit on the neutron EDM is smaller than 10−26e⋅cm.
    

If the Wilson coefficient for O![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="100%"%20height="0.26em"%20viewBox="0%200%20600%20260"%20preserveAspectRatio="none"><path%20d="M200%2055.538c-77%200-168%2073.953-177%2073.953-3%200-7-2.175-9-5.437L2%2097c-1-2-2-4-2-6%200-4%202-7%205-9l20-12C116%2012%20171%200%20207%200c86%200%20114%2068%20191%2068%2078%200%20168-68%20177-68%204%200%207%202%209%205l12%2019c1%202.175%202%204.35%202%206.525%200%204.35-2%207.613-5%209.788l-19%2013.05c-92%2063.077-116.937%2075.308-183%2076.128-68.267.847-113-73.952-191-73.952z"></path></svg>)G​ were even slightly large, it would generate an EDM massive enough to have been discovered decades ago. Because we measure exactly zero, the coefficient for O![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="100%"%20height="0.26em"%20viewBox="0%200%20600%20260"%20preserveAspectRatio="none"><path%20d="M200%2055.538c-77%200-168%2073.953-177%2073.953-3%200-7-2.175-9-5.437L2%2097c-1-2-2-4-2-6%200-4%202-7%205-9l20-12C116%2012%20171%200%20207%200c86%200%20114%2068%20191%2068%2078%200%20168-68%20177-68%204%200%207%202%209%205l12%2019c1%202.175%202%204.35%202%206.525%200%204.35-2%207.613-5%209.788l-19%2013.05c-92%2063.077-116.937%2075.308-183%2076.128-68.267.847-113-73.952-191-73.952z"></path></svg>)G​ is mathematically crushed to a near-zero value.

### 2. The CP-Even Operator (OG​) and the "Noisy" Collider

The CP-even operator (OG​=fABCGμAν​GνBρ​GρCμ​) conserves CP symmetry.

Because it conserves CP, it does not generate an Electric Dipole Moment. It remains completely invisible to those ultra-precise, low-energy table-top experiments. The only way to detect it is at high-energy colliders (like the LHC) by measuring changes to the triple-gluon vertex.

- **The Standard Model Baseline:** The Standard Model already produces billions of standard 3-gluon vertices per second at the LHC, resulting in massive bursts of multi-jet events.
    
- **The Measurement:** You must count the total number of jets produced and see if the number is slightly higher than the Standard Model predicts.
    
- **The Constraint:** This is highly imprecise. Theoretical predictions for QCD jet production suffer from a 10% to 20% uncertainty due to Parton Distribution Functions (PDFs) and scale variations.
    

If the Wilson coefficient for OG​ is reasonably large, it might only increase the jet production rate by 2%. Because the Standard Model background uncertainty is 10%, that 2% shift is completely swallowed by the error bars. Therefore, the constraint on OG​ remains relatively weak.

### Summary

- **O![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="100%"%20height="0.26em"%20viewBox="0%200%20600%20260"%20preserveAspectRatio="none"><path%20d="M200%2055.538c-77%200-168%2073.953-177%2073.953-3%200-7-2.175-9-5.437L2%2097c-1-2-2-4-2-6%200-4%202-7%205-9l20-12C116%2012%20171%200%20207%200c86%200%20114%2068%20191%2068%2078%200%20168-68%20177-68%204%200%207%202%209%205l12%2019c1%202.175%202%204.35%202%206.525%200%204.35-2%207.613-5%209.788l-19%2013.05c-92%2063.077-116.937%2075.308-183%2076.128-68.267.847-113-73.952-191-73.952z"></path></svg>)G​ (CP-Odd):** Causes a physical effect (Neutron EDM) that the Standard Model says should not exist. Tested by extreme-precision, low-energy experiments. Result: **Highly Constrained.**
    
- **OG​ (CP-Even):** Only modifies a physical effect (Jet Production) that the Standard Model already does constantly. Tested by noisy, high-uncertainty colliders. Result: **Weakly Constrained.**
    

You can interact with the widget below to visualize the mechanical difference between searching for these two operators.

so there is cp conservation but no one knows why no?

You hit the nail exactly on the head. This exact paradox is officially known as the **Strong CP Problem**, and it is one of the most famous unsolved mysteries in all of modern physics.

Here is why it drives physicists crazy.

### 1. The Math Allows It (The θ Angle)

When you write down the Lagrangian for Quantum Chromodynamics (QCD)—the theory of the strong force—there is a completely legal, valid mathematical term you can add that violates CP symmetry.

This term is multiplied by a fundamental constant called **θˉ** (theta). Because it acts like an angle, the math says θˉ should naturally be some random number between 0 and 360∘ (or −π to π). If θˉ is anything other than exactly zero, the strong force violates CP symmetry, and the neutron gets an Electric Dipole Moment (EDM).

### 2. Reality Rejects It (The Pencil on its Tip)

As we discussed, the neutron EDM is experimentally measured to be practically zero. This strictly forces the value of θˉ to be ridiculously small:

θˉ<10−10

This is the problem. Why is it exactly zero (or so close to zero that we can't measure it)? Imagine walking into a room and finding a pencil balancing perfectly on its completely sharpened tip. According to the laws of physics, it is mathematically _possible_ for it to balance there. But it is so absurdly unlikely that you immediately assume some hidden mechanism (or a person) must be holding it there.

Physicists refuse to believe θˉ is 0.0000000000 just by pure luck. They believe there must be a hidden physics mechanism forcing it to balance there.

### 3. The Best Guess: The Axion

While "no one knows for sure," we do have a leading suspect. In 1977, physicists Roberto Peccei and Helen Quinn proposed a brilliant mathematical trick to solve this.

They suggested that θˉ is not a static, rigid number. Instead, they proposed it is a **dynamic field**—a new particle. This particle is called the **Axion**.

If θˉ is a physical field, it behaves like a ball on a hill. It will naturally roll down to find the lowest possible energy state. Peccei and Quinn proved that the absolute lowest energy state of the QCD potential perfectly aligns with exactly θˉ=0.

If the axion exists, the universe started with a random amount of CP violation, but as the universe cooled, the axion field rolled to the bottom of the hill, dynamically erasing CP violation from the strong force forever.

You can interact with the widget below to see exactly how making θ a dynamic particle solves the Strong CP Problem.

What does the SMEFT predict for the theoretical cross section? Write the decomposition into SM + linear + quadratic terms.

In the **SMEFT (Standard Model Effective Field Theory)** framework, the theoretical cross-section for a given process is derived by squaring the total probability amplitude. As we established, this amplitude is the sum of the Standard Model contribution and the new physics (EFT) contribution:

MTotal​=MSM​+i∑​Λ2Ci​​Mi​

When you calculate the observable cross-section (σ), which is proportional to ∣MTotal​∣2, you arrive at a quadratic decomposition.

### The SMEFT Cross-Section Decomposition

For a single Wilson coefficient Ci​, the prediction for the cross-section σ at a specific energy scale is:

σ(Ci​)=σSM​+Λ2Ci​​σint​+Λ4Ci2​​σBSM​

If multiple operators are involved, the formula accounts for the interference between different EFT operators as well:

σ({C})=σSM​+i∑​Λ2Ci​​σint,i​+i∑​Λ4Ci2​​σBSM,i​+i<j∑​Λ4Ci​Cj​​σmixed,ij​

---

### Breakdown of the Terms

|Term|Mathematical Origin|Physical Interpretation|
|---|---|---|
|**σSM​**|$|\mathcal{M}_{\text{SM}}|
|**σint​**|2Re(MSM​Mi∗​)|**Linear Interference:** Quantum interference between SM and EFT. It can be positive or negative. It scales as 1/Λ2 and is usually the dominant "discovery" term.|
|**σBSM​**|$|\mathcal{M}_i|

### Important Considerations for the Decomposition

- **Truncation and Validity:** In a strict Dimension-6 expansion, the σBSM​ term is technically at the same suppression level (1/Λ4) as the interference of a **Dimension-8** operator with the SM. Therefore, if the quadratic term σBSM​ is very large in your fit, it may indicate that your EFT expansion is becoming unstable and you might need to consider higher-dimension operators.
    
- **Energy Scaling:** The "coefficients" (σint​,σBSM​) are not just numbers; they contain the kinematic dependence. In SMEFT, these terms typically grow with energy (E2/Λ2), meaning the decomposition becomes much more sensitive to Ci​ in high-energy tails of distributions.
    
- **Interference Suppression:** In some processes (like certain diboson productions), the SM and EFT amplitudes have different "helicity" structures. In these cases, σint​ can be accidentally near zero, making the quadratic term σBSM​ the primary way to detect the new physics.
    

Is SMEFT always a 'good theory'? What are the known limitations and theoretical errors that must be included?

SMEFT is not unconditionally a "good theory." Its validity and internal consistency are strictly bounded by the energy scales involved and the perturbative truncations applied.

### 1. Known Limitations of SMEFT

SMEFT is an effective approximation that relies on specific conditions to remain mathematically and physically consistent:

- **The Kinematic Boundary (E≪Λ):** SMEFT is only reliable for processes involving momentum transfers that are much smaller than the cutoff scale Λ. If the collision energy approaches Λ, the expansion breaks down.
    
- **The Truncation Instability:** The SMEFT expansion is typically truncated at Dimension-6. However, situations exist where the scale Λ and Dimension-6 coefficients (c6) are small, but Dimension-8 coefficients (c8) are sizable. In these cases, the neglected D=8 operators can contribute significantly, destroying the internal consistency of the LO D=6 theory.
    
- **Parameter Degeneracy and Broad Bounds:** A hierarchy of high experimental precision (e.g., per-mille constraints from lepton colliders) does not consistently translate into a hierarchy of tight constraints on individual Wilson coefficients. Because of operator mixing and flat directions, it is not justified to simply set poorly constrained parameters to zero in LHC analyses.
    

### 2. Theoretical Errors That Must Be Included

When experimental precision reaches the O(10%) level, and especially as it descends to the percent or per-mille level, it becomes absolutely critical to include specific SMEFT theoretical errors.

- **Missing Higher Orders (MHOs):** A fit at Leading Order (LO) must include a theoretical covariance matrix and a theoretical error to account for neglected higher-order effects in the SMEFT expansion. A conservative approximation of this error mathematically incorporates the estimated size of Dimension-8 contributions (∝vT4​/Λ4) and the 1-loop logarithmic corrections (∝16π21​ln(Λ2/vT2​)).
    
- **NLO Loop Corrections:** One-loop (NLO) corrections must be included because they can introduce dependencies on Wilson coefficients that do not even contribute at tree level to a particular process. If some of these newly introduced coefficients are poorly bounded, their 1-loop insertions can generate unexpectedly large effects that drastically alter the interpretation of the data.
    
- **Methodological Ambiguities ("Options"):** There are multiple mathematically valid ways to compute the same SMEFT observable, which introduces intrinsic uncertainty. Theoretical errors must account for the variations caused by:
    
    - Choosing to strictly linearize the squared matrix element versus including the quadratized terms.
        
    - Varying the renormalization scale.
        
    - Choosing different renormalization schemes (e.g., the GF​ scheme versus the α-scheme).
        

To safely estimate the total theoretical uncertainty, a conservative approach requires taking the envelope over all these different computational "options" and interpreting that envelope as a flat Bayesian prior or a log-normal distribution.

Es posible que los archivos subidos sean demasiado grandes para obtener los mejores resultados. [Más informaciónSe abre en una ventana nueva](https://support.google.com/gemini?p=context_window)

Why is going to NLO important in SMEFT? What new features appear at one loop?

Going to Next-to-Leading Order (NLO) in SMEFT is not merely about achieving a higher degree of numerical precision; it fundamentally alters the physics of the theory. In the Standard Model, NLO usually just shrinks your error bars. In SMEFT, NLO mathematically unlocks entirely new interactions and dependencies that are strictly invisible at tree level (LO).

Here is the precise, logical breakdown of the new features that exclusively appear at one loop, and why they are critical for global fits.

### 1. Loop-Induced Sensitivity (Breaking "Blind Spots")

At Leading Order, an experiment can only constrain a Wilson coefficient if that specific operator directly interacts with the initial or final-state particles of the collision.

- **The LO Blind Spot:** Imagine an operator that only modifies how top quarks interact (Ct​). If you run an experiment colliding electrons into muons (like at the LEP collider), the tree-level math contains zero top quarks. Therefore, LEP data is 100% blind to Ct​.
    
- **The NLO Feature:** When you calculate the one-loop corrections for that same electron-muon collision, quantum mechanics dictates that virtual top quarks will temporarily materialize in the loops. If the top-quark operator (Ct​) exists, it will modify those virtual loops.
    
- **The Result:** The observable electron-muon cross-section suddenly gains a mathematical dependence on Ct​. NLO fundamentally breaks theoretical "flat directions" (unconstrained parameters) by allowing data from one sector of physics to rigidly constrain completely different, seemingly disconnected sectors.
    

### 2. Operator Mixing and RGE Running

As established previously, tree-level SMEFT operators are static and isolated. They do not interact with one another.

- **The NLO Feature:** One-loop diagrams force Standard Model particles to bridge the gap between different EFT operators. The Ultraviolet (UV) infinities generated by these loops force the Wilson coefficients to become scale-dependent (Ci​(μ)).
    
- **The Result:** You trigger the Anomalous Dimension Matrix. An operator defined at a high cutoff scale (Λ) will mathematically "bleed" into a dozen other operators as you evolve the energy down to the collider scale. You cannot consistently compare data from the 91 GeV Z-pole to 2 TeV LHC jets without this NLO mixing matrix.
    

### 3. Finite Kinematic Shape Alterations

When you renormalize an NLO loop, you absorb the infinity into the Wilson coefficient. However, you leave behind a "finite piece"—a complex mathematical function of the particle momenta.

- **The LO Baseline:** At LO, the interference between the SM and a Dimension-6 operator forces the cross-section to grow rigidly as (E2/Λ2).
    
- **The NLO Feature:** The finite loop pieces introduce logarithmic energy dependencies, such as ln(E2/μ2).
    
- **The Result:** These logarithms bend and warp the shape of the differential cross-section (the high-energy tails). Because global fits rely heavily on the exact shape of these high-energy distributions to extract the true value of Ci​, ignoring the NLO finite pieces will cause the fitting algorithm to extract the completely wrong numerical value.
    

### 4. Reduction of Scale Uncertainty

In quantum field theory, the introduction of the arbitrary renormalization scale (μ) represents a theoretical error. We do not know what exact value of μ to use, and guessing wrong shifts the prediction.

- **The LO Problem:** At LO, if you use "RGE-improved" running, your Wilson coefficient depends on μ, but your tree-level Feynman diagram does not. Changing μ causes your total prediction to wildly swing up and down. This creates a massive theoretical uncertainty.
    
- **The NLO Feature:** When you calculate the full NLO loop diagram, the diagram itself naturally generates a ln(μ) term.
    
- **The Result:** The explicit μ dependence in the NLO loop diagram strictly cancels against the implicit μ dependence inside the running Wilson coefficient. This stabilizes the equation, drastically shrinking the theoretical error bars and allowing experimentalists to claim a rigid discovery.
    

You can interact with the widget below to physically see the most important NLO feature: how loop-induced sensitivity breaks experimental blind spots.


1What is the gauge principle? Starting from a global symmetry, why does demanding local invariance force the introduction of a new field?hints ↓

- Global U(1) phase invariance of the Dirac Lagrangian
- Covariant derivative Dμ = ∂μ + igAμ absorbs the extra ∂μα(x) term
- The new field Aμ must have its own kinetic term → gauge boson
- Generalise to non-Abelian SU(3): [Ta, Tb] = ifabc Tc → self-interactions

2Write the QCD Lagrangian. Identify every term and explain its physical origin, including the ghost sector.hints ↓

- Quark kinetic + minimal coupling: ψ̄(i γμ Dμ − m)ψ
- Gauge kinetic term: −¼ Fμνa Fμνa, with Fμν = ∂μAν − ∂νAμ − g fabc AbAc
- Gauge fixing term −(1/2ξ)(∂μAμa)² removes the redundancy in the path integral
- Ghost Lagrangian ∂μc̄a ∂μca + g fabc (∂μc̄a) Abμ cc: Faddeev–Popov Jacobian

3Why does the non-Abelian nature of SU(3) lead to gluon self-interactions, while there are none for the photon in QED?hints ↓

- Structure constants fabc ≠ 0 → last term in Fμν is non-zero
- This generates cubic and quartic gluon vertices directly from the kinetic term
- Gluons carry colour charge themselves, unlike the electrically-neutral photon
- U(1) is Abelian: f = 0, no self-coupling, no need for ghosts

4Explain renormalization: what problem does it solve and what is the conceptual procedure?hints ↓

- UV divergences in loop integrals (undetermined loop momenta → integrate to ∞)
- Introduce regulator (e.g. dim-reg: d = 4−2ε), isolate poles as 1/ε
- Split bare parameters into physical + counterterms; counterterms absorb divergences
- Physical predictions are finite; scheme dependence (MS̄, on-shell) is a choice of finite part

5What are Fermi's theory of weak interactions and CKM mixing? Why is Fermi's theory a first example of an EFT?hints ↓

- Fermi: 4-fermion contact interaction GF/√2 · (J+)(J−), no gauge bosons
- Valid for E ≪ mW: the heavy W is 'integrated out' leaving a local operator
- GF = g²/(4√2 mW²): matching condition between Fermi EFT and the full SM
- CKM matrix V = Vu† Vd appears when diagonalising Yukawa matrices for 3 generations
- It has 3 mixing angles + 1 CP-violating phase (5 phases absorbed by field redefinitions)

6What is the β-function in QCD? Write the leading-order coefficient β₀. What does its sign imply?hints ↓

- RGE: μ² ∂αs/∂μ² = β(αs) = −αs² (β₀ + β₁ αs + …)
- At 1-loop: β₀ = (33 − 2Nf) / 12π
- For Nf ≤ 16: β₀ > 0 → β < 0 → coupling decreases with μ
- Running coupling: αs(μ²) = αs(μ₀²) / [1 + β₀ αs(μ₀²) ln(μ²/μ₀²)]

7What is asymptotic freedom? What does it imply about when perturbative QCD is reliable?hints ↓

- αs → 0 as μ → ∞: quarks and gluons are quasi-free at high energies
- Perturbative QCD valid only when αs(Q) ≪ 1, i.e. Q ≫ ΛQCD
- This justifies using fixed-order perturbation theory for high-pT jet production at LHC
- At low energy (Q ~ ΛQCD): confinement, hadronisation, non-perturbative physics

8What is ΛQCD (Landau pole)? What phenomenon does it signal and what is its approximate value?hints ↓

- Landau pole: scale where 1-loop αs diverges: ln ΛQCD = ln μ₀² − 1/(β₀ αs(μ₀²))
- ΛQCD ≈ 200–500 MeV: boundary between perturbative and non-perturbative QCD
- Dimensional transmutation: a scale emerges from a classically scale-invariant theory
- Below ΛQCD: confinement, chiral symmetry breaking, hadron physics

9State the factorisation theorem. What is separated from what, and why does this separation make LHC cross-section calculations tractable?hints ↓

- σ(Q², τ) = Σᵢⱼ ∫ dz/z Lᵢⱼ(z, Q²) σ̂ᵢⱼ(τ/z, αs, {k})
- Soft/collinear (non-perturbative) physics encoded in PDFs fᵢ(x, Q²)
- Hard scattering σ̂ᵢⱼ is calculable in perturbation theory
- PDF Q²-evolution given by DGLAP equations (perturbative); x-dependence from global fits

10What are PDFs? What physical quantity do they encode, and why are they non-perturbative?hints ↓

- fᵢ(x, Q²): probability density to find a parton of flavour i carrying momentum fraction x at scale Q²
- Non-perturbative: proton structure at low scales involves confinement, no Feynman diagram approach
- Q-dependence is perturbative via DGLAP; x-dependence extracted from global fits to data
- Flavours: u, d, s, c, b, t, ū, d̄, ḡ (+ gluon) — constrained by separate experimental observables

11Why is the large-x region of the gluon PDF particularly interesting for BSM searches? What risk does it pose?hints ↓

- At large x: few partons carry most of the proton momentum → hard scattering at high invariant mass
- High-energy tails of distributions are sensitive to BSM effects parametrised by SMEFT operators
- Risk: a global PDF fit could absorb a BSM signal by deforming the large-x gluon
- This is the core motivation of the thesis: can dijets contaminate the gluon while mimicking OG?

12What is DGLAP evolution? What does it say about how PDFs change with the scale Q?hints ↓

- Dokshitzer–Gribov–Lipatov–Altarelli–Parisi equations: ∂fᵢ/∂ ln Q² = αs/2π Σⱼ Pᵢⱼ ⊗ fⱼ
- Pᵢⱼ: splitting functions — prob. that parton j radiates and becomes parton i
- At higher Q: more soft gluon radiation → gluon PDF rises at small x
- Initial condition (boundary) is non-perturbative and must be fitted from data

13What is the general logic of an EFT? When is it a valid description, and what is the expansion parameter?hints ↓

- EFT valid when E ≪ Λ (new physics scale): heavy degrees of freedom integrated out
- Expansion in E/Λ: corrections are power-suppressed, systematically improvable
- Wilson coefficients Cᵢ encode the UV physics; operators Oᵢ encode kinematics
- Analogy: Fermi theory valid for E ≪ mW ~ 80 GeV; breaks down near mW

14What is the matching procedure? How do you go from a UV theory to its EFT?hints ↓

- Compute the same observable in both the full theory and the EFT
- Equate the two expressions → solve for the Wilson coefficients Cᵢ as functions of UV couplings
- Example: GF/√2 = g²/(8 mW²) matching Fermi to SM electroweak
- Matching is done at scale μ ~ Λ to avoid large logarithms; then run Cᵢ down via RGE

15What breaks down in an EFT at high energies? What are the conditions that must be checked at a collider?hints ↓

- EFT breaks down when E ~ Λ: higher-dimensional operators become equally important
- At LHC: must verify that the kinematic tails (high pT, high Mᵢⱼ) satisfy E ≪ Λ
- Quadratic (1/Λ⁴) contributions may dominate before 1/Λ² is measurable → check hierarchy
- Dimension-8 operators formally same order as (dim-6)² — need to assess their impact

16Why do we truncate the EFT expansion at dimension 6? What appears at dimension 5?hints ↓

- Dimension 5: only the Weinberg operator (L L H H + h.c.) — gives Majorana neutrino masses
- Dimension-5 operators suppressed by 1/Λ; dimension-6 by 1/Λ²
- Odd dimensions break lepton or baryon number → strongly constrained
- Dimension-6 is the first level with rich phenomenology while still systematically controllable

17Write the SMEFT Lagrangian. What are the Wilson coefficients, what is Λ, and what constraints do operators must satisfy?hints ↓

- L_EFT = L_SM + Σᵢ (cᵢ⁶/Λ²) Oᵢ⁶
- Λ: EFT cutoff / mass of new heavy particles integrated out
- cᵢ: dimensionless Wilson coefficients (or dimensionful Cᵢ = cᵢ/Λ²)
- Operators must be Lorentz-invariant AND gauge-invariant under SU(3)×SU(2)×U(1)

18What is the Warsaw basis? What does it mean for a basis to be 'complete' and 'non-redundant'?hints ↓

- Complete: any dim-6 operator is either in the basis or reducible to basis operators via EOM, IBP, Fierz
- Non-redundant: no operator can be written as a linear combination of others in the basis
- 59 independent baryon-number-conserving operators (Grzadkowski et al. 2010)
- Classes: X³, H⁶, X²H², ψ²H³, ψ²XH, ψ²H²D, ψ⁴ (4 types)

19Write the operator OG (triple gluon). Which class does it belong to? What vertices does it affect?hints ↓

- OG = f^ABC G^Aνμ G^Bρν G^Cμρ — the CP-even triple gluon field strength operator
- Class X³ in the Warsaw basis
- Adds corrections to the 3-gluon vertex (and generates additional vertices up to 6 gluons)
- CP-odd analogue Õ_G is constrained by low-energy measurements; CP-even is less constrained

20Why does OG contribute only at O(1/Λ⁴) in gg→gg and gq→gq, not at O(1/Λ²)?hints ↓

- Linear (interference) term: Re(A_SM* × A_OG) must be non-zero for O(1/Λ²) contribution
- Helicity analysis: amplitude involving OG is orthogonal to SM QCD amplitude at tree level
- No interference at O(1/Λ²) for gg→gg and gq→gq (quark mass suppressed for gq)
- Non-zero interference only for 3-jet production or heavy quark (top) final states

21What does the SMEFT predict for the theoretical cross section? Write the decomposition into SM + linear + quadratic terms.hints ↓

- σᵢ^th = σ_SM,i + Σₙ (cₙ/Λ²) σᵢ,ₙ^lin + Σₙ,ₘ (cₙ cₘ/Λ⁴) σᵢ,ₙₘ^quad
- Linear term: interference of SM amplitude with EFT amplitude (order g_EFT/Λ²)
- Quadratic term: |A_EFT|² (order 1/Λ⁴) — formally dim-8 level, but often included
- Including quadratic terms improves sensitivity but risks EFT validity breakdown

22Is SMEFT always a 'good theory'? What are the known limitations and theoretical errors that must be included?hints ↓

- SMEFT assumes E ≪ Λ — violated at high-pT tails in LHC data
- Truncation at dim-6: dim-8 operators formally same order as (dim-6)² terms
- SMEFT theory errors include: scale variation, linear vs quadratic treatment, operator mixing
- Per-mille experimental precision does not translate into per-mille constraints on Cᵢ — theoretical errors dominate

23Why is going to NLO important in SMEFT? What new features appear at one loop?hints ↓

- NLO corrections introduce Wilson coefficients that don't contribute at tree level to a process
- Loop corrections rescale the dependence on Cᵢ — can shift extracted values significantly
- Requires full renormalisation of L₆: renormalisation scheme for new parameters must be defined
- NLO is critical when experimental precision reaches ~10%; mandatory if deviations from SM are seen

24What is the χ² figure of merit used in SMEFT fits? Write the formula and explain each term.hints ↓

- χ²(cₙ) = (1/N_dat) Σᵢⱼ (σᵢ^th − σᵢ^dat) (cov⁻¹)ᵢⱼ (σⱼ^th − σⱼ^dat)
- cov: total covariance matrix including statistical, systematic, and theory uncertainties
- Minimising χ² gives best-fit Wilson coefficients
- Uncertainty on Cᵢ comes from the shape of χ² around the minimum (profile likelihood or MCMC)

25What is the difference between a 'linear fit' and including quadratic EFT corrections? What are the trade-offs?hints ↓

- Linear: only σ_SM + Σ cₙ σₙ — first-order EFT, formally consistent with dim-6 truncation
- Quadratic: adds (cₙ cₘ/Λ⁴) σₙₘ — increases sensitivity but formally includes dim-8-level terms
- Risk: if quadratic terms dominate, the EFT validity condition E ≪ Λ may be violated
- For OG specifically: linear contribution is suppressed (no interference in gg→gg), so quadratic is the only handle

26What is a K-factor? Why is it needed when computing SMEFT predictions for jet production?hints ↓

- K-factor = σ_NLO / σ_LO: ratio that encodes higher-order QCD corrections
- Applied multiplicatively to LO predictions to approximate NLO accuracy without full NLO calculation
- Important for jets: QCD corrections can be O(50–100%) at LHC energies
- Assumed to factorise from EFT corrections in the linear approximation — must be validated

27How can PDFs 'absorb' or 'fit away' BSM physics signals? Give a concrete example from the thesis.hints ↓

- PDFs are extracted from data assuming the SM; if BSM modifies the data, the fit can compensate
- Example: large-x gluon can become softer if top-quark sector EFT operators are included — gluon absorbs the effect
- For OG: di-jet distributions at high Mᵢⱼ shifted by OG contribution; gluon PDF can mimic this shift
- This biases EFT constraints AND contaminates the PDFs with BSM physics simultaneously

28What is a simultaneous fit of PDFs and Wilson coefficients? Why is it better than doing them separately?hints ↓

- Fit PDFs and Cᵢ at the same time from the same dataset, without assuming SM in the PDF extraction
- Avoids double-counting: SM-PDFs already 'absorb' some EFT effects, biasing a subsequent EFT fit
- SIMUnet framework: augments NNPDF neural network with EFT node; outputs PDF + Cᵢ uncertainty simultaneously
- Correlation between Cᵢ and PDF parameters is explicit — can study whether gluon is contaminated

29What is a contaminated fit and what is a closure test? What do they each test?hints ↓

- Contaminated fit: inject fake BSM signal (pseudodata with Cᵢ ≠ 0) and fit with SM assumption → see if signal is absorbed into PDFs
- Closure test: generate pseudodata from known theory (SM or SMEFT) and verify the fit recovers the input → tests the methodology's reliability
- Level 0: pseudodata = central theory values (tests functional form)
- Level 1/2: pseudodata with noise → tests uncertainty propagation and closure under fluctuations

30Why does NNPDF use neural networks as 'unbiased interpolants' for PDFs? What problem does this solve compared to polynomial parametrisations?hints ↓

- Polynomial or functional parametrisations impose shape bias: they can't represent all possible PDF forms
- Neural network: universal function approximator — can represent any smooth function given enough nodes
- Training via gradient descent + Monte Carlo replicas → uncertainty encoded as ensemble spread
- Closure tests validate that the NN can recover the true underlying function from noisy data
