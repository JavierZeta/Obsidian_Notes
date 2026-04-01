Don't ask me why, but it naturally appeared in my life a moment where I'm working on all these topics, don't ask me because I don't know, not because I don't love it . During this time I realized something, there is a common behavior in all these theories, they are screaming the same.

They are screaming  about the absolute.

What would it mean for something to be _absolute_? . We will define it as the following:
If something is truly absolute, it has no complement, no “what it is not,” no boundary drawn against an outside. It is not defined relationally; it does not derive its character by contrast with anything else.

Once you follow the idea carefully through several rigorous frameworks: Shannon’s information theory, thermodynamics, quantum field theory, and the metaphysics of Plotinus, you discover that they all arrive, by their own internal logic, at the same structural conclusion: a truly absolute ground cannot be an _object of knowledge_ in the ordinary sense. Not because it is hidden or complicated, but because the very act of knowing (formal, informational, computational) presupposes the difference that the Absolute lacks.

There is no need to read all the frameworks, because as I said, they are screaming the same,  you can choose your favorites and end with Plotinus.

The point of this essay is not to reduce Plotinus to a historical anticipation of the rest of conclusions of other physicists (well, maybe a bit yes), but to show how these independent frameworks converge on the same precise structural limit. 


## II. Information Is Difference: The Formal Argument

Claude Shannon established information theory, which is central object is **entropy**, and we wont give an obscure insight of what entropy is, as other do for no reason. Let's define it:

Given a discrete random variable $X$ with possible outcomes $\{x_1, x_2, \ldots, x_n\}$ and probability distribution $\{p_1, p_2, \ldots, p_n\}$, the Shannon entropy is defined as:

$$H(X) = -\sum_{i=1}^{n} p_i \log_2 p_i$$

This quantity measures the **average uncertainty** in the outcome — or equivalently, the average amount of information gained when the outcome is revealed. These two descriptions are the same thing: resolving uncertainty is acquiring information.

Now notice what happens at the extremes:

- **Maximum entropy**: when all outcomes are equally probable ($p_i = 1/n$ for all $i$), $H = \log_2 n$. Nothing is known in advance; every outcome is maximally surprising. Each observation yields the most information possible.

- **Zero entropy**: when one outcome is certain ($p_j = 1$ for some $j$, all others zero), then $H = -1 \cdot \log_2(1) = 0$. There is no uncertainty to resolve. Every observation yields no information,  you already knew the outcome.

The zero-entropy case is the mathematically precise description of something that admits no alternatives, no surprise, no distinction between "what happened" and "what could have happened." It is perfectly *determined* — not in the sense of being mechanistically caused, but in the sense of being the *only possibility*.

Here is the clave: information, in Shannon's framework, is not a property of a state in isolation. It is a property of a **probability distribution over a set of distinguishable states**. Before you can have entropy, you need two things: (1) a collection of mutually distinct possibilities, and (2) a measure over them. Information is structurally *diacritical*, it lives in the space between one possibility and another.

This means: **if there are no "other possibilities," the concept of information does not apply.** Not in the sense that information is zero, but in the sense that the framework itself fails to get traction. Shannon entropy presupposes that you have already defined a set of distinguishable states. If what you are examining is prior to that distinction — if it is, in some sense, what makes all distinctions possible , then asking "what is its Shannon entropy?" is like asking "what is the weight of Tuesday?" The question is malformed.

The Absolute, understood as something without complement, without alternative, without internal differentiation stands outside the framework as its unacknowledged presupposition.

## III. A Sharper Edge: Kolmogorov Complexity and the Limits of Description

There is another formal framework worth examining here, because it illuminates a different facet. Kolmogorov complexity defines the **complexity** of a binary string $x$ as the length of the shortest program $p$ that, run on a universal Turing machine $U$, outputs $x$:

$$K(x) = \min_{p : U(p) = x} |p|$$

A string is *incompressible* — and therefore maximally complex — if $K(x) \approx |x|$: no program shorter than the string itself can produce it. It has no regularities, no structure that can be exploited for compression. This is, in a precise sense, the definition of algorithmic randomness.

It is tempting to think: perhaps the Absolute is incomprehensible in this sense, infinitely complex, requiring infinite information to describe. But this would be wrong.

The Absolute, precisely because it lacks internal differentiation, cannot be discretized. Not because it is too complex to fit in a string, but because it has no *features* to encode. A projection of the Absolute into a domain (strings, symbols, differences),  that is foreign to its nature.

## IV. Thermodynamics: Work, Gradients, and the Self-Sealing Boundary

The connection between information and physics is not merely analogical, it is exact. Landauer's Principle establishes that any logically irreversible computation necessarily dissipates at least $k_B T \ln 2$ of energy as heat. Information processing is a physical process; it requires energy gradients and produces entropy as an unavoidable by-product. Logic and thermodynamics are the same thing described in different languages.

The deeper principle is Carnot's: the maximum efficiency of any heat engine operating between temperatures $T_h$ and $T_c$ is:

$$
\eta_{\text{Carnot}} = 1 - \frac{T_c}{T_h}
$$

If $T_h = T_c$, then $\eta = 0$. No work can be extracted from a perfectly uniform thermal bath, regardless of how much total energy it contains. Without a gradient, nothing happens. This is the thermodynamic version of the same structural point made in the previous section: difference is not a feature of the world, it is the condition of possibility for there being a world of processes at all.

The heat death, the state of maximum entropy toward which all isolated systems evolve is the Absolute?. 

It is a specific, contingent physical state, still embedded in space, time, and the laws of physics. It is "dead" in the sense that nothing happens in it, but it is still a state of something. The Absolute, as we are examining it, is not a terminus within physics but what makes the existence of physical states possible in the first place.

That said, thermodynamics has something far more precise to say about its own undifferentiated limit, and this is where a recent result tightens the argument considerably.

For over a century, thermodynamics rested on three laws. The third — Nernst's theorem, that entropy exchanges approach zero as temperature approaches absolute zero, entailing that $T = 0$ is physically unreachable — was treated as an independent empirical postulate. Einstein himself argued it must be separate: since a machine capable of reaching absolute zero would violate the second law, the unattainability of $T = 0$ had to be a brute additional fact about the world, not derivable from the second law alone. The debate between Nernst and Einstein on this point remained unresolved for over a hundred years.

In 2025, physicist José María Martín-Olalla demonstrated that Einstein was wrong here, and I had the honor of listening to him explain it in a recent congress. By introducing the concept of a virtual Carnot engine, a thermometer formally required by the second law's own definition of temperature, but which performs no physical cycle and therefore violates nothing. He showed that the unattainability of absolute zero follows as a logical consequence of the second law itself. The third law is not independent; it is a theorem of the second.

The philosophical significance of this is exact and non-trivial. The second law is the fundamental law of differentiated physical reality, it governs every process, every gradient, every flow of energy and information. What Martín-Olalla's result reveals is that this law, unfolded with sufficient care, internally generates the inaccessibility of its own undifferentiated limit. Absolute zero — the state prior to all thermal gradients, prior to all thermodynamic processes — is not blocked by a separate wall erected from outside. The law of difference itself, by its own logic, seals the boundary against what precedes difference.

This is a stronger statement than "we cannot reach the undifferentiated ground." It says the laws governing the differentiated world carry, in their own formal body, the proof that the undifferentiated ground lies beyond them. The framework does not merely fail to reach its limit — it formally prohibits itself from doing so. As we will see, Plotinus argues for exactly this structure at the level of thought: not that the One is difficult to reach, but that the very act of cognition, by its own logic, reinstates the distance from the One that it is trying to close.

---

## V. Quantum Field Theory: The Ground That Has Structure

Quantum Field Theory (QFT) tells us that particles are not primary fields are. The electron is not a small hard object; it is a localized excitation, in an underlying electron field that extends across all of spacetime. The photon is an excitation of the electromagnetic field. Everything we call "matter" is, in QFT, a pattern of activity in something more fundamental.

The vacuum state $|0\rangle$ is the lowest-energy state of this underlying field structure — the state with no excitations, no particles. One might expect this to be the closest physics gets to "nothing." It is not.

Even in the vacuum, each field mode contributes a non-zero ground-state energy of

$$
\frac{1}{2}\hbar\omega
$$

a direct consequence of the uncertainty principle. The vacuum is not quiet. It is filled with quantum fluctuations: transient, correlated disturbances in field amplitudes that are physically real and measurable.

The Casimir effect, a small but precisely measured attractive force between two uncharged conducting plates in a vacuum, arising from the modification of vacuum fluctuations between them, is direct empirical evidence of this. 

The vacuum is therefore too far from nothing: a structured, active, constrained substrate from which all particles emerge as excitations.

The QFT vacuum, then, is the Absolute?.

It is the closest thing within physics to an absolute ground, but it is still defined relative to a Hamiltonian, a reference frame, a set of field equations. It has structure, observer-dependence, broken symmetry. Physics keeps finding ground beneath ground: look below particles and find fields; look at the field ground state and find vacuum fluctuations; look at those and find symmetry-breaking dynamics.

**Spontaneous symmetry breaking** illustrates how difference itself arises from a more symmetric ground. The Higgs field, simplified, evolves in a "Mexican hat" potential — symmetric around its maximum at $\phi = 0$, with a ring of true minima at $|\phi| = v$. The fully symmetric state is an *unstable* equilibrium. The universe settled into one of the asymmetric minima, and from that settling emerged the mass of the electron, the $W$ and $Z$ bosons, the distinction between electromagnetism and the weak force. The differences that constitute the physical world are daughters of broken symmetry — features of the particular vacuum we inhabit, not features of the underlying field equations.
![[Pasted image 20260313124552.png|637]]

That is crazy to be honest, because it is giving us an insight on how the perfectly homogeneous symmetrical object  could be unstable, and how it breaks into differentiable parts, and exactly there, is where physics starts.

## VII. Plotinus and the One

Plotinus (204–270 CE) is the founder of Neoplatonism and, arguably, the most rigorous metaphysician of antiquity after Aristotle. His *Enneads* — 54 philosophical treatises organized by his student Porphyry after his death — constitute a systematic philosophical cosmology built around a single central concept: **the One** (τὸ Ἕν, *to Hen*).

It is worth noting that Plotinus was not a mystic in the sense of someone making claims based on emotional experience alone. He was a philosopher working in the tradition of Plato, extending Plato's thoughts about the supreme Idea with rigor. The *Enneads* are difficult, technical, and argumentatively dense. Plotinus's conclusions about the One are not poetic gestures, they follow from careful analysis of what it means to think, to know, and to be.

### The Three Hypostases

Plotinus's system describes reality as organized into three fundamental levels or "hypostases":

1. **The One** (τὸ Ἕν): The first and highest principle, the source of all that is.
2. **Intellect** (Νοῦς, *Nous*): The second hypostasis, the realm of pure thought thinking itself, the home of the Platonic Forms.
3. **Soul** (Ψυχή, *Psyche*): The third hypostasis, which generates and animates the physical world.

Each lower hypostasis "proceeds" (πρόοδος, *proodos*) from the higher through a kind of overflow or emanation — not a temporal event but a logical/ontological dependence. The physical world is the lowest expression of this chain.

The One is not one *thing among others*. It is not a being in the ordinary sense. It is the source of being. And this distinction, between *being* and *the source of being*, is the center of the argument.

### The One Cannot Think Itself

Plotinus makes a startling argument in *Ennead* V.3 (titled "On the Knowing Hypostases and the Transcendent"): **the One cannot think itself.** This is not a limitation but a consequence of what the One is.

Thinking requires a structure of *subject* and *object* — a thinker directed toward something thought. Even self-thought (thinking about oneself) involves a distinction between the thinking aspect and the thought-about aspect. Intellect (Nous), the second hypostasis, is precisely defined as thought thinking itself — a rich, self-referential structure in which the Forms are both the content of thought and the thinker. But this self-referential richness *already implies multiplicity*: there is the thinking, the thought, and the thought-about, and these are not simply identical.

As Plotinus writes in *Ennead* V.3.13 (Armstrong translation):
> "That which is before Intellect is not Intellect... if one grants that Intellect knows itself, it still needs to be asked whether in knowing itself it finds itself simple or has some multiplicity in itself... but then would not the First need to be something other than Intellect?"

The One, being absolutely simple — without internal division, without multiplicity — cannot sustain the subject/object structure that cognition requires. Therefore the One does not think. It is not *beneath* thinking; it is *beyond* it. 

This is not an arbitrary claim. It follows from a strict analysis: **any act of cognition requires distinguishing the knower from the known.** The One, being indivisible, cannot be caught in this structure — not as knower, not as known.

### The One Is Beyond Being

For Aristotle and for common sense, "to be" is the most basic predicate. Everything that exists, exists in some way. But Plotinus follows Plato's lead from the *Republic* (509b): the Form of the Good is described as "beyond being" (ἐπέκεινα τῆς οὐσίας), exceeding being in dignity and power. Plotinus takes this seriously and radicalizes it.

Being, for Plotinus, is already a kind of determination — a "this rather than that." To be something specific is to be bounded, to have a nature that distinguishes you from other natures. Even the most abstract being is still a *kind* of being — and that kind-ness is already a form of difference.

The One, as the source of all being, cannot itself be a being — that would make it one thing among the things it generates, dependent on the same ontological structure it is supposed to ground. In *Ennead* VI.9.3 (Armstrong translation), Plotinus writes:

> "The One is perfect because it seeks nothing, has nothing, needs nothing; and being perfect, it overflows, as it were, and its superabundance makes something other than itself. What has come into being from it turns towards it and is filled, and looking towards it becomes Intellect."

Notice the logical structure here: the One does not *create* by deliberate choice (that would require the One to have a "before" and "after," a need and a fulfillment). It *overflows* by necessity of its own nature. The generation of multiplicity from the One is not an event in time but a logical consequence of what the One is — namely, something so "full" that being cannot be contained in it, and so multiplicity must proceed from it.

### Apophasis: Knowing by Unknowing

Because the One is beyond being and beyond thought, Plotinus is forced into what the tradition calls **apophasis** (ἀπόφασις) — negative theology. We cannot say what the One *is*, only what it *is not*.

In *Ennead* V.3.14, Plotinus states this with full clarity:
> "Since the nature we are speaking of is one and simple and first of all, it has no description (logos). A description requires a middle term, and a middle term requires that the two extremes already be known. But the First has no 'other side.' We approach it by taking away everything else."

And in *Ennead* VI.9.6:
> "We are in agony to find the right description. We do not say it is this or that; we run over all things and do not name it; at last, passing beyond all others, we are left with this: we call it the One, wishing to indicate to each other what is beyond predication."

What is remarkable about this passage is that the word "One" is not, for Plotinus, a positive description. It is the minimum possible designation , the attempt to gesture at what is left when all positive content is removed. Calling it "One" is not saying that it has the property of unity (as opposed to being a multiplicity). It is saying: when you have stripped away all multiplicity, all form, all difference, all being — whatever remains, *that* is what we are pointing at.

This is the via negativa at its most rigorous: not a rhetorical device but a logical consequence of the analysis. You cannot describe the One in positive terms because description requires the structure of difference, and the One is prior to that structure.

### The Regress Argument: Why the One Must Exist

Plotinus also provides arguments for *why* the One must exist, not merely arguments about its nature. The central one is a regress argument that resonates directly with the information-theoretic discussion above.

Any composite thing — anything that has parts, that is a *this and that* — is what it is by virtue of its parts and their relation. The parts are, in some sense, prior to the composite. For instance, an organism is explained by its organs; the organs by their cells; the cells by their chemistry; the chemistry by the atoms. But at each stage, we have *more things*, not fewer. Explanation has not terminated; it has merely multiplied.

Plotinus's insight is that this regress is not vicious only if it terminates in something that is **not a composite at all** — something that is genuinely simple, that has no parts in terms of which it is to be explained. And this terminus must be self-subsistent: it cannot derive its being from anything prior, because if it did, *that* prior thing would be the real terminus. The One, being perfectly simple — no internal division, no structure, no multiplicity — does not depend on parts. It is the first term in the chain, the term for which the question "what makes *it* what it is?" does not arise, because "what it is" is not constituted by anything other than itself.

In the language of modern mathematics, the One is something like a **fixed point of the ontological structure** — a point at which the operator "explain in terms of prior components" has no further application, because there are no prior components.

---

## VIII. Convergence: The Same Structure, Four Times

We are now in a position to see what is actually going on when these frameworks are laid side by side. The parallels are not superficial — they are structural. Each framework independently arrives at a specific kind of limit: a point beyond which its own methods cannot reach, and which its internal logic nevertheless demands.

| Framework | What requires difference | What "absolute ground" looks like | Why the absolute is unreachable |
|---|---|---|---|
| **Shannon Information Theory** | Entropy requires a probability distribution over distinguishable states | Zero-entropy state: no uncertainty, no information | The framework needs a pre-given set of states to operate; the absolute is prior to that set |
| **Thermodynamics** | Work requires a gradient; computation requires free energy | Perfect thermodynamic equilibrium: no gradients, no processes | Any physical process is an act of differentiation; the undifferentiated ground cannot participate in processes |
| **Quantum Field Theory** | Particles are excitations above a ground state; the ground state has structure | The vacuum: lowest-energy state, but not "nothing" — it has structure, is relational | The vacuum is itself defined relative to a Hamiltonian and reference frame; the truly undifferentiated would be prior to the field equations |
| **Plotinus / Neoplatonism** | Cognition requires subject/object distinction; being requires determination | The One: prior to being, prior to thought, prior to multiplicity | Thought cannot reach the One because thought is already a departure from it |

What is structurally identical across all four cases?

**The absolute ground is not an object within the framework — it is the condition for the framework having objects at all.**

Shannon entropy is not a property of *the source of all signal*; it is a property of signals. Thermodynamic gradients are not features of *the ground of all physical processes*; they are features of processes. The QFT vacuum is not a particle, but it is still a state defined within the theory. The One is not a being among beings.

In each case, the framework is powerful and precise *within its domain* — but its domain presupposes differences, and the absolute is precisely what is prior to difference. The framework's power comes from its ability to handle differences rigorously. And that same power is what prevents it from reaching what precedes difference.

## X. Epistemological Consequences: The Shape of What Cannot Be Known

If the argument above is correct, it has a precise epistemological consequence: **the Absolute cannot be known in the mode in which objects are known.** Not because of a contingent limitation — insufficient data, inadequate instruments, insufficient mathematical machinery — but because the very structure of objective knowledge requires the difference that the Absolute lacks.

Now that I'm finishing this text, I just realize that maybe is not that deep what I'm saying and actually is quite obvious, I'm just saying that each framework is analyzing the location of their own boundary , but i felt that during the process we could see some abstract similarities.

But there is a further point that Plotinus makes, and which deserves consideration: the boundary itself can be a kind of access. In *Ennead* VI.9.7-8, Plotinus describes a mode of "contact" with the One that he calls not *gnosis* (knowledge) but *henosis* (union). This is not union in the sense of dissolution — the individual is not destroyed — but a kind of direct coincidence in which the distinction between knower and known momentarily collapses. Plotinus describes it as the closest we can come to the One: not knowing it, but *being* it, insofar as that is possible for something that is already not-the-One.

Whether one takes this phenomenological/experiential claim seriously is a separate question. What matters here is the logical structure: if the One is prior to the subject/object distinction, then the closest approach to the One is not through refined observation or better theory but through the *suspension* of the subject/object distinction. This is the inverse of what formal knowledge does. Formal knowledge sharpens the distinction; the approach to the One dissolves it.

---

## XI. On the Question of Why

One more piece of the original question deserves careful treatment: not just *what* the Absolute is, but *why it should exist at all*.

The information-theoretic and thermodynamic frameworks offer what might be called a **structural necessity argument**. Differences — bits, gradients, distinctions — do not explain themselves. A bit is a bit *relative to* a channel, a message, a receiver. A gradient is a gradient *relative to* a background. Explanation proceeds by relating things to other things. But this relational chain cannot be self-sustaining unless there is something that is not itself relational — not explained by something further, not defined by its contrast with something else.

This is the old *cosmological argument* in a new key, stripped of its theistic specificity. You do not need to conclude from this that the Absolute is a person, a creator, or anything with familiar properties. You only need to conclude that **if the relational web of differences is not to be a free-floating structure with no terminus, there must be something that stands outside the web as its ground.** The regress of "A is explained by B, B by C" either terminates or it doesn't. If it doesn't, nothing is ultimately explained as Aristotle said,the chain of explanations is infinite and therefore never reaches solid ground. If it does, the terminus is precisely something that has no further "because" behind it, no further relational explanation — something that is, in the root sense, absolute.

Plotinus's elegant addition to this argument: the One does not *decide* to generate multiplicity, does not *choose* to be the source of being. It generates multiplicity as a logical consequence of its own completeness. A lamp does not decide to illuminate; illumination follows from what a lamp is. The One is like a lamp that cannot *not* illuminate — and what it illuminates, by its presence and through the mediation of Intellect, is the entire structure of being, thought, and physical reality.

---

## XII. Conclusion: The Precision of the Limit

We began with a question: what would it mean for something to be absolute, unconditioned, beyond difference? We have followed that question through four rigorous frameworks.

Shannon's information theory: the concept of information is constitutively dependent on difference. A ground prior to difference is prior to information. It is not a source of zero bits; it is prior to the bit/non-bit distinction.

Thermodynamics: work, computation, and physical process are all forms of difference-exploitation. The ground of physical processes cannot be a physical process. The second law points toward equilibrium; the question of what grounds the non-equilibrium initial conditions is thermodynamically unanswerable.

Quantum Field Theory: the vacuum is richer and stranger than "nothing," with structure, observer-dependence, and broken symmetry. The most symmetric possible ground state is unstable; the differentiated world emerges from symmetry-breaking. 

Plotinus: the One is prior to being, prior to thought, prior to multiplicity. It is not a being among beings but the source of being. It can be approached only through negation — by removing all positive content until what remains is the indefinite residue that resists removal. And even this residue cannot be grasped *as an object* — it can only be approached as a limit.

What is remarkable is not that these frameworks say the same thing in different ways. What is remarkable is that each of them *had to* say it. The conclusion is not imported from outside — it arises from the internal pressure of each framework's own logic when pushed to its foundations. The One, the vacuum, the zero-entropy ground: these are not answers invented to satisfy a prior desire for absolutes. They are the shadows cast on the boundary of formal knowledge by the structure of formal knowledge itself.

To follow a formal system to its limit and find there a horizon that the system cannot cross — that is not the failure of rigor. It is rigor's most honest achievement.





















 


---


