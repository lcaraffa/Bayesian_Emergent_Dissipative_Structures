---
title: "BEDS : Bayesian Emergent Dissipative Structures"
subtitle: "Toward a unification between logical incompleteness and thermodynamics of information"
author: "Laurent Caraffa"
date: "2026-01-03"
status: "Working paper"
---

# Bayesian Emergent Dissipative Structures: A Unified Framework

## Introduction

This work proposes a formal correspondence between three domains: dissipative structure thermodynamics (Prigogine, 1977), information geometry (Amari, 1998), and variational inference. The central hypothesis is that learning processes could be interpreted as dissipative structures that convert a data flux into internal order by exporting entropy.

---

## 1. Formalism

### 1.1 Dissipative structure

A dissipative structure $S$ is an open system that absorbs an incoming flux $\Phi_{in}$, maintains internal order (negentropy $N$), and exports entropy $H$ to the environment.

The second law imposes:

$$\frac{dS_{system}}{dt} = \frac{dS_{internal}}{dt} + \frac{dS_{exchange}}{dt}$$

where $\frac{dS_{internal}}{dt} \geq 0$ (irreversible production) and $\frac{dS_{exchange}}{dt}$ can be negative. The structure exists as long as $\Phi_{in} > \Phi_{min}$.

### 1.2 Information geometry

The space of probability distributions forms a statistical manifold $\mathcal{M}$. The Fisher metric defines the natural distance on this manifold:

$$g_{ij}(\theta) = \mathbb{E}_{p(x|\theta)}\left[\frac{\partial \log p(x|\theta)}{\partial \theta_i} \frac{\partial \log p(x|\theta)}{\partial \theta_j}\right]$$

The natural gradient corrects the ordinary gradient to point in the steepest descent direction in distribution space:

$$\tilde{\nabla} L(\theta) = G(\theta)^{-1} \nabla L(\theta)$$

### 1.3 Proposed correspondence

The framework proposes a formal isomorphism between thermodynamic and variational free energy:

| Thermodynamics      | Bayesian inference                    |          |
|---------------------|---------------------------------------|----------|
| Internal energy $E$ | Negative log-likelihood $-\log p(D    | \theta)$ |
| Entropy $S$         | Entropy of $q(\theta)$                |          |
| Temperature $T$     | Regularization parameter $\beta^{-1}$ |          |
| Free energy $F$     | ELBO (negative)                       |          |
| Thermal equilibrium | Optimal posterior                     |          |

**Status**: This correspondence is a formal mathematical isomorphism. It allows transposing intuitions and tools from one domain to another, but does not constitute a proven physical identity.

### 1.4 Central conjecture

Under the following hypotheses:
1. Valid Laplace approximation (locally Gaussian posterior)
2. Slowly varying Fisher metric
3. Stationary data flux

Minimizing variational free energy by natural gradient *would approximate* a geodesic on the statistical manifold and *would converge* to the optimal Bayesian posterior while minimizing total informational cost.

### 1.5 Recursive emergence

When a structure reaches a stable state, it *crystallizes*: its parameters cease to fluctuate significantly. The posterior at level $n$ then becomes the prior at level $n+1$:

$$p_{n+1}(\theta) = p_n(\theta | D_n)$$

At each level, the space of possibilities shrinks: $\mathcal{H}(p_{n+1}) < \mathcal{H}(p_n)$.

---

## 2. Related Work

**Dissipative structures.** Prigogine & Stengers (1984) established that far-from-equilibrium systems can spontaneously self-organize by exporting entropy. Bénard cells, hurricanes, and living systems are canonical examples.

**Information geometry.** Amari (1998) demonstrated the efficiency of the natural gradient for learning. Chentsov's theorem establishes the uniqueness of the Fisher metric as the only reparameterization-invariant Riemannian metric.

**Free energy principle.** Friston (2010) proposed that biological systems minimize a variational free energy to maintain their integrity. This principle provides a theoretical precedent for applying Bayesian formalism to self-organized systems.

**VAE and deep learning.** Kingma & Welling (2014) introduced variational autoencoders. Higgins et al. (2017) showed with β-VAE that explicit constraints can favor the emergence of interpretable representations. Locatello et al. (2019) however demonstrated that a standard VAE does not guarantee an identifiable disentangled representation without inductive bias.

**JEPA.** LeCun (2022) and Balestriero & LeCun (2025) proposed JEPA architectures which, according to our analysis, would constitute a computational instantiation of BEDS principles: JEPA energy would correspond to variational free energy, and the regularizer $R(z)$ to the dissipative constraint.

**Physics of information.** Landauer (1961) established the minimal thermodynamic cost of information erasure. Bennett (1982) showed that reversible computation can in principle be performed without dissipation.

---

## 3. Outlook

### Implications for frugal AI

If the central conjecture is correct, a BEDS network would only require energy to *exist* — that is, to compensate the dissipation that would bring it back toward maximum uncertainty. Learning would not be an additional cost but the survival flux itself.

### Crystallization and fragility

The erratic behaviors of current models (hallucinations, out-of-distribution fragility) could be interpreted as a thermodynamic consequence of excessive crystallization. A BEDS network would maintain a permanent tension between convergence and forgetting via a dissipation parameter $\gamma$, preserving residual plasticity.

### Toward a quantum substrate

A more speculative conjecture suggests that Bayesian formalism could find a natural substrate in quantum computing. In quantum mechanics, the state is intrinsically a probability distribution, measurement is Bayesian conditioning, and superposition maintains uncertainty without crystallization. A quantum BEDS node would not need to *simulate* its uncertainty — it would be physical, encoded in superposition. This path remains highly speculative.

---

## References

Amari, S. (1998). Natural gradient works efficiently in learning. *Neural Computation*, 10(2), 251-276.

Balestriero, R. & LeCun, Y. (2025). LeJEPA: Provable and Scalable Self-Supervised Learning Without the Heuristics. *arXiv:2511.08544*.

Bennett, C.H. (1982). The Thermodynamics of Computation—A Review. *Int. J. Theoretical Physics*, 21(12), 905-940.

Friston, K. (2010). The free-energy principle: a unified brain theory? *Nature Reviews Neuroscience*, 11, 127-138.

Higgins, I., et al. (2017). β-VAE: Learning Basic Visual Concepts with a Constrained Variational Framework. *ICLR*.

Kingma, D.P. & Welling, M. (2014). Auto-Encoding Variational Bayes. *ICLR*.

Landauer, R. (1961). Irreversibility and Heat Generation in the Computing Process. *IBM J. Research and Development*, 5(3), 183-191.

Locatello, F., et al. (2019). Challenging Common Assumptions in the Unsupervised Learning of Disentangled Representations. *ICML*.

Prigogine, I. (1977). *Time, Structure and Fluctuations*. Nobel Lecture.

Prigogine, I. & Stengers, I. (1984). *Order out of Chaos*. Bantam Books.
