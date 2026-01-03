---
title: "BEDS Reformulation of the Navier-Stokes Equations"
subtitle: "A Bayesian recursive multi-scale approach to the regularity problem"
author: "Laurent Caraffa & Claude"
date: "2026-01-03"
status: "Working paper — DRAFT"
---

# Abstract

This document proposes a reformulation of the regularity problem for the 3D Navier-Stokes equations within the framework of Bayesian Emergent Dissipative Structures (BEDS). The central idea: instead of treating the fluid as a monolithic system, we decompose it into a **recursive hierarchy of scales**, where each level is a BEDS that crystallizes and becomes the prior of the next level.

This reformulation translates the question of singularities into a question of **hierarchy termination**: a singularity would correspond to an infinite cascade that never crystallizes. We conjecture that the growth of dissipation with wave number ($\gamma_n \sim k_n^2$) guarantees crystallization at each level, and therefore the absence of singularities.

**Keywords**: Navier-Stokes, dissipative structures, Bayesian inference, multi-scale cascade, regularity, turbulence.

---

# 1. Introduction

## 1.1 The millennium problem

The Navier-Stokes equations describe the flow of incompressible viscous fluids:

$$\frac{\partial \mathbf{v}}{\partial t} + (\mathbf{v} \cdot \nabla)\mathbf{v} = -\nabla p + \nu \nabla^2 \mathbf{v}$$

$$\nabla \cdot \mathbf{v} = 0$$

where $\mathbf{v}(\mathbf{x}, t)$ is the velocity field, $p$ the pressure, and $\nu > 0$ the kinematic viscosity.

**Millennium question (Clay Mathematics Institute)**: For smooth initial conditions $\mathbf{v}_0 \in C^\infty(\mathbb{R}^3)$ with rapid decay, does a smooth solution $\mathbf{v}(\mathbf{x}, t)$ exist for all $t > 0$, or can singularities (blow-up) appear in finite time?

## 1.2 State of the art

**What we know**:
- In 2D: global regularity proven (Ladyzhenskaya, 1969)
- In 3D: existence of weak solutions (Leray, 1934), but uniqueness and regularity are open
- Local-in-time regular solutions (Kato, Fujita)
- Conditional criteria: if certain norms remain bounded, no singularity (Beale-Kato-Majda, Prodi-Serrin)

**What's stuck**: the nonlinear term $(\mathbf{v} \cdot \nabla)\mathbf{v}$ allows **vortex stretching** in 3D, absent in 2D. This mechanism can concentrate vorticity faster than viscosity can diffuse it.

## 1.3 Our approach

We propose to reformulate the problem in the BEDS framework by exploiting three ideas:

1. **Multi-scale decomposition**: the fluid is a hierarchy of scales, not a monolithic block
2. **Bayesian recursion**: each scale crystallizes and becomes the prior of the next
3. **Crystallization as regularity**: a singularity = a hierarchy that doesn't terminate

---

# 2. Navier-Stokes as a Dissipative Structure

## 2.1 Identification of BEDS components

| BEDS component | Navier-Stokes |
|----------------|---------------|
| Open system | Fluid domain with boundary conditions |
| Incoming flow | Energy injected at large scales (forcing) |
| Internal state | Velocity field $\mathbf{v}(\mathbf{x}, t)$ |
| Dissipation | Viscous term $\nu \nabla^2 \mathbf{v}$ |
| Exported entropy | Heat (viscous dissipation) |
| Maintained structure | Organized flow (vs thermal chaos) |

## 2.2 Energy balance

Total kinetic energy:

$$E(t) = \frac{1}{2} \int_{\mathbb{R}^3} |\mathbf{v}|^2 \, d\mathbf{x}$$

satisfies:

$$\frac{dE}{dt} = -\nu \int_{\mathbb{R}^3} |\nabla \mathbf{v}|^2 \, d\mathbf{x} = -\varepsilon(t) \leq 0$$

where $\varepsilon(t)$ is the dissipation rate. **Energy always decreases** — it's a dissipative structure.

## 2.3 Enstrophy balance

Enstrophy (integrated squared vorticity):

$$\Omega(t) = \frac{1}{2} \int_{\mathbb{R}^3} |\boldsymbol{\omega}|^2 \, d\mathbf{x}, \quad \boldsymbol{\omega} = \nabla \times \mathbf{v}$$

satisfies:

$$\frac{d\Omega}{dt} = \underbrace{\int \boldsymbol{\omega} \cdot (\boldsymbol{\omega} \cdot \nabla)\mathbf{v} \, d\mathbf{x}}_{\text{vortex stretching } P(t)} - \underbrace{\nu \int |\nabla \boldsymbol{\omega}|^2 \, d\mathbf{x}}_{\text{dissipation } D(t)}$$

**The drama in 3D**: $P(t)$ can be positive and grow faster than $D(t)$.

## 2.4 The reformulated question

In BEDS language:

> **Is viscous dissipation always sufficient for the structure to crystallize (reach a regular state), or can it fail to control enstrophy production, leading to an "explosion" of local uncertainty?**

---

# 3. Recursive Multi-Scale Decomposition

## 3.1 Spectral decomposition

Let's decompose the velocity field into scales via Fourier:

$$\mathbf{v}(\mathbf{x}, t) = \sum_{n=0}^{\infty} \mathbf{v}_n(\mathbf{x}, t)$$

where $\mathbf{v}_n$ contains modes of wave number $k \in [k_n, k_{n+1})$ with $k_n = 2^n k_0$.

Each $\mathbf{v}_n$ represents structures at scale $\ell_n \sim 1/k_n$.

## 3.2 The Kolmogorov cascade revisited

Kolmogorov (1941) phenomenologically established:

1. Energy is **injected** at large scales ($n = 0$)
2. It **cascades** toward small scales via the nonlinear term
3. It is **dissipated** at the Kolmogorov scale $\eta = (\nu^3/\varepsilon)^{1/4}$

**Our reformulation**: this cascade is a **recursive BEDS hierarchy** where each level crystallizes before passing the flow to the next.

## 3.3 The BEDS hierarchy

```
Level 0: Large scales
    - Incoming flow: external forcing Φ₀
    - State: distribution q₀(v₀)
    - Dissipation: γ₀ = ν k₀²
    - Crystallization: posterior p₀(v₀ | data) concentrated
            ↓
    The posterior p₀ becomes the prior of level 1
            ↓
Level 1: Intermediate scales
    - Incoming flow: non-crystallized residual from level 0
    - State: distribution q₁(v₁)
    - Dissipation: γ₁ = ν k₁² = 4 γ₀
    - Crystallization: posterior p₁(v₁ | p₀)
            ↓
    The posterior p₁ becomes the prior of level 2
            ↓
Level n: Scale 2⁻ⁿ
    - Incoming flow: Φₙ (cascade from n-1)
    - State: distribution qₙ(vₙ)
    - Dissipation: γₙ = ν kₙ² = 4ⁿ γ₀
    - Crystallization: posterior pₙ(vₙ | pₙ₋₁)
            ↓
           ...
            ↓
Level N*: Kolmogorov scale
    - Dissipation totally dominates
    - Terminal crystallization: all flow is dissipated
```

## 3.4 Key property: growth of dissipation

At each level:

$$\gamma_n = \nu k_n^2 = \nu (2^n k_0)^2 = 4^n \gamma_0$$

**Dissipation grows exponentially with level.**

This is the key: even if cascading flow grows, dissipation grows faster (exponentially vs polynomially in general).

---

# 4. Bayesian Formalization

## 4.1 Probabilistic state at each level

Instead of considering $\mathbf{v}_n(t)$ as deterministic, we consider a **distribution** $q_n(\mathbf{v}_n, t)$ over possible configurations at scale $n$.

This distribution encodes our **uncertainty** about the fluid's state at this scale, given what has crystallized at higher scales.

## 4.2 Variational free energy per level

For each level $n$, let's define variational free energy:

$$\mathcal{F}_n[q_n] = D_{KL}(q_n \| p_{n-1}) + \mathbb{E}_{q_n}\left[\frac{1}{2}\int |\mathbf{v}_n|^2 \, d\mathbf{x}\right]$$

where:
- $D_{KL}(q_n \| p_{n-1})$ measures deviation from the prior (crystallized posterior of previous level)
- The second term is mean kinetic energy at this scale

## 4.3 Free energy dynamics

The evolution of $\mathcal{F}_n$ is governed by:

$$\frac{d\mathcal{F}_n}{dt} = \underbrace{\Phi_n}_{\text{incoming flow from } n-1} - \underbrace{\gamma_n \cdot \mathcal{D}_n}_{\text{dissipation}} + \underbrace{\mathcal{C}_n}_{\text{nonlinear coupling}}$$

where:
- $\Phi_n$ is the energy flow cascading from level $n-1$
- $\mathcal{D}_n$ is a dissipation term (always positive)
- $\mathcal{C}_n$ encodes inter-scale interactions

## 4.4 Crystallization condition

**Definition**: Level $n$ **crystallizes** if:

$$\mathcal{F}_n(t) \to \mathcal{F}_n^* < \infty \quad \text{as } t \to \infty$$

and the distribution $q_n$ concentrates around a state $\mathbf{v}_n^*$:

$$q_n(\mathbf{v}_n, t) \to \delta(\mathbf{v}_n - \mathbf{v}_n^*)$$

or more generally, variance $\sigma_n^2 \to \sigma_{n,*}^2 < \infty$.

## 4.5 Bayesian recursion

Once level $n$ crystallizes, its posterior becomes the prior of level $n+1$:

$$p_n(\mathbf{v}_n) := \lim_{t \to \infty} q_n(\mathbf{v}_n, t)$$

This prior encodes the **axioms** that level $n+1$ inherits: large-scale structure is fixed, only smaller-scale fluctuations remain to be determined.

---

# 5. The Central Conjecture

## 5.1 Informal statement

> **BEDS-Navier-Stokes Conjecture**: For the 3D Navier-Stokes equations with viscosity $\nu > 0$, the multi-scale BEDS hierarchy **crystallizes at each level** in finite time. Therefore, no finite-time singularity exists.

## 5.2 Formal statement

**Conjecture**: Let $\mathbf{v}_0 \in C^\infty(\mathbb{R}^3)$ be a rapidly decaying initial condition. Consider the multi-scale decomposition $\mathbf{v} = \sum_n \mathbf{v}_n$ and associated BEDS hierarchy. Then:

1. **Level-by-level crystallization**: For all $n \geq 0$, there exists $T_n < \infty$ such that level $n$ crystallizes for $t > T_n$.

2. **Hierarchy termination**: There exists $N^* < \infty$ such that for $n > N^*$, incoming flow $\Phi_n$ is entirely dissipated ($\mathcal{F}_n \equiv 0$).

3. **Regularity**: The solution $\mathbf{v}(\mathbf{x}, t) = \sum_{n=0}^{N^*} \mathbf{v}_n^*(\mathbf{x}, t)$ is $C^\infty$ for all $t > 0$.

## 5.3 Intuition

**Why it should work**:

Dissipation at level $n$ is $\gamma_n = \nu k_n^2 = 4^n \gamma_0$.

Cascading flow $\Phi_n$ grows at most polynomially (Kolmogorov theory: $\Phi_n \sim \varepsilon$ constant in the inertial range).

So for $n$ large enough:

$$\gamma_n \cdot \mathcal{D}_n \gg \Phi_n$$

Dissipation **dominates** incoming flow. The level crystallizes.

**The Kolmogorov scale** $\eta = (\nu^3/\varepsilon)^{1/4}$ is precisely the scale where $\gamma_n \sim \Phi_n$ — below, everything is dissipated.

## 5.4 What remains to prove

To transform this conjecture into a theorem, we would need to:

1. **Bound the cascading flow**: show that $\Phi_n \leq C \cdot \varepsilon$ for a universal constant

2. **Bound the nonlinear coupling**: show that $|\mathcal{C}_n| \leq C' \cdot \Phi_n$ (coupling cannot amplify arbitrarily)

3. **Recursive Grönwall inequality**: deduce that $\mathcal{F}_n(t) \leq \mathcal{F}_n(0) e^{-\alpha_n t} + \beta_n$ with $\alpha_n > 0$

---

# 6. Link with Singularity

## 6.1 What is a singularity in this framework?

**BEDS Definition**: A singularity would correspond to a situation where **the hierarchy doesn't terminate**:

- Either a level $n$ never crystallizes ($\mathcal{F}_n \to \infty$)
- Or the number of active levels $N^* \to \infty$ in finite time

## 6.2 Singularity scenario (hypothetical)

For a singularity to occur, we would need:

1. Cascading flow $\Phi_n$ grows faster than $4^n$ (faster than exponential)
2. Or coupling $\mathcal{C}_n$ amplifies flow uncontrollably

**Physically**: this would correspond to a "runaway" cascade, where vortex stretching creates structure at arbitrarily small scales faster than viscosity can dissipate it.

## 6.3 Why it's (probably) impossible

**Dimensional argument**: The energy transfer rate between scales is bounded by:

$$\Phi_n \lesssim \frac{v_n^3}{\ell_n}$$

where $v_n$ is typical velocity at scale $\ell_n$.

For $\Phi_n$ to grow faster than $4^n$, we would need $v_n \gtrsim k_n^{1/3} \cdot C^n$ for $C > 4^{1/3}$.

But total energy is bounded: $\sum_n v_n^2 / k_n \leq E_0 < \infty$.

This constraint **limits** possible growth of $v_n$, and therefore of $\Phi_n$.

**This is essentially Kolmogorov's argument**: the cascade is "self-regulated" by energy conservation.

---

# 7. Detailed Mathematical Formalization

## 7.1 Functional space

Let's work in $L^2(\mathbb{R}^3)^3$ with Littlewood-Paley decomposition:

$$\mathbf{v} = \sum_{n=-1}^{\infty} \Delta_n \mathbf{v}$$

where $\Delta_n$ is the projector on frequencies $|\xi| \sim 2^n$.

## 7.2 Equation per level

The Navier-Stokes equation projected to level $n$:

$$\frac{\partial \mathbf{v}_n}{\partial t} + \Delta_n[(\mathbf{v} \cdot \nabla)\mathbf{v}] = -\Delta_n \nabla p + \nu \nabla^2 \mathbf{v}_n$$

The nonlinear term couples scales:

$$\Delta_n[(\mathbf{v} \cdot \nabla)\mathbf{v}] = \sum_{j,k} \Delta_n[(\mathbf{v}_j \cdot \nabla)\mathbf{v}_k]$$

## 7.3 Energy balance per level

$$\frac{d}{dt}\|\mathbf{v}_n\|_{L^2}^2 = -2\nu \|\nabla \mathbf{v}_n\|_{L^2}^2 + T_n$$

where $T_n$ is net energy transfer:

$$T_n = -2 \int \mathbf{v}_n \cdot \Delta_n[(\mathbf{v} \cdot \nabla)\mathbf{v}] \, d\mathbf{x}$$

## 7.4 Variational distribution

Set $q_n(\mathbf{v}_n, t)$ as a Gaussian distribution:

$$q_n(\mathbf{v}_n) = \mathcal{N}(\boldsymbol{\mu}_n, \Sigma_n)$$

where $\boldsymbol{\mu}_n$ is the mean and $\Sigma_n$ the covariance in Fourier mode space at level $n$.

## 7.5 Explicit variational free energy

$$\mathcal{F}_n = \frac{1}{2}\text{Tr}(\Sigma_{n-1}^{-1}\Sigma_n) - \frac{1}{2}\log\det(\Sigma_{n-1}^{-1}\Sigma_n) - \frac{d_n}{2} + \frac{1}{2}\|\boldsymbol{\mu}_n\|^2$$

where $d_n$ is the dimension of mode space at level $n$.

## 7.6 Variance dynamics

In Gaussian approximation, variance $\sigma_n^2 = \text{Tr}(\Sigma_n)/d_n$ evolves according to:

$$\frac{d\sigma_n^2}{dt} = \underbrace{\phi_n}_{\text{incoming flow}} - \underbrace{2\gamma_n \sigma_n^2}_{\text{dissipation}} + \underbrace{c_n}_{\text{coupling}}$$

with $\gamma_n = \nu k_n^2 \sim 4^n \nu k_0^2$.

## 7.7 Explicit crystallization condition

Level $n$ crystallizes if and only if:

$$2\gamma_n > \frac{\partial \phi_n}{\partial \sigma_n^2} + \frac{\partial c_n}{\partial \sigma_n^2}$$

i.e. if dissipation is stronger than the sensitivity of flow and coupling to uncertainty.

---

# 8. Proof Directions

## 8.1 General strategy

1. **Show crystallization of level 0** (large scales) — this is the "easy" case, essentially Leray's weak solution theory

2. **Propagation of crystallization**: if levels $0, ..., n-1$ have crystallized, show that level $n$ also crystallizes

3. **Termination**: show there exists $N^*$ such that $\Phi_n \approx 0$ for $n > N^*$

## 8.2 Potential tools

**Bernstein inequalities**: control of norms of $\mathbf{v}_n$ as function of $n$

$$\|\nabla^k \mathbf{v}_n\|_{L^p} \lesssim 2^{nk} \|\mathbf{v}_n\|_{L^p}$$

**Recursive Grönwall lemma**: if $\frac{d\mathcal{F}_n}{dt} \leq -\alpha_n \mathcal{F}_n + \beta_n$ with $\alpha_n = c \cdot 4^n$, then:

$$\mathcal{F}_n(t) \leq \mathcal{F}_n(0) e^{-\alpha_n t} + \frac{\beta_n}{\alpha_n}$$

and $\mathcal{F}_n \to \beta_n/\alpha_n < \infty$ as $t \to \infty$.

**Bony estimates**: control of nonlinear term via paraproduct

## 8.3 The crucial point

Everything hinges on the **bound of cascading flow** $\Phi_n$.

If we can show:

$$\Phi_n \leq C \cdot \varepsilon \cdot f(n)$$

with $f(n)$ sub-exponential (polynomial, for example), then $\gamma_n = 4^n \gamma_0$ wins for large $n$.

**This is exactly what Kolmogorov's K41 theory predicts** ($\Phi_n \approx \varepsilon$ = constant in the inertial zone), but proving it rigorously from the equations is the heart of the problem.

---

# 9. Discussion

## 9.1 What this reformulation brings

1. **New perspective**: the regularity problem becomes a hierarchy termination problem

2. **Bayesian tools**: access to variational inequalities, entropic bounds, etc.

3. **Reinforced physical intuition**: recursive crystallization formalizes the Kolmogorov cascade

4. **Singularity criterion**: a singularity = infinite hierarchy in finite time

## 9.2 Remaining difficulties

1. **Formalize coupling**: the term $\mathcal{C}_n$ mixes scales in complex ways

2. **Passage from probabilistic to deterministic**: show that crystallization of $q_n$ implies regularity of $\mathbf{v}_n$

3. **Uniformity in $n$**: ensure constants don't degenerate

## 9.3 Connection with existing approaches

| Approach | Link with BEDS |
|----------|----------------|
| Leray weak solutions | Partial crystallization (bounded energy, not enstrophy) |
| Beale-Kato-Majda criterion | Condition for hierarchy not to terminate |
| Besov spaces | Natural space for multi-scale decomposition |
| K41 theory | Phenomenological version of our hierarchy |

## 9.4 What if the conjecture is false?

If singularities exist, the BEDS framework predicts:

- There exist initial conditions for which the hierarchy **doesn't terminate**
- Cascading flow grows super-exponentially
- "Pathological crystallization" creates infinite vorticity concentration

This would give a **constructive criterion** for seeking singularities: find initial data that prevent recursive crystallization.

---

# 10. Conclusion and Research Program

## 10.1 Summary

We have proposed a reformulation of the 3D Navier-Stokes regularity problem in the BEDS framework:

1. The fluid is a **recursive hierarchy** of dissipative structures
2. Each scale **crystallizes** (converges) and becomes the **prior** of the next scale
3. **Dissipation grows exponentially** with level ($\gamma_n \sim 4^n$)
4. A **singularity** would correspond to a hierarchy that doesn't terminate
5. The growth of dissipation should **guarantee termination**

## 10.2 Research program

**Short term**:
- [ ] Rigorously formalize the BEDS decomposition
- [ ] Prove crystallization of level 0
- [ ] Establish propagation lemma (level $n-1$ → level $n$)

**Medium term**:
- [ ] Bound cascading flow $\Phi_n$
- [ ] Control nonlinear coupling $\mathcal{C}_n$
- [ ] Establish recursive Grönwall inequality

**Long term**:
- [ ] Prove hierarchy termination
- [ ] Deduce global regularity
- [ ] Or identify obstructions and characterize potential singularities

## 10.3 Final word

This reformulation does not (yet) solve the millennium problem. But it offers a **new angle of attack**, anchored in the physics of dissipative structures and Bayesian formalism.

If Kolmogorov was right — if the cascade is indeed self-regulated and always terminates at the dissipative scale — then the BEDS framework perhaps provides the language to prove it.

And if singularities exist, this framework tells us exactly **what to look for**: initial conditions that break recursion, configurations where flow grows faster than dissipation, hierarchies that refuse to crystallize.

In either case, it's a step forward.

---

# References

## Navier-Stokes and regularity

- Leray, J. (1934). Sur le mouvement d'un liquide visqueux emplissant l'espace. *Acta Mathematica*, 63, 193-248.
- Ladyzhenskaya, O.A. (1969). *The Mathematical Theory of Viscous Incompressible Flow*. Gordon and Breach.
- Beale, J.T., Kato, T., & Majda, A. (1984). Remarks on the breakdown of smooth solutions for the 3-D Euler equations. *Communications in Mathematical Physics*, 94, 61-66.
- Fefferman, C. (2000). Existence and smoothness of the Navier-Stokes equation. *Clay Mathematics Institute Millennium Problems*.

## Turbulence and cascade

- Kolmogorov, A.N. (1941). The local structure of turbulence in incompressible viscous fluid for very large Reynolds numbers. *Doklady Akademii Nauk SSSR*, 30, 299-303.
- Frisch, U. (1995). *Turbulence: The Legacy of A.N. Kolmogorov*. Cambridge University Press.

## Harmonic analysis and Besov spaces

- Bony, J.-M. (1981). Calcul symbolique et propagation des singularités pour les équations aux dérivées partielles non linéaires. *Annales scientifiques de l'École normale supérieure*, 14(2), 209-246.
- Bahouri, H., Chemin, J.-Y., & Danchin, R. (2011). *Fourier Analysis and Nonlinear Partial Differential Equations*. Springer.

## Dissipative structures and Bayesian inference

- Prigogine, I. (1977). *Time, Structure and Fluctuations*. Nobel Lecture.
- Amari, S. (1998). Natural gradient works efficiently in learning. *Neural Computation*, 10(2), 251-276.
- Friston, K. (2010). The free-energy principle: a unified brain theory? *Nature Reviews Neuroscience*, 11, 127-138.

---

*Working document. The conjectures presented here are theoretical propositions requiring rigorous validation. Any constructive criticism is welcome.*


