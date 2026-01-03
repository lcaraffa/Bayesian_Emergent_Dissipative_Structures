---
title: "Dissipate to Demonstrate"
subtitle: "Toward a unification between logical incompleteness and thermodynamics of information"
author: "Laurent Caraffa & Claude"
date: "2026-01-03"
status: "Working paper — HIGHLY SPECULATIVE"
---

> *"A formal system that does not dissipate ends up contradicting itself."*

# Abstract

This document proposes a unifying conjecture between three apparently distinct fundamental results:

1. **Gödel's incompleteness theorem** (1931): any sufficiently expressive formal system contains true but unprovable statements.

2. **Landauer's principle** (1961): erasing one bit of information costs at minimum $k_B T \ln 2$ joules.

3. **Prigogine's dissipative structures** (1977): open systems maintain their order by exporting entropy.

**Central conjecture**: These three results are manifestations of the same fundamental principle:

> **A formal system can only maintain its coherence if it is open, dissipative, and recursive. Logical pathologies (incompleteness, undecidability, paradoxes) emerge when a system attempts to close upon itself without dissipation.**

We propose that stable mathematics are necessarily **anchored in physics** — that truth has a thermodynamic cost, and that coherence requires dissipation.

**Keywords**: incompleteness, thermodynamics of information, dissipative structures, foundations of mathematics, Gödel, Landauer, Prigogine.

---

> **Warning**: This document is highly speculative. It proposes deep analogies between traditionally separated domains. These analogies could be fruitful or misleading. The goal is to formulate ideas clearly enough that they can be evaluated, criticized, and eventually refuted.

---

# 1. Introduction: Three Walls

## 1.1 Gödel's wall

In 1931, Kurt Gödel demonstrated that any formal system capable of expressing arithmetic contains true but unprovable statements within the system.

More precisely:

**First incompleteness theorem**: If $S$ is a consistent formal system containing Peano arithmetic, then there exists a statement $G$ such that neither $G$ nor $\neg G$ are provable in $S$.

**Second theorem**: If $S$ is consistent, $S$ cannot prove its own consistency.

**Consequence**: No closed formal system can be both consistent and complete. There are always "holes" — truths inaccessible from within.

## 1.2 Turing's wall

In 1936, Alan Turing demonstrated that the halting problem is undecidable: there exists no general algorithm capable of determining whether an arbitrary program will terminate.

**Consequence**: A computation can run indefinitely without being predictable. Without external intervention (timeout, interruption), some programs never "crystallize".

## 1.3 Landauer's wall

In 1961, Rolf Landauer established that erasing information has an incompressible thermodynamic cost:

$$E_{min} = k_B T \ln 2 \approx 2.9 \times 10^{-21} \text{ J at 300K}$$

**Consequence**: Information is not abstract — it is physical. Manipulating information means manipulating energy. Forgetting costs.

## 1.4 The question

Are these three walls independent, or are they three faces of the same fundamental obstacle?

**Our thesis**: They are linked. Gödel's incompleteness, Turing's undecidability, and Landauer's cost are manifestations of the same principle:

> **A system that does not dissipate cannot remain coherent indefinitely.**

---

# 2. Formal Systems as Structures

## 2.1 What is a formal system?

A formal system $S$ is defined by:
- An **alphabet** of symbols
- **Formation rules** (grammar)
- **Axioms** (starting truths)
- **Rules of inference** (production of new truths)

A formal system is a machine for producing theorems from axioms.

## 2.2 Closed vs open system

**Closed system**: Axioms are fixed once and for all. The system does not interact with the outside. All truth must be derived from within.

**Open system**: The system can receive new axioms, new observations, new constraints. It interacts with an environment.

## 2.3 The thermodynamic analogy

| Formal system | Thermodynamic system |
|---------------|----------------------|
| Axioms | Initial conditions |
| Theorems | Accessible states |
| Proof | Trajectory in state space |
| Incompleteness | Inaccessible states |
| Contradiction | Singularity / explosion |

## 2.4 The reformulated question

Is a **closed** formal system analogous to an **isolated** thermodynamic system?

If so, the second law applies: entropy can only increase. The system tends toward maximal disorder — or, in logical terms, toward incoherence or undecidability.

---

# 3. Incompleteness as a Dissipation Deficit

## 3.1 Gödel's construction

Gödel constructs a statement $G$ that essentially says: "This statement is not provable in $S$."

- If $G$ is provable, then $G$ is false (contradiction)
- If $G$ is unprovable, then $G$ is true (incompleteness)

It's a **self-reference** — the system speaks about itself.

## 3.2 Self-reference as a closed loop

Gödel's statement creates a **closed loop**: the system points to itself, with no exit, no dissipation.

```
S → states G → G speaks of S → S cannot decide → blockage
```

It's a **cycle without dissipation**. Information goes round and round without ever being exported or resolved.

## 3.3 The dissipative conjecture

> **Conjecture 1**: Incompleteness appears when a formal system creates self-referential loops without a dissipation mechanism (exporting information to the outside).

A system that could "dissipate" self-reference — export it to a meta-level, anchor it in an external reality — would avoid the blockage.

## 3.4 Tarski's hierarchies

Tarski (1936) showed that semantic paradoxes can be avoided by stratifying language:

- Level 0: object language
- Level 1: metalanguage speaking about level 0
- Level 2: meta-metalanguage
- ...

This is exactly a **recursive BEDS hierarchy**: each level crystallizes truths that become the axioms of the next level.

**Gödel's incompleteness** says that this hierarchy never terminates — there is always a necessary higher level.

**BEDS reading**: The hierarchy is infinite, but if each level dissipates (crystallizes properly), the system remains coherent. Incompleteness is not a catastrophe — it's the price of openness.

---

# 4. Undecidability as Non-Termination

## 4.1 The halting problem

Turing shows that there exists no program $H$ such that:
- $H(P, x) = 1$ if $P(x)$ terminates
- $H(P, x) = 0$ if $P(x)$ does not terminate

The proof proceeds by diagonalization — another form of self-reference.

## 4.2 Non-termination as infinite cascade

A program that doesn't terminate is a **hierarchy that never crystallizes**:

```
State 0 → State 1 → State 2 → ... → ∞
```

Without dissipation (without an external stopping criterion), computation can descend indefinitely into levels.

## 4.3 Dissipation as timeout

In practice, every real computation has **dissipation**:
- Timeout: we stop after a fixed time
- Bounded resources: finite memory, finite energy
- Human intervention: we decide to stop

These mechanisms are **external dissipations** that force crystallization (even if it's on a "failure" state).

## 4.4 Conjecture on halting

> **Conjecture 2**: A computation that has bounded dissipative resources (energy, time, memory) always terminates. The undecidability of the halting problem is a consequence of idealizing a system without dissipation.

In the real physical world, the halting problem doesn't exist — every computation terminates when energy runs out.

---

# 5. The Cost of Coherence

## 5.1 Landauer and logical irreversibility

Landauer showed that **irreversible** logical operations (like erasure, AND, OR) dissipate heat.

An AND gate:
- 2 bits input → 1 bit output
- 1 bit of information "lost" → at least $k_B T \ln 2$ dissipated

## 5.2 Bennett and reversibility

Bennett (1973) showed that any computation can be made **reversible** (without information loss), and therefore without theoretical dissipation.

But there's a price: you must keep the entire history — **infinite memory**.

## 5.3 The fundamental dilemma

| Option | Memory | Dissipation | Coherence |
|--------|--------|-------------|-----------|
| Irreversible computation | Bounded | Yes | Maintained |
| Pure reversible computation | Infinite | No | Fragile (everything accumulates) |

**Interpretation**: To maintain coherence with finite resources, you must dissipate. Structured forgetting is the price of stability.

## 5.4 Thermodynamic conjecture of coherence

> **Conjecture 3**: The coherence of a formal system operating on a finite physical substrate requires continuous dissipation. The minimum rate of dissipation is related to the complexity of self-references the system must manage.

The more expressive a system is (capable of self-reference), the more it must dissipate to remain coherent.

---

# 6. Unification: The Generalized BEDS Principle

## 6.1 The three conditions of stability

We propose that a stable formal system must satisfy three conditions:

### Condition 1: Openness (O)

The system receives inputs from the outside — new axioms, observations, constraints. It is not closed upon itself.

**Violation** → Pathological self-reference → Paradoxes

### Condition 2: Dissipation (D)

The system exports information to the outside — it forgets, prunes, simplifies. It doesn't preserve everything.

**Violation** → Infinite accumulation → Undecidability / non-termination

### Condition 3: Recursion (R)

The system organizes itself in hierarchical levels. Each level crystallizes truths that become axioms for the next level.

**Violation** → No stable structure → Unmanaged incompleteness

## 6.2 The informal theorem

> **BEDS Meta-Conjecture**: A formal system satisfying conditions O, D and R is **structurally stable**: it may be incomplete (Gödel) but this incompleteness is channeled into the recursive hierarchy. It avoids explosive paradoxes and pathological non-terminations.

## 6.3 Summary table

| System | O | D | R | Observed pathology |
|--------|---|---|---|--------------------|
| Peano arithmetic | ❌ | ❌ | ❌ | Incompleteness (Gödel) |
| Naive set theory | ❌ | ❌ | ❌ | Russell's paradox |
| Turing machine (ideal) | ❌ | ❌ | ❌ | Undecidability (halting) |
| Pure lambda calculus | ❌ | ❌ | ❌ | Non-termination |
| Tarski's hierarchy | ✅ | ❌ | ✅ | Incomplete but structured |
| ZFC (Zermelo-Fraenkel) | ⚠️ | ❌ | ✅ | Independence (CH, etc.) |
| Physical computer | ✅ | ✅ | ✅ | **Stable** (bounded resources) |
| Biological brain | ✅ | ✅ | ✅ | **Stable** (forgetting, sleep) |
| **BEDS network** | ✅ | ✅ | ✅ | **Stable by construction** |

## 6.4 The physicalist interpretation

"Pure" mathematics — idealized formal systems without physical substrate — are structurally unstable. They necessarily develop pathologies (Gödel, Turing, Russell).

**Embodied** mathematics — operating on a physical substrate with dissipation — are stable, but at the price of:
- Incompleteness (there are always inaccessible truths)
- Forgetting (you can't preserve everything)
- Finitude (resources are bounded)

> **Coherence has a thermodynamic cost. Thinking consumes energy. Proving dissipates heat.**

---

# 7. Deep Implications

## 7.1 On the foundations of mathematics

If this conjecture is correct, Hilbert's program (founding mathematics on a complete and consistent formal system) was doomed to failure not only for logical reasons (Gödel), but for **physical** reasons.

A complete and consistent system would be a closed system without dissipation — thermodynamically impossible.

## 7.2 On the nature of truth

Mathematical truth may not be "discovered" in a Platonic heaven — it is **constructed** by dissipative processes.

A proof is a thermodynamic path: it starts from axioms (initial conditions), traverses intermediate states (proof steps), and crystallizes a conclusion (theorem).

The theorem is "true" because it has been **stabilized by dissipation** — the elimination of alternatives, the forgetting of paths not taken.

## 7.3 On intelligence

Intelligence — human or artificial — would be fundamentally a dissipative process:

- **Perceiving**: receiving flow (condition O)
- **Forgetting**: dissipating irrelevant information (condition D)
- **Abstracting**: crystallizing concepts that become priors for the next levels (condition R)

An intelligent system that doesn't dissipate (that preserves everything) becomes **pathological**:
- Perfect memory → inability to generalize
- No forgetting → accumulation of contradictions
- Closed system → psychosis (disconnection from reality)

## 7.4 On current AI

Large language models (LLMs) are **crystallized** systems:
- Trained (dissipative phase)
- Frozen (crystal phase)
- No continuous dissipation

**BEDS prediction**: Frozen LLMs will develop pathologies (hallucinations, inconsistencies) precisely because they no longer dissipate. They are closed formal systems operating on evolving data.

The solution: systems that **continue to dissipate** — continuous learning, structured forgetting, interaction with the environment.

---

# 8. Formalization (Outline)

## 8.1 Definitions

**Definition 1 (Dissipative formal system)**: A dissipative formal system is a tuple $(S, \Phi, \gamma, \pi)$ where:
- $S$ is a classical formal system (alphabet, axioms, rules)
- $\Phi : \text{Env} \to S$ is an input flow (new axioms, observations)
- $\gamma : S \to \mathbb{R}^+$ is a dissipation rate (forgetting, elimination)
- $\pi : S_n \to S_{n+1}$ is a promotion operator (recursive crystallization)

**Definition 2 (Dissipative coherence)**: A system is **dissipatively coherent** if for all time $t$, the informational load $I(t)$ remains bounded:

$$I(t) = I_0 + \int_0^t \Phi(\tau) d\tau - \int_0^t \gamma(\tau) d\tau < I_{max}$$

## 8.2 Formal conjecture

**Conjecture (BEDS Stability)**: Let $(S, \Phi, \gamma, \pi)$ be a dissipative formal system. If:

1. $\gamma > 0$ (strictly positive dissipation)
2. $\limsup_{t \to \infty} \frac{1}{t}\int_0^t \Phi(\tau) d\tau < \liminf_{t \to \infty} \frac{1}{t}\int_0^t \gamma(\tau) d\tau$ (average dissipation exceeds average flow)
3. $\pi$ satisfies the crystallization condition (each level terminates in finite time)

Then $S$ is **dissipatively coherent**: no explosive paradox, no global non-termination.

## 8.3 Link with Gödel

Incompleteness persists: there exist statements $G_n$ at each level $n$ that are not decidable at that level.

But these statements are **promoted** to level $n+1$ where they can (sometimes) be decided.

The hierarchy is infinite, but each level is **finite and coherent**.

> **Incompleteness is the price of openness. Coherence is the fruit of dissipation.**

---

# 9. Objections and Responses

## 9.1 "It's just an analogy"

**Objection**: You make poetic parallels between thermodynamics and logic, but these are not real mathematical correspondences.

**Response**: That's true — for now. This document is programmatic. The rigorous work remains to be done. But analogies have often preceded theorems (thermodynamics → information theory, geometry → relativity).

## 9.2 "Gödel applies even to physical systems"

**Objection**: If a physical computer can simulate Peano arithmetic, it inherits Gödel's incompleteness.

**Response**: Yes, but the incompleteness is **channeled**. The physical computer cannot prove certain things, but it doesn't **crash**. It continues to function, ignoring what it cannot decide. Dissipation allows **living with** incompleteness.

## 9.3 "Pure mathematics works very well"

**Objection**: Mathematicians have been proving theorems for millennia without worrying about thermodynamics.

**Response**: Mathematicians are physical systems. They dissipate (they forget, they sleep, they die). The mathematical community is a collective dissipative structure. Mathematics "works" because it is carried by dissipative beings.

## 9.4 "Quantum physics allows reversible computations"

**Objection**: A quantum computer can in principle compute without dissipation (unitary evolution).

**Response**: Until measurement. Quantum measurement is irreversible and dissipative. And any useful result must be **measured** (extracted to the classical world). Dissipation is unavoidable for **using** the result.

---

# 10. Research Program

## 10.1 Short term

- [ ] Formalize the correspondence between formal systems and thermodynamic systems
- [ ] Rigorously define "logical dissipation"
- [ ] Exhibit examples of stable dissipative formal systems

## 10.2 Medium term

- [ ] Establish a theorem relating dissipation rate and paradox avoidance
- [ ] Quantify the minimal thermodynamic cost of coherence
- [ ] Apply the framework to analysis of proof systems

## 10.3 Long term

- [ ] Unify complexity theory and non-equilibrium thermodynamics
- [ ] Reformulate the foundations of mathematics in a dissipative framework
- [ ] Develop natively dissipative and intrinsically stable AI systems

---

# 11. Conclusion

## 11.1 What we propose

A **unifying conjecture**: the pathologies of formal systems (incompleteness, undecidability, paradoxes) are manifestations of a dissipation deficit.

A stable formal system must be:
- **Open**: receive external flow
- **Dissipative**: export entropy (forget)
- **Recursive**: crystallize into hierarchical levels

## 11.2 What it would change

If this conjecture is correct:

1. **Mathematics is physical** — not just in its implementation, but in its very structure.

2. **Truth costs energy** — demonstrating is dissipating.

3. **Incompleteness is inevitable but manageable** — through dissipative hierarchy.

4. **Stable intelligence requires forgetting** — systems that don't dissipate go mad.

## 11.3 Final word

Gödel showed that formal systems are **incomplete**.

Turing showed that they are **undecidable**.

Landauer showed that information is **physical**.

Prigogine showed that order emerges from **dissipation**.

We propose that these four truths are but one:

> **To think without contradicting oneself, one must forget.**
>
> **To compute without looping, one must stop.**
>
> **To prove without exploding, one must dissipate.**
>
> **Coherence is a dissipative structure.**

---

# References

## Logic and foundations

- Gödel, K. (1931). Über formal unentscheidbare Sätze der Principia Mathematica und verwandter Systeme I. *Monatshefte für Mathematik und Physik*, 38, 173-198.
- Turing, A.M. (1936). On Computable Numbers, with an Application to the Entscheidungsproblem. *Proceedings of the London Mathematical Society*, 42, 230-265.
- Tarski, A. (1936). Der Wahrheitsbegriff in den formalisierten Sprachen. *Studia Philosophica*, 1, 261-405.
- Chaitin, G. (1982). Gödel's Theorem and Information. *International Journal of Theoretical Physics*, 21, 941-954.

## Thermodynamics of information

- Landauer, R. (1961). Irreversibility and Heat Generation in the Computing Process. *IBM Journal of Research and Development*, 5(3), 183-191.
- Bennett, C.H. (1973). Logical Reversibility of Computation. *IBM Journal of Research and Development*, 17(6), 525-532.
- Bennett, C.H. (1982). The Thermodynamics of Computation—A Review. *International Journal of Theoretical Physics*, 21(12), 905-940.
- Zurek, W.H. (1989). Thermodynamic Cost of Computation, Algorithmic Complexity and the Information Metric. *Nature*, 341, 119-124.

## Dissipative structures

- Prigogine, I. (1977). *Time, Structure and Fluctuations*. Nobel Lecture.
- Prigogine, I. & Stengers, I. (1984). *Order out of Chaos: Man's New Dialogue with Nature*. Bantam Books.
- Nicolis, G. & Prigogine, I. (1977). *Self-Organization in Non-Equilibrium Systems*. Wiley.

## Physics and information

- Wheeler, J.A. (1990). Information, Physics, Quantum: The Search for Links. In *Complexity, Entropy, and the Physics of Information*. Addison-Wesley.
- Lloyd, S. (2006). *Programming the Universe*. Knopf.
- Verlinde, E. (2011). On the Origin of Gravity and the Laws of Newton. *Journal of High Energy Physics*, 2011(4), 29.

## Cognition and forgetting

- Friston, K. (2010). The free-energy principle: a unified brain theory? *Nature Reviews Neuroscience*, 11, 127-138.
- Anderson, M.C. & Hanslmayr, S. (2014). Neural mechanisms of motivated forgetting. *Trends in Cognitive Sciences*, 18(6), 279-292.

---

*Highly speculative document. The conjectures presented here are philosophical and programmatic propositions, not established theorems. The objective is to stimulate reflection and open research avenues. All criticism is not only welcome, but necessary.*


