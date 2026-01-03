---
title: "Bayesian Emergent Dissipative Structures"
subtitle: "Outline of a theory of frugal emergence v:0x40"
author: "Laurent Caraffa"
date: "2026-01-02"
pdf-engine: xelatex
geometry: margin=3cm
mainfont: "DejaVu Serif"
monofont: "DejaVu Sans Mono"
mathfont: "DejaVu Math TeX Gyre"
---

> *What do a river and a neural network have in common? They can both be formalized as Bayesian Emergent Dissipative Structures. Could this paradigm be the path toward frugal and sustainable AI?*

# Abstract

This work proposes a unifying framework between the thermodynamics of dissipative structures (Prigogine, 1977) and geometric Bayesian inference (Amari, 1998). The central thesis: **learning — whether it be a river carving its bed or a neural network adjusting its weights — can be re-described as a single fundamental process of converting flow into structure by exporting entropy**.

A **mathematical isomorphism** is established between thermodynamic crystallization and Bayesian convergence. This formal correspondence — between thermodynamic free energy ($F = E - TS$) and variational free energy ($\mathcal{F} = D_{KL}(q\|p) - \mathbb{E}_q[\log p(D|\theta)]$) — opens the way to transposing concepts between the two domains, although their direct physical identification (for example, measuring a "crystallized bit" in joules) remains an open question.

**Central conjecture**: Under the Laplace approximation (locally quadratic free energy) and when the Fisher metric varies slowly, the natural gradient trajectory approximates a geodesic of the statistical manifold. It is in this regime that the convergence path would be both optimal (least informational action) and geodesic.

This unification allows formalizing **recursive emergence**: crystallized posteriors become the priors of subsequent structures, forming a hierarchy where each level restricts the space of possibilities and reduces the cost of learning.

**Energy bound**: A major consequence of the BEDS framework is the possibility of bounding a priori the energy consumption of a learning network. If each level of the hierarchy crystallizes (reaches its basin of attraction), then the series of costs converges: $E_{total} = \sum E_n < \infty$. We propose a class of problems — Networks of Bayesian Emergent Dissipative Structures (NBEDS) — that guarantee this bound by construction.

**Implementation**: We show that a peer-to-peer network where each node is a BEDS can be instantiated on very low power microcontrollers, powered by solar energy, and operate indefinitely. Bayesian fusion — the minimal operation on the statistical manifold — requires only about ten operations per update, making possible continuous distributed learning with an energy footprint five orders of magnitude lower than existing "AI blockchain" infrastructures.

**Inspirations**: This work has four major sources of inspiration. The first is Yann LeCun's vision of predictive architectures with joint embeddings, presented in *A Path Towards Autonomous Machine Intelligence* (LeCun, 2022), complemented by the theoretical foundations of *LeJEPA* (Balestriero & LeCun, 2025) — the latter establishing that the isotropic Gaussian distribution is optimal for embeddings, a result that resonates with our conjecture on thermodynamic optimality. The second is *Thermodynamics of Evolution* by François Roddier (2012), which applies Prigogine's principles to biological and social systems, and whose reading profoundly oriented this work toward a unified vision of dissipative structures at all scales. The distributed architecture is also inspired by the Polkadot network (Wood, 2016), whose model of interoperable parachains offers a precedent for emergent consensus hierarchies — although our approach substitutes cryptographic proof with Bayesian convergence. The last is the book Gödel, Escher, Bach: An Eternal Golden Braid which explores, through logic, art and music, how formal systems can generate self-reference, consciousness and meaning.

Bayesian Emergent Dissipative Structures could constitute a fertile theoretical framework for the continuation of this work.

**Keywords**: dissipative structures, Bayesian inference, information geometry, variational free energy, natural gradient, emergence, energy bound, peer-to-peer networks, crypto.

---

> **Note:** this document is a whitepaper presenting working notes. Some parts may be incomplete or contain errors. The state of the art presented is not exhaustive, and it is very likely that some reflections presented here have already been formulated elsewhere. This document aims to share ideas and reflections in progress and is not intended to be definitive.
> 


# Introduction: The River and the Network

What do a river and a neural network have in common?
They can both be formalized as Bayesian Emergent Dissipative Structures. Couldn't using this paradigm lead toward frugal and sustainable AI?


## Water that learns

Imagine a drop of water falling on virgin terrain. It could go anywhere — maximum uncertainty. It flows, erodes, chooses a path. Then another drop, then another. Each passage carves certain channels a bit deeper, abandoning others.

The bed forms.

Now the arriving water "knows" where to go — uncertainty about the path has been absorbed by the structure. What the river has learned is the relationship between its input (rain) and its output (the sea), inscribed in rock.

The price paid: energy dissipated as heat and erosion.

---

## The network that learns

A neural network does exactly the same thing. Data arrives in a space of random parameters — it could produce anything. It flows through, weights adjust, certain paths strengthen. Valleys are carved in parameter space.

In the end, the network "knows": this input gives this output.

The price paid: CPU cycles dissipated as heat.

---

## The same story

|                           | River                        | Neural network                |
|---------------------------|------------------------------|-------------------------------|
| **Flow**                  | Water                        | Data                          |
| **Terrain to sculpt**     | Geology                      | Parameter space               |
| **Erosion**               | Friction on rock             | Weight updates                |
| **Learned structure**     | Riverbed                     | Found minimum (valley)        |
| **What is represented**   | Path of least resistance     | Input → output function       |
| **Exported entropy**      | Heat, sediments              | Heat (CPU/GPU)                |

In both cases, **learning is converting flow into structure by exporting entropy**.

This intuition is not just a poetic metaphor. It is based on established results in non-equilibrium thermodynamics (Prigogine & Stengers, 1984), information theory (Shannon, 1948), and information geometry (Amari & Nagaoka, 2000).

---

## A re-description of learning

From the most general thermodynamic point of view, what we call "learning" can be re-described as a special case of dissipative self-organization. There would be no specific mechanism for learning — only dissipative structures doing what all dissipative structures do: maintain their internal organization by exporting entropy to their environment.

The river doesn't "decide" to learn geology — it cannot do otherwise. The neural network doesn't "decide" to learn the data — it's simply what happens when a flow passes through an open structure.

This re-description doesn't deny the specificity of biological or computational adaptive mechanisms — it proposes a broader unifying framework in which to situate them.

---

## The shortest path

The Bayesian framework captures the essence of this process:

- **At the beginning**: water could go anywhere — maximum uncertainty
- **During**: each drop reduces possibilities, the bed is carved
- **At the end**: a single path dominates — maximum certainty

The Bayesian is the ideal river: it carves only what the water forces it to carve, nothing more.

**Central conjecture**: Under the Laplace approximation (locally quadratic free energy) and when the Fisher metric varies slowly, the natural gradient trajectory approximates a geodesic of the statistical manifold. It is in this regime that the convergence path would be both optimal — in the sense of least informational action — and geodesic.

A real river dissipates more: it must rub against rock to exist. The gap between the ideal Bayesian and the real river is the **cost of incarnation** — the price to pay for existing in the physical world.

---

## The mill that emerges

Now that the bed exists, something new becomes possible.

Water flows predictably — it's free energy, available. A mill can attach itself. It couldn't have existed before: without a stable bed, where would it have been built? On what flow would it have counted?

The mill is itself a dissipative structure. Water passes through it, gears turn, wear out, adjust. At first, it squeaks, it jams. Then the pieces find their place, the rhythm stabilizes. The mill has learned to convert current into rotation.

The price paid: friction, wear, heat.

But once crystallized, the mill in turn releases energy — a regular, exploitable rotation. A blacksmith sets up shop. His forge learns iron: what temperatures, what gestures, what rhythms. It crystallizes. Its tools, once forged, allow digging channels, improving the bed, building other mills.

The loop closes. Or rather: it rises.

```
Rain (maximum uncertainty)
    │
    ▼
Riverbed ──── crystallizes ──── → stable current (free energy)
                                        │
                                        ▼
               Mill ──── crystallizes ──── → rotation (free energy)
                                                    │
                                                    ▼
                          Forge ──── crystallizes ──── → tools
                                                          │
                                                          ▼
                                                        ...
```

Each structure can only exist because the previous one has crystallized. The mill inherits an axiom: "water flows here, at this rate". It doesn't have to learn it — it's acquired, inscribed in rock. Its space of possibilities is already restricted, and that's precisely what allows it to exist.

This is recursion: **the crystallized posterior becomes the prior of the next structure**.




## What follows

The theory that follows formalizes this intuition. It establishes that:

1. Structures that learn can be described as dissipative systems
2. Under certain conditions (Laplace approximation), these systems follow the optimal Bayesian path
3. Crystallized structures become the foundations of subsequent ones

The river carves its bed. The bed guides subsequent rivers. And so on, until an entire network of valleys emerges — each level building on the previous.

---

# Part I — Foundations: The Dissipative Structure

## 1.1 Definition

A **dissipative structure** is a concept introduced by Ilya Prigogine (Nobel Prize in Chemistry, 1977) to describe open systems that maintain their organization by exchanging energy and matter with their environment.

Formally, a dissipative structure S is an open system that:
- Absorbs an incoming flow Φ_in
- Maintains internal order (negentropy N)
- Exports entropy H to the environment

```
Φ_in → [S] → H_out
         │
         └─ N (maintained order)
```

## 1.2 The entropic balance

The second law of thermodynamics imposes:

$$\frac{dS_{total}}{dt} \geq 0$$

For a dissipative structure, we decompose:

$$\frac{dS_{system}}{dt} = \frac{dS_{internal}}{dt} + \frac{dS_{exchange}}{dt}$$

where:
- $\frac{dS_{internal}}{dt} \geq 0$ (irreversible production)
- $\frac{dS_{exchange}}{dt}$ can be negative (negentropy import)

The structure can maintain or increase its order ($dS_{system} < 0$) if and only if it exports enough entropy to the environment.

## 1.3 Existence condition

A dissipative structure exists as long as:

$$\Phi_{in} > \Phi_{min}$$

where $\Phi_{min}$ is the minimum flow needed to compensate for internal entropy production. Below this threshold, the structure disorganizes and disappears.

## 1.4 Canonical examples

| System | Incoming flow | Maintained order | Exported entropy |
|--------|---------------|------------------|------------------|
| Bénard cell | Heat (gradient) | Convection rolls | Heat (top) |
| Living cell | Nutrients, ATP | Cellular structure | Waste, heat |
| Hurricane | Ocean heat | Organized vortex | Heat (altitude) |
| River | Water (rain) | Structured bed | Sediments, heat |

---

# Part II — Information Geometry

## 2.1 The space of distributions

Consider the set of probability distributions over a space $\mathcal{X}$. This set forms a **statistical manifold** $\mathcal{M}$ — a curved space where each point represents a distribution.

For a parametric family $p(x|\theta)$, the parameters $\theta \in \mathbb{R}^n$ serve as coordinates on this manifold.

## 2.2 The Fisher metric

The natural distance on this manifold is given by the **Fisher metric**:

$$g_{ij}(\theta) = \mathbb{E}_{p(x|\theta)}\left[\frac{\partial \log p(x|\theta)}{\partial \theta_i} \frac{\partial \log p(x|\theta)}{\partial \theta_j}\right]$$

This metric measures local distinguishability between neighboring distributions. It is:
- **Intrinsic**: does not depend on the chosen parameterization
- **Unique**: it is the only reparameterization-invariant Riemannian metric (Chentsov's theorem)

## 2.3 The natural gradient

The ordinary gradient $\nabla L(\theta)$ points toward the steepest descent direction in the Euclidean space of parameters. But this is not the right space — it's the space of distributions that matters.

The **natural gradient** corrects this error:

$$\tilde{\nabla} L(\theta) = G(\theta)^{-1} \nabla L(\theta)$$

where $G(\theta)$ is the Fisher matrix.

The natural gradient points toward the steepest descent direction in distribution space — the direction that changes the distribution the most, not the parameters.

## 2.4 Geometric interpretation

| Concept | Euclidean space | Distribution space |
|---------|-----------------|-------------------|
| Distance | $\|\theta_1 - \theta_2\|^2$ | $D_{KL}(p_1 \| p_2)$ (local) |
| Optimal direction | $-\nabla L$ | $-G^{-1}\nabla L$ |
| Metric | Identity | Fisher matrix |
| Invariance | No | Yes (reparameterization) |

## 2.5 Geodesic convergence principle

A **geodesic** is the shortest path between two points on a curved manifold. On the statistical manifold, geodesics minimize Kullback-Leibler divergence.

**Conjecture**: Under the Laplace approximation (locally quadratic cost function) and when the Fisher metric varies slowly, the natural gradient trajectory approximates a geodesic of the statistical manifold. It is in this regime that the convergence path would be both optimal (least informational action) and geodesic.

In general, the natural gradient trajectory is not exactly a geodesic. But in the Laplace approximation regime, this approximation becomes relevant and provides the central geometric intuition of the proposed framework.

---

# Part III — The Fundamental Correspondence

## 3.1 Two free energies

**Thermodynamics** (Helmholtz):
$$F = E - TS$$

where $E$ is internal energy, $T$ temperature, $S$ entropy.

**Variational inference**:
$$\mathcal{F} = D_{KL}(q(\theta) \| p(\theta)) - \mathbb{E}_{q}[\log p(D|\theta)]$$

where $q(\theta)$ is the variational distribution, $p(\theta)$ the prior, $D$ the data.

## 3.2 The proposed isomorphism

The framework uses a formal correspondence — a mathematical isomorphism — between these two formalisms:

| Thermodynamics | Bayesian inference |
|----------------|-------------------|
| Internal energy $E$ | Negative log-likelihood $-\log p(D|\theta)$ |
| Entropy $S$ | Entropy of $q(\theta)$ |
| Temperature $T$ | Regularization parameter $\beta^{-1}$ |
| Free energy $F$ | ELBO (negative) |
| Thermal equilibrium | Optimal posterior |
| Thermal fluctuations | Epistemic uncertainty |

## 3.3 Status of this correspondence

This correspondence is **mathematically suggestive** and allows transposing intuitions and tools from one domain to another. However, it should be specified:

- It is a **formal isomorphism**, not a proven physical identity
- The relationship with Friston's Free Energy Principle (applied to biological systems) provides a theoretical precedent, but complete physical validation remains a research program
- Measuring a "crystallized bit" in joules still belongs to future work


## 3.4 The convergence theorem (under hypotheses)

Under the following hypotheses:
1. Valid Laplace approximation (locally Gaussian posterior)
2. Slowly varying Fisher metric
3. Stationary data flow

Minimizing variational free energy by natural gradient:
- Approximately follows a geodesic in distribution space
- Converges to the optimal Bayesian posterior
- Minimizes total informational cost

This is the **thermodynamic optimality conjecture**: in this regime, the Bayesian path would be the path of least dissipation.

---

# Part IV — Recursive Emergence

## 4.1 Crystallization

When a dissipative structure reaches a stable state (local minimum of free energy), it **crystallizes**: its parameters cease to fluctuate significantly.

This crystallization corresponds to:
- **Thermodynamics**: non-equilibrium stationary state
- **Bayesian**: concentrated posterior (low variance)
- **Geometric**: basin of attraction reached

## 4.2 The posterior becomes prior

Once crystallized, the structure becomes a **constraint** for subsequent structures. Its state — once uncertain — is now an established fact.

Formally:
$$p_{n+1}(\theta) = p_n(\theta | D_n)$$

The posterior of level $n$ becomes the prior of level $n+1$.

## 4.3 Cost reduction

At each level, the space of possibilities narrows:

$$\mathcal{H}(p_{n+1}) < \mathcal{H}(p_n)$$

where $\mathcal{H}$ is differential entropy.

Learning cost decreases because there is less to learn — previous levels have already crystallized part of the structure.

## 4.4 Emergent hierarchy

```
Level 0: Raw data → Structure S₀ crystallizes
                                    ↓
Level 1: S₀ as prior → Structure S₁ crystallizes  
                                    ↓
Level 2: S₁ as prior → Structure S₂ crystallizes
                                    ↓
                                   ...
```

Each level:
- Inherits axioms from the previous
- Learns on a reduced space
- Crystallizes new axioms

---

# Application: The VAE as a Dissipative Structure

## Architecture

A **Variational Autoencoder** (VAE) is naturally interpretable in this framework:

```
x (data) → Encoder → q(z|x) → z (latent) → Decoder → p(x|z)
```

| Component | Dissipative role |
|-----------|-----------------|
| Data $x$ | Incoming flow |
| Latent space $z$ | Internal state (order) |
| ELBO | Variational free energy |
| Training | Geodesic convergence |
| Trained model | Crystallized structure |

## The emergence cycle

**Level 1: Learn (Bayesian)**

We train the VAE on data. No labels. Pure self-supervised. The network minimizes the ELBO (Evidence Lower Bound) — this is the approximation of the geodesic path.

**Level 2: Observe (epistemology)**

We don't use the decoder. We don't generate anything. We just look at z — the latent states.

We can *sometimes* discover that the latent space has organized itself:
- Certain dimensions encode shape
- Others encode color
- Clusters emerge

Discontinuous order emerged from a continuous process — *when conditions allow*.

> **Important note**: This organization is not guaranteed. Fundamental work on disentanglement (Locatello et al., 2019) demonstrates that a standard VAE, without explicit inductive bias, generally does not learn a reliably identifiable disentangled representation. For the emergence cycle (Observe → Name → Axiom) to work, either particularly structured data or constraints in the objective (like Higgins et al.'s β-VAE, 2017) are needed — constraints that themselves bias the "pure geodesic path". The emergence of interpretable axioms is therefore a *possible* result, not an intrinsic property of the framework.

**Level 3: Crystallize (axiom)**

We identify these structures. We name them. We freeze them.

"Dimension 3 encodes brightness" → axiom.
"This cluster corresponds to faces" → axiom.

These axioms become the prior of the next level.

**Level 4: Stack (recursion)**

We train a new VAE on the latent space z, not on x.

```
z (level 1) → Encoder → z' (level 2) → ...
```

Order emerges again. Meta-categories. Abstractions.

## The Emergent Dissipative Network in practice

```
Raw data (flow)
    │
    ▼ VAE level 0 (Bayesian)
    │
Latent variables z⁰
    │
    ▼ Epistemology (observe, name)
    │
Axioms A⁰ (crystallized order)
    │
    ▼ z⁰ becomes the flow of the next level
    │
VAE level 1 (Bayesian with prior A⁰)
    │
Latent variables z¹
    │
    ▼ ...
```

## Why it's (potentially) optimal

| Property      | Hierarchical VAE                            | EDN                                |
|---------------|---------------------------------------------|------------------------------------|
| Learning      | Variational inference, minimizes KL         | Bayesian, geodesic approximation   |
| Observation   | Explicit latent space                       | Observable states                  |
| Emergence     | Order can appear (under conditions)         | Conditional self-organization      |
| Stacking      | Each level feeds the next                   | Axiomatic recursion                |
| Cost          | Potentially decreasing at each level        | C(n+1) < C(n) (conjecture)         |

## Toward frugal AI

A Bayesian BEDS network where latent variables are observed without ever decoding — this is, according to the central conjecture of this framework, an approximation of the thermodynamic lower bound.

**The cost is that of survival:**

| Phase                    | Cost       | Description                      |
|--------------------------|------------|----------------------------------|
| Initial crystallization  | $E_{init}$ | Reaching the basin of attraction |
| Staying alive            | $E_{flux}$ | Compensating dissipation         |

Once crystallized, the system only needs enough energy to **not die** — that is, to compensate the dissipation γ that would bring it back toward maximum uncertainty.

Learning is not an additional cost. It **is** the survival flow. Each observation that keeps the system alive is also an observation that updates its beliefs.

**The difference from classical architectures:**

| Classical approach                        | BEDS approach                             |
|-------------------------------------------|-------------------------------------------|
| Massive training, then frozen inference   | Crystallization, then maintenance         |
| Expensive periodic retraining             | Survival flow = continuous learning       |
| Learning and existing are separate        | Learning and existing are identical       |

> A BEDS doesn't need energy to learn. It needs energy to exist — and learning is what a dissipative structure that exists does.




# Implementation: P2P Network of Bayesian Emergent Dissipative Structures

## Motivation

BEDS are not just a theoretical framework — they can be instantiated directly in a peer-to-peer network.

The central idea: **each node in the network is a BEDS**.

## The node as a dissipative structure

Let's recall the properties defining a BEDS:

1. **Open system**: exchanges with the environment
2. **Permanent flow**: absorbs data, exports entropy
3. **Dissipation**: without flow, return toward maximum uncertainty
4. **Crystallization**: the posterior becomes the prior of the next level

A P2P node that respects these constraints is a BEDS by construction.

## Architecture of a BEDS node

Each node contains:

| Component | Role | Notation |
|-----------|------|----------|
| Belief | Current state (posterior) | μ |
| Uncertainty | Variance on belief | σ² |
| Dissipation | Forgetting rate | γ |
| Identity | Public key | pk |
| Secret | Private key | sk |

### Isolation principle

Once created, a node:
- **Cannot** be reconfigured
- **Communicates only** through signed messages
- **Dies only** if the flow is cut

This is the dissipative constraint: the node exists through the flow passing through it. No flow, no node.

## Exchange protocol

### Minimal message format

A message contains exactly four elements:

| Field | Description |
|-------|-------------|
| source | Who sends (public key) |
| belief | The belief μ |
| sigma | The uncertainty σ |
| signature | Cryptographic proof |

Four fields suffice. It's canonical.

### Bayesian update

When a node B receives a belief from A, it merges by product of Gaussians:

$$\tau_{new} = \tau_A + \tau_B$$

$$\mu_{new} = \frac{\tau_A \cdot \mu_A + \tau_B \cdot \mu_B}{\tau_{new}}$$

$$\sigma_{new} = \sqrt{\frac{1}{\tau_{new}}}$$

where $\tau = 1/\sigma^2$ is precision.

This is minimal variational inference — the geodesic path on the statistical manifold.

### Temporal dissipation

Without a new message, uncertainty grows:

$$\sigma(t) = \sigma_0 \cdot e^{\gamma t}$$

The node "forgets". It returns toward maximum uncertainty. This is thermodynamic death if the flow stops.

## The network as an emergent hierarchy

### BEDS recursion

The crystallized posterior of a node becomes the prior for nodes listening to it:
```
Level 0: Sensors → raw beliefs
              ↓ crystallization
Level 1: Aggregators → fused beliefs
              ↓ crystallization  
Level 2: Meta-aggregators → consensus
              ↓
            ...
```

Each level inherits axioms from the previous. The space of possibilities narrows. Learning cost decreases.

### Energy bound property

If each level crystallizes (reaches its basin), then:

$$E_{total} = \sum_{n=0}^{\infty} E_n < \infty$$

The series converges because $\mathcal{H}(p_{n+1}) < \mathcal{H}(p_n)$. The network is **self-bounded energetically**.

## Design pattern: the node-organism

A BEDS node is like a living organism:

| Biology | BEDS node |
|---------|-----------|
| Birth | Creation with cryptographic keys |
| DNA | Immutable parameters (γ, pk) |
| Breathing | Flow of incoming/outgoing messages |
| Memory | Bayesian state (μ, σ²) |
| Forgetting | Dissipation (σ grows without flow) |
| Death | Flow stoppage (kill) |

### What is forbidden

- Reconfiguring a node after its birth
- Communicating other than through signed messages
- Surviving without incoming flow

These prohibitions are not technical choices — they are the **thermodynamic constraints** that define a dissipative structure.

## Verification of BEDS properties

| BEDS property | How it manifests |
|---------------|------------------|
| Open system | Incoming and outgoing messages |
| Permanent flow | Continuous exchanges between nodes |
| Dissipation | σ grows exponentially without flow |
| Crystallization | σ decreases through Bayesian fusion |
| Recursive emergence | Posterior → Prior of the next level |
| Mortality | Without flow, the node dies (σ → ∞) |

## What this design pattern guarantees

**Stability by construction** 
No external supervision, no exploding gradient. The system is pure self-supervised — free flow toward equilibrium.

**Energy optimality**
If the Geodesic Conjecture is true, Bayesian fusion follows the path of least dissipation on the statistical manifold.

**Emergent consensus**
Without a central server, beliefs converge through Bayesian averaging. Consensus is not computed — it **emerges**.

**Energy bound**
The network's total consumption is bounded by construction. Each crystallization reduces the remaining work.

**Transparency**
Each message is signed. Each state is an explicit distribution (μ, σ²). No black box.

## Summary

A P2P network of BEDS is:

- **Minimal**: four fields per message, three equations per node
- **Canonical**: Bayesian fusion is the unique operation
- **Sustainable**: energy bounded by construction
- **Faithful**: each node respects BEDS properties

> The network doesn't compute consensus. It **becomes** it.




# Status of the proposed framework

This document proposes a **unifying conceptual framework**, not an empirically validated theory. The correspondences established between thermodynamics and Bayesian inference are mathematically suggestive isomorphisms — they allow transposing intuitions and tools from one domain to another, but their complete physical validation remains a research program.

Several central claims have the status of **conjectures**:

1. **Geodesic conjecture**: Under the Laplace approximation and with a slowly varying Fisher metric, the natural gradient approximates a geodesic of the statistical manifold.

2. **Thermodynamic optimality conjecture**: Bayesian inference represents the thermodynamic lower bound of learning — the path of least dissipation.

3. **Recursion conjecture**: Crystallized structures naturally form recursive hierarchies where the posterior of each level becomes the prior of the next.

These conjectures are consistent with the established theories they mobilize (Prigogine, Amari, Friston), but their validation would require:

- **Testable predictions** derived from the framework
- **Concrete case studies**: simulations of simple dissipative systems, inspired neural architectures
- **Experimental measurements** of energy costs comparing different learning algorithms

The research program is open.

---

# Appendix: Reflections on Bayesian society

> **Note**: This section is more speculative than the rest of the document. It proposes an analogy — not a formal theory — between the principles developed above and social dynamics.

A Bayesian society would be a set of agents who share their beliefs and update them collectively. Each agent observes the world, exchanges with others, and adjusts what they believe based on what they learn.

When enough agents converge toward the same belief — when collective uncertainty about a question becomes very low — this belief crystallizes and becomes a **shared axiom**. This axiom is not imposed by anyone: it emerges from the flow of information, like a riverbed emerges from the repeated passage of water.

These crystallized axioms then become the foundation on which new beliefs can be built. The cost to learn decreases at each level, because the space of possibilities narrows.

**The speculative hypothesis**: only value systems, norms and institutions that emerge from this process — that is, that naturally crystallize from interactions and data — are sustainable. What is imposed from above, without roots in the collective dissipative structure, tends to collapse.

An artificial dam can hold for a while, but the river always ends up finding its true bed.

---


# Case Study: Energy Autonomy of a BEDS Network

## The challenge

Can we build a BEDS network that operates **indefinitely** with ambient solar energy?

If yes, this would concretely validate the promise of energy bounds in the BEDS framework: a distributed learning system whose consumption is bounded by construction.

## The hardware stack

Three components suffice:

| Component | Role | Key characteristic |
|-----------|------|---------------------|
| Microcontroller (ESP32) | Computation and communication | Deep sleep modes (10 µA) |
| JavaScript engine (MicroQuickJS) | BEDS logic execution | 10 KB RAM, 100 KB ROM |
| Long-range radio (LoRa) | P2P communication | 2-15 km range, very low power |

**Note on MicroQuickJS**: This JavaScript engine, published by Fabrice Bellard in December 2025, allows running JavaScript on extreme embedded systems — exactly what's needed for a minimal BEDS node.

## Life cycle of a node

A BEDS sensor node performs a simple cycle every 5 minutes:

1. **Wake up**: exit from deep sleep
2. **Measure**: sensor reading
3. **Fusion**: Bayesian update with received beliefs
4. **Transmit**: broadcast of updated belief
5. **Sleep**: return to deep sleep

## Energy balance

For a 5-minute cycle (300 seconds):

| Phase | Duration | Consumption | Energy |
|-------|----------|-------------|--------|
| Wake + Measure | 15 ms | ~20 mA | ~1 µWh |
| Bayesian fusion | 20 ms | ~25 mA | ~1.6 µWh |
| LoRa transmission | 100 ms | ~60 mA | ~20 µWh |
| LoRa reception | 50 ms | ~5 mA | ~0.8 µWh |
| **Total active** | **185 ms** | — | **~24 µWh** |
| Deep sleep | 299.8 s | 10 µA | ~275 µWh |
| **Total cycle** | **300 s** | — | **~300 µWh** |

**Average power**: 300 µWh / (5/60 h) ≈ **3.6 mW**

## Why Bayesian fusion is negligible

Bayesian update of two Gaussians requires:
- 2 divisions (precision calculations)
- 2 multiplications
- 2 additions
- 1 square root

**Total: ~10 floating-point operations per fusion.**

Even with 100 beliefs to fuse, the calculation takes less than 5 ms on a modest microcontroller. Computation energy is negligible compared to radio transmission.

This is a direct consequence of the BEDS formalism: Bayesian fusion is **the minimal operation** on the statistical manifold.

## The autonomy equation

A small IoT solar panel (about 5 × 7 cm) provides:
- In full sun: 300-400 mW
- Average over 24h (night, clouds): **30-50 mW**

**Comparison:**

| | Value |
|---|--------|
| Energy supplied (solar, average) | ~40 mW |
| Energy consumed (BEDS node) | ~3.6 mW |
| **Margin** | **×11** |

The node consumes about **ten times less** than what the sun provides.

## Autonomy without sun

With a supercapacitor for storage (50 F @ 5V):
- Stored energy: ~170 mWh
- Autonomy without sun: 170 / 3.6 ≈ **47 hours**

The node survives two full days without light.

## Autonomy theorem

**Proposition.** A network of N BEDS nodes, each powered by a solar panel of average power $P_{solar}$, is **energetically autonomous** if:

$$P_{solar} > P_{node}$$

where $P_{node}$ is the average power of a node (computation + communication + thermal dissipation).

**Argument.** Each node is a dissipative structure:
- Incoming flow (solar) is bounded by $P_{solar}$
- Outgoing flow (computation + radio + heat) is bounded by $P_{max}$
- Internal state (beliefs) is bounded by available memory

If $P_{solar} > P_{node}$, the surplus charges storage. Thermal dissipation guarantees that the system cannot "explode" energetically.

**The node cannot consume more than incoming flow in the long run** — exactly like a flame doesn't burn more than its fuel.

## Comparison with existing systems

| System | Consumption | Autonomy | Learning |
|--------|-------------|----------|----------|
| AI datacenter | ~20 MW | Electric grid | GPU backpropagation |
| Raspberry Pi + ML | ~5 W | Battery (hours) | Inference only |
| ESP32 + TensorFlow Lite | ~200 mW | Battery (days) | Limited inference |
| **BEDS node** | **~4 mW** | **Solar (∞)** | **Distributed Bayesian fusion** |

The ratio is **three orders of magnitude** with a Raspberry Pi, **five orders of magnitude** with a datacenter.

## What this means

A BEDS network implemented on this hardware stack:

1. **Operates indefinitely** with ambient solar energy
2. **Learns** (fuses beliefs) without significant consumption
3. **Communicates** over several kilometers with a fraction of a milliwatt
4. **Stays simple** — the logic fits in 10 KB of RAM

This is the concrete realization of the BEDS energy bound: a system that **flows** indefinitely, maintained by a flow of solar energy, with learning that **emerges** from the physics of exchanges.

## Case study conclusion

> A complete BEDS infrastructure — sensors, aggregators, consensus — can be powered by the sun and operate without time limit.

This is not a posteriori optimization. It's a direct consequence of design: Bayesian fusion is the minimal operation, deep sleep is the default state, and dissipation is built into the architecture.

The system is **sustainable by construction**.




## Comparison with existing infrastructures

| Infrastructure | Annual consumption | Mechanism | Learning |
|----------------|-------------------|-----------|----------|
| Bitcoin | ~120 TWh | Proof of Work | None |
| Ethereum (post-merge) | ~0.01 TWh | Proof of Stake | None |
| Filecoin | ~0.2 TWh | Proof of Storage | None |
| GPT-4 training | ~50 GWh (one-shot) | Backpropagation | Centralized, non-continuous |
| ChatGPT inference | ~1-10 TWh/year (estimated) | Forward pass | None (frozen model) |
| Bittensor (TAO) | ~0.1 TWh (estimated) | Proof of Intelligence | Distributed, supervised |
| Fetch.ai | ~0.01 TWh (estimated) | Proof of Stake + Agents | Classical ML agents |
| **BEDS network (1M nodes)** | **~0.00003 TWh** | **Bayesian fusion** | **Distributed, self-supervised, continuous** |

**Notes on estimates:**
- Bitcoin/Ethereum: public data from Cambridge Centre for Alternative Finance
- GPT-4: estimates based on OpenAI declarations and third-party analyses
- Bittensor/Fetch.ai: estimates based on number of validators and consumption per node
- BEDS network: 1 million nodes × 3.6 mW × 8760 h = 31.5 MWh ≈ 0.00003 TWh

### What this table reveals

**Five orders of magnitude** separate a BEDS network from current AI blockchains.

The reason is structural:

| Approach              | Source of cost                                   |
|-----------------------|--------------------------------------------------|
| Proof of Work         | Intentional waste (security through energy)      |
| Backpropagation       | Gradients over millions/billions of parameters   |
| Proof of Intelligence | Validation by redundant ML computation           |
| **Bayesian fusion**   | **~10 operations per update**                    |

Current AI blockchains inherit from Bitcoin's "proof by waste" paradigm, or from deep learning's "gradient over everything" paradigm.

The BEDS framework proposes an alternative: **proof by Bayesian coherence**, where cost is proportional to exchanged information, not to mobilized computing power.

> A BEDS network doesn't prove it has *worked*. It proves it has *converged*.

# Related work: Relationship with JEPA

The EDN framework presents deep correspondences with LeCun's Joint Embedding Predictive Architectures (JEPA) (2022) and LeJEPA (Balestriero & LeCun, 2025).

## Formal correspondence

| JEPA                                  | EDN                                                       |
|---------------------------------------|-----------------------------------------------------------|
| Encoder $x \to s_x$                   | Structure extraction from flow                            |
| Latent variable $z$                   | Non-exportable entropy                                    |
| Energy $D(s_y, \tilde{s}_y)$          | Variational free energy                                   |
| Regularizer $R(z)$                    | Dissipative constraint                                    |
| Optimal isotropic Gaussian (LeJEPA)   | Maximum entropy under constraint = dissipative equilibrium |

## What EDN brings

JEPA prescribes *what* to build. EDN explains *why*:

- **Optimality**: the JEPA architecture realizes the flow → structure conversion with minimal dissipation
- **Dynamics**: the learning path should approximate a Fisher geodesic
- **Hierarchy**: H-JEPA corresponds to recursive crystallization where each posterior becomes the prior of the next level

> JEPA is a computational instantiation of EDN principles. EDN provides the theoretical framework that explains why JEPA works.

# Perspectives

## Toward robustness to non-Gaussian events

The BEDS framework presented here implicitly relies on Gaussian likelihoods — a convenient hypothesis but fragile against rare events, regime changes, or heavy tails. A natural extension would be to integrate a *Graduated Non-Convexity* (GNC) approach: instead of a quadratic cost function, we use a parameterized family $\rho(r, \mu)$ that interpolates between Gaussian behavior ($\mu \to \infty$) and saturating robust behavior ($\mu \to 0$).

The thermodynamic intuition suggests a correspondence: the parameter $\mu$ would play the role of a **rigidity temperature** of the system. A low $\mu$ ("hot" system) would tolerate outliers and allow exploration of new basins; a high $\mu$ ("cold" system) would refine beliefs in a stable regime. Even more elegant: $\mu$ could be dynamically coupled to incoming flow or internal entropy, so that the system **self-regulates its convexity** — relaxing its beliefs in the face of persistent residuals (detected regime change), tightening them when evidence flows coherently. This path remains to be rigorously formalized.

## Non-equilibrium dynamics and regime transitions

The article focuses on crystallization — arrival in a basin of attraction. But real systems go through **phase transitions**: a digital twin following a machine must sometimes abandon its current basin when the real system changes regime (wear, failure, modification).

Formalizing the conditions for **controlled destabilization** — when and how to "melt" a crystallized belief to allow migration to a new basin — is a natural extension. The thermodynamic intuition suggests that a sudden influx of flow (or detection of persistent residuals) should be able to trigger this transition, like a phase change induced by a temperature gradient.

## Link with Landauer's principle

Landauer's principle (1961) establishes that erasing one bit of information costs at minimum $k_B T \ln 2$ joules. In the BEDS framework, dissipation $\gamma$ — structured forgetting — is not free: it has an **incompressible thermodynamic cost**.

This suggests a physical lower bound on the maintenance energy of a dissipative structure: the cost of the forgetting necessary to remain adaptive. A BEDS node that forgets too slowly becomes rigid; a node that forgets too fast wastes energy. The optimum would be the dissipation rate $\gamma^*$ that minimizes total cost (maintenance + adaptation) — a path to be formalized.

## Toward Active Inference

The current BEDS framework is **passive**: the system observes and updates its beliefs, but doesn't act on its environment. The natural extension is **Active Inference** (Friston, 2010) where the system can also act to reduce its uncertainty — choose which observations to acquire, where to place its sensors, when to communicate.

In a P2P network of BEDS, this would translate to nodes that **decide** when to transmit, whom to address, and which beliefs to share — optimizing not only their internal free energy but also the energy cost of communication. Consensus would no longer be merely emergent, it would be **actively constructed** by agents that minimize their expected surprise.

## Crystallization, fragility, and the quantum path

A profound remark emerges from this framework: **the unpredictable behaviors of current AIs are not a bug, but a thermodynamic consequence of crystallization**.

When we freeze a large language model after training, we implicitly crystallize a hypothesis about the environment — the world as it was encoded in the data. The model becomes a rigid structure, a river with a concrete bed. As long as the world stays close to this crystallization, the system works. But as soon as the environment drifts — and it always drifts — the model extrapolates into uncalibrated regions. Hallucinations, erratic out-of-distribution behaviors, fragility to adversarial examples: these are symptoms of a system that has **crystallized too much**.

Conversely, a BEDS network maintains a permanent tension between crystallization (convergence) and dissipation (forgetting). The parameter $\gamma$ prevents total rigidification — it preserves a non-zero "temperature", a residual plasticity. The system remains **liquid**: ordered but adaptable, structured but not frozen.

This observation opens onto a more speculative conjecture: **the Bayesian formalism perhaps finds its natural substrate in quantum computing**. In quantum mechanics, the state of a system is intrinsically a probability distribution (the squared amplitude). Measurement is conditioning — a Bayesian update. Unitary evolution transports the distribution without crystallizing it. A quantum computer cannot "freeze" a state without measuring it; superposition — uncertainty — is maintained as long as we don't observe.

| Paradigm | State | Adaptability | Fragility |
|----------|-------|--------------|-----------|
| Frozen LLM | Crystal | None after training | High (out of distribution) |
| Classical BEDS | Liquid | Maintained by $\gamma$ | Controlled |
| Quantum BEDS (speculative) | Superposition | Native | Decoherence = forced crystallization |

From this perspective, a quantum BEDS node wouldn't need to *simulate* its uncertainty ($\sigma^2$) — it would be *physical*, encoded in superposition. Dissipation would no longer be an added mechanism but the thermodynamic price of interaction with the classical environment: decoherence. Structured forgetting would emerge from physics itself.

This path remains highly speculative, but it suggests a possible convergence: Bayesian dissipative structures could be not only a theoretical framework for learning, but also a **natural description of what quantum matter already does** — maintaining order by exporting entropy, without ever completely crystallizing.

---

# References

## Thermodynamics and dissipative structures

- Prigogine, I. (1977). *Time, Structure and Fluctuations*. Nobel Lecture.
- Prigogine, I. & Stengers, I. (1984). *Order out of Chaos: Man's New Dialogue with Nature*. Bantam Books.
- Nicolis, G. & Prigogine, I. (1977). *Self-Organization in Non-Equilibrium Systems*. Wiley.

## Information geometry and natural gradient

- Amari, S. (1998). Natural gradient works efficiently in learning. *Neural Computation*, 10(2), 251-276.
- Amari, S. & Nagaoka, H. (2000). *Methods of Information Geometry*. AMS & Oxford University Press.
- Rao, C.R. (1945). Information and the accuracy attainable in the estimation of statistical parameters. *Bulletin of the Calcutta Mathematical Society*, 37, 81-91.
- Chentsov, N.N. (1982). *Statistical Decision Rules and Optimal Inference*. AMS.

## Free Energy Principle and variational inference

- Friston, K. (2010). The free-energy principle: a unified brain theory? *Nature Reviews Neuroscience*, 11, 127-138.
- Friston, K., Kilner, J. & Harrison, L. (2006). A free energy principle for the brain. *Journal of Physiology Paris*, 100, 70-87.
- Friston, K. & Kiebel, S. (2009). Predictive coding under the free-energy principle. *Philosophical Transactions of the Royal Society B*, 364, 1211-1221.

## VAE and Bayesian deep learning

- Balestriero, R. & LeCun, Y. (2025). LeJEPA: Provable and Scalable Self-Supervised Learning Without the Heuristics. *arXiv:2511.08544*.
- Kingma, D.P. & Welling, M. (2014). Auto-Encoding Variational Bayes. *ICLR*.
- Kingma, D.P. & Welling, M. (2019). An Introduction to Variational Autoencoders. *Foundations and Trends in Machine Learning*, 12(4), 307-392.
- Higgins, I., et al. (2017). β-VAE: Learning Basic Visual Concepts with a Constrained Variational Framework. *ICLR*.
- Locatello, F., et al. (2019). Challenging Common Assumptions in the Unsupervised Learning of Disentangled Representations. *ICML*.

## Information Bottleneck

- Tishby, N., Pereira, F. & Bialek, W. (1999). The Information Bottleneck Method. *Proceedings of the 37th Allerton Conference*.
- Tishby, N. & Zaslavsky, N. (2015). Deep Learning and the Information Bottleneck Principle. *IEEE Information Theory Workshop*.
- Shwartz-Ziv, R. & Tishby, N. (2017). Opening the Black Box of Deep Neural Networks via Information. *arXiv:1703.00810*.

## Foundations

- Shannon, C.E. (1948). A Mathematical Theory of Communication. *Bell System Technical Journal*, 27, 379-423.
- Jaynes, E.T. (1957). Information Theory and Statistical Mechanics. *Physical Review*, 106(4), 620-630.
- Zellner, A. (1988). Optimal Information Processing and Bayes's Theorem. *The American Statistician*, 42(4), 278-280.

## Physics of information

- Landauer, R. (1961). Irreversibility and Heat Generation in the Computing Process. *IBM Journal of Research and Development*, 5(3), 183-191.
- Bennett, C.H. (1982). The Thermodynamics of Computation—A Review. *International Journal of Theoretical Physics*, 21(12), 905-940.

---

*Article written in a spirit of scientific rigor and intellectual openness. The principles stated are theoretical propositions — not established laws. Any constructive criticism is welcome.*
