---
title: "Reformulation SDEB des Équations de Navier-Stokes"
subtitle: "Une approche bayésienne récursive multi-échelle du problème de régularité"
author: "Laurent Caraffa & Claude"
date: "2026-01-03"
status: "Working paper — DRAFT"
---

# Résumé

Ce document propose une reformulation du problème de régularité des équations de Navier-Stokes 3D dans le cadre des Structures Dissipatives Émergentes Bayésiennes (SDEB). L'idée centrale : au lieu de traiter le fluide comme un système monolithique, nous le décomposons en une **hiérarchie récursive d'échelles**, où chaque niveau est une SDEB qui cristallise et devient le prior du niveau suivant.

Cette reformulation traduit la question des singularités en une question de **terminaison de la hiérarchie** : une singularité correspondrait à une cascade infinie qui ne cristallise jamais. Nous conjecturons que la croissance de la dissipation avec le nombre d'onde ($\gamma_n \sim k_n^2$) garantit la cristallisation à chaque niveau, et donc l'absence de singularités.

**Mots-clés** : Navier-Stokes, structures dissipatives, inférence bayésienne, cascade multi-échelle, régularité, turbulence.

---

# 1. Introduction

## 1.1 Le problème du millénaire

Les équations de Navier-Stokes décrivent l'écoulement des fluides visqueux incompressibles :

$$\frac{\partial \mathbf{v}}{\partial t} + (\mathbf{v} \cdot \nabla)\mathbf{v} = -\nabla p + \nu \nabla^2 \mathbf{v}$$

$$\nabla \cdot \mathbf{v} = 0$$

où $\mathbf{v}(\mathbf{x}, t)$ est le champ de vitesse, $p$ la pression, et $\nu > 0$ la viscosité cinématique.

**Question du millénaire (Clay Mathematics Institute)** : Pour des conditions initiales $\mathbf{v}_0 \in C^\infty(\mathbb{R}^3)$ à décroissance rapide, existe-t-il une solution $\mathbf{v}(\mathbf{x}, t)$ lisse pour tout $t > 0$, ou peut-il apparaître des singularités (blow-up) en temps fini ?

## 1.2 L'état de l'art

**Ce qu'on sait** :
- En 2D : régularité globale prouvée (Ladyzhenskaya, 1969)
- En 3D : existence de solutions faibles (Leray, 1934), mais unicité et régularité ouvertes
- Solutions régulières locales en temps (Kato, Fujita)
- Critères conditionnels : si certaines normes restent bornées, pas de singularité (Beale-Kato-Majda, Prodi-Serrin)

**Ce qui coince** : le terme non-linéaire $(\mathbf{v} \cdot \nabla)\mathbf{v}$ permet l'**étirement tourbillonnaire** (vortex stretching) en 3D, absent en 2D. Ce mécanisme peut concentrer la vorticité plus vite que la viscosité ne la diffuse.

## 1.3 Notre approche

Nous proposons de reformuler le problème dans le cadre SDEB en exploitant trois idées :

1. **Décomposition multi-échelle** : le fluide est une hiérarchie d'échelles, pas un bloc monolithique
2. **Récursion bayésienne** : chaque échelle cristallise et devient le prior de la suivante
3. **Cristallisation comme régularité** : une singularité = une hiérarchie qui ne termine pas

---

# 2. Navier-Stokes comme Structure Dissipative

## 2.1 Identification des composants SDEB

| Composant SDEB | Navier-Stokes |
|----------------|---------------|
| Système ouvert | Domaine fluide avec conditions aux limites |
| Flux entrant | Énergie injectée aux grandes échelles (forçage) |
| État interne | Champ de vitesse $\mathbf{v}(\mathbf{x}, t)$ |
| Dissipation | Terme visqueux $\nu \nabla^2 \mathbf{v}$ |
| Entropie exportée | Chaleur (dissipation visqueuse) |
| Structure maintenue | Écoulement organisé (vs chaos thermique) |

## 2.2 Bilan énergétique

L'énergie cinétique totale :

$$E(t) = \frac{1}{2} \int_{\mathbb{R}^3} |\mathbf{v}|^2 \, d\mathbf{x}$$

satisfait :

$$\frac{dE}{dt} = -\nu \int_{\mathbb{R}^3} |\nabla \mathbf{v}|^2 \, d\mathbf{x} = -\varepsilon(t) \leq 0$$

où $\varepsilon(t)$ est le taux de dissipation. **L'énergie décroît toujours** — c'est une structure dissipative.

## 2.3 Bilan d'enstrophie

L'enstrophie (carré de la vorticité intégré) :

$$\Omega(t) = \frac{1}{2} \int_{\mathbb{R}^3} |\boldsymbol{\omega}|^2 \, d\mathbf{x}, \quad \boldsymbol{\omega} = \nabla \times \mathbf{v}$$

satisfait :

$$\frac{d\Omega}{dt} = \underbrace{\int \boldsymbol{\omega} \cdot (\boldsymbol{\omega} \cdot \nabla)\mathbf{v} \, d\mathbf{x}}_{\text{étirement tourbillonnaire } P(t)} - \underbrace{\nu \int |\nabla \boldsymbol{\omega}|^2 \, d\mathbf{x}}_{\text{dissipation } D(t)}$$

**Le drame en 3D** : $P(t)$ peut être positif et croître plus vite que $D(t)$.

## 2.4 La question reformulée

Dans le langage SDEB :

> **La dissipation visqueuse est-elle toujours suffisante pour que la structure cristallise (atteigne un état régulier), ou peut-elle échouer à contrôler la production d'enstrophie, menant à une "explosion" de l'incertitude locale ?**

---

# 3. Décomposition Multi-Échelle Récursive

## 3.1 Décomposition spectrale

Décomposons le champ de vitesse en échelles via Fourier :

$$\mathbf{v}(\mathbf{x}, t) = \sum_{n=0}^{\infty} \mathbf{v}_n(\mathbf{x}, t)$$

où $\mathbf{v}_n$ contient les modes de nombre d'onde $k \in [k_n, k_{n+1})$ avec $k_n = 2^n k_0$.

Chaque $\mathbf{v}_n$ représente les structures à l'échelle $\ell_n \sim 1/k_n$.

## 3.2 La cascade de Kolmogorov revisitée

Kolmogorov (1941) a établi phénoménologiquement :

1. L'énergie est **injectée** aux grandes échelles ($n = 0$)
2. Elle **cascade** vers les petites échelles via le terme non-linéaire
3. Elle est **dissipée** à l'échelle de Kolmogorov $\eta = (\nu^3/\varepsilon)^{1/4}$

**Notre reformulation** : cette cascade est une **hiérarchie SDEB récursive** où chaque niveau cristallise avant de passer le flux au suivant.

## 3.3 La hiérarchie SDEB

```
Niveau 0 : Grandes échelles
    - Flux entrant : forçage externe Φ₀
    - État : distribution q₀(v₀)
    - Dissipation : γ₀ = ν k₀²
    - Cristallisation : posterior p₀(v₀ | données) concentré
            ↓
    Le posterior p₀ devient le prior du niveau 1
            ↓
Niveau 1 : Échelles intermédiaires
    - Flux entrant : résidu non cristallisé du niveau 0
    - État : distribution q₁(v₁)
    - Dissipation : γ₁ = ν k₁² = 4 γ₀
    - Cristallisation : posterior p₁(v₁ | p₀)
            ↓
    Le posterior p₁ devient le prior du niveau 2
            ↓
Niveau n : Échelle 2⁻ⁿ
    - Flux entrant : Φₙ (cascade depuis n-1)
    - État : distribution qₙ(vₙ)
    - Dissipation : γₙ = ν kₙ² = 4ⁿ γ₀
    - Cristallisation : posterior pₙ(vₙ | pₙ₋₁)
            ↓
           ...
            ↓
Niveau N* : Échelle de Kolmogorov
    - Dissipation domine totalement
    - Cristallisation terminale : tout le flux est dissipé
```

## 3.4 Propriété clé : croissance de la dissipation

À chaque niveau :

$$\gamma_n = \nu k_n^2 = \nu (2^n k_0)^2 = 4^n \gamma_0$$

**La dissipation croît exponentiellement avec le niveau.**

C'est la clé : même si le flux cascadant croît, la dissipation croît plus vite (exponentiellement vs polynomialement en général).

---

# 4. Formalisation Bayésienne

## 4.1 État probabiliste à chaque niveau

Au lieu de considérer $\mathbf{v}_n(t)$ comme déterministe, nous considérons une **distribution** $q_n(\mathbf{v}_n, t)$ sur les configurations possibles à l'échelle $n$.

Cette distribution encode notre **incertitude** sur l'état du fluide à cette échelle, étant donné ce qui s'est cristallisé aux échelles supérieures.

## 4.2 Énergie libre variationnelle par niveau

Pour chaque niveau $n$, définissons l'énergie libre variationnelle :

$$\mathcal{F}_n[q_n] = D_{KL}(q_n \| p_{n-1}) + \mathbb{E}_{q_n}\left[\frac{1}{2}\int |\mathbf{v}_n|^2 \, d\mathbf{x}\right]$$

où :
- $D_{KL}(q_n \| p_{n-1})$ mesure l'écart au prior (le posterior cristallisé du niveau précédent)
- Le second terme est l'énergie cinétique moyenne à cette échelle

## 4.3 Dynamique de l'énergie libre

L'évolution de $\mathcal{F}_n$ est gouvernée par :

$$\frac{d\mathcal{F}_n}{dt} = \underbrace{\Phi_n}_{\text{flux entrant depuis } n-1} - \underbrace{\gamma_n \cdot \mathcal{D}_n}_{\text{dissipation}} + \underbrace{\mathcal{C}_n}_{\text{couplage non-linéaire}}$$

où :
- $\Phi_n$ est le flux d'énergie cascadant depuis le niveau $n-1$
- $\mathcal{D}_n$ est un terme de dissipation (toujours positif)
- $\mathcal{C}_n$ encode les interactions entre échelles

## 4.4 Condition de cristallisation

**Définition** : Le niveau $n$ **cristallise** si :

$$\mathcal{F}_n(t) \to \mathcal{F}_n^* < \infty \quad \text{quand } t \to \infty$$

et la distribution $q_n$ se concentre autour d'un état $\mathbf{v}_n^*$ :

$$q_n(\mathbf{v}_n, t) \to \delta(\mathbf{v}_n - \mathbf{v}_n^*)$$

ou plus généralement, la variance $\sigma_n^2 \to \sigma_{n,*}^2 < \infty$.

## 4.5 Récursion bayésienne

Une fois le niveau $n$ cristallisé, son posterior devient le prior du niveau $n+1$ :

$$p_n(\mathbf{v}_n) := \lim_{t \to \infty} q_n(\mathbf{v}_n, t)$$

Ce prior encode les **axiomes** que le niveau $n+1$ hérite : la structure à grande échelle est fixée, seules les fluctuations à plus petite échelle restent à déterminer.

---

# 5. La Conjecture Centrale

## 5.1 Énoncé informel

> **Conjecture SDEB-Navier-Stokes** : Pour les équations de Navier-Stokes 3D avec viscosité $\nu > 0$, la hiérarchie SDEB multi-échelle **cristallise à chaque niveau** en temps fini. Par conséquent, il n'existe pas de singularité en temps fini.

## 5.2 Énoncé formel

**Conjecture** : Soit $\mathbf{v}_0 \in C^\infty(\mathbb{R}^3)$ une condition initiale à décroissance rapide. Considérons la décomposition multi-échelle $\mathbf{v} = \sum_n \mathbf{v}_n$ et la hiérarchie SDEB associée. Alors :

1. **Cristallisation niveau par niveau** : Pour tout $n \geq 0$, il existe $T_n < \infty$ tel que le niveau $n$ cristallise pour $t > T_n$.

2. **Terminaison de la hiérarchie** : Il existe $N^* < \infty$ tel que pour $n > N^*$, le flux entrant $\Phi_n$ est entièrement dissipé ($\mathcal{F}_n \equiv 0$).

3. **Régularité** : La solution $\mathbf{v}(\mathbf{x}, t) = \sum_{n=0}^{N^*} \mathbf{v}_n^*(\mathbf{x}, t)$ est $C^\infty$ pour tout $t > 0$.

## 5.3 Intuition

**Pourquoi ça devrait marcher** :

La dissipation au niveau $n$ est $\gamma_n = \nu k_n^2 = 4^n \gamma_0$.

Le flux cascadant $\Phi_n$ croît au plus polynomialement (théorie de Kolmogorov : $\Phi_n \sim \varepsilon$ constant dans la zone inertielle).

Donc pour $n$ assez grand :

$$\gamma_n \cdot \mathcal{D}_n \gg \Phi_n$$

La dissipation **domine** le flux entrant. Le niveau cristallise.

**L'échelle de Kolmogorov** $\eta = (\nu^3/\varepsilon)^{1/4}$ est précisément l'échelle où $\gamma_n \sim \Phi_n$ — en dessous, tout est dissipé.

## 5.4 Ce qui reste à prouver

Pour transformer cette conjecture en théorème, il faudrait :

1. **Borner le flux cascadant** : montrer que $\Phi_n \leq C \cdot \varepsilon$ pour une constante universelle

2. **Borner le couplage non-linéaire** : montrer que $|\mathcal{C}_n| \leq C' \cdot \Phi_n$ (le couplage ne peut pas amplifier arbitrairement)

3. **Inégalité de Grönwall récursive** : en déduire que $\mathcal{F}_n(t) \leq \mathcal{F}_n(0) e^{-\alpha_n t} + \beta_n$ avec $\alpha_n > 0$

---

# 6. Lien avec la Singularité

## 6.1 Qu'est-ce qu'une singularité dans ce cadre ?

**Définition SDEB** : Une singularité correspondrait à une situation où **la hiérarchie ne termine pas** :

- Soit un niveau $n$ ne cristallise jamais ($\mathcal{F}_n \to \infty$)
- Soit le nombre de niveaux actifs $N^* \to \infty$ en temps fini

## 6.2 Scénario de singularité (hypothétique)

Pour qu'une singularité se produise, il faudrait :

1. Le flux cascadant $\Phi_n$ croît plus vite que $4^n$ (plus vite qu'exponentiel)
2. Ou le couplage $\mathcal{C}_n$ amplifie le flux de manière incontrôlée

**Physiquement** : cela correspondrait à un "emballement" de la cascade, où l'étirement tourbillonnaire crée de la structure à des échelles arbitrairement petites plus vite que la viscosité ne peut la dissiper.

## 6.3 Pourquoi c'est (probablement) impossible

**Argument dimensionnel** : Le taux de transfert d'énergie entre échelles est borné par :

$$\Phi_n \lesssim \frac{v_n^3}{\ell_n}$$

où $v_n$ est la vitesse typique à l'échelle $\ell_n$.

Pour que $\Phi_n$ croisse plus vite que $4^n$, il faudrait $v_n \gtrsim k_n^{1/3} \cdot C^n$ pour $C > 4^{1/3}$.

Mais l'énergie totale est bornée : $\sum_n v_n^2 / k_n \leq E_0 < \infty$.

Cette contrainte **limite** la croissance possible de $v_n$, et donc de $\Phi_n$.

**C'est essentiellement l'argument de Kolmogorov** : la cascade est "auto-régulée" par la conservation de l'énergie.

---

# 7. Formalisation Mathématique Détaillée

## 7.1 Espace fonctionnel

Travaillons dans $L^2(\mathbb{R}^3)^3$ avec la décomposition de Littlewood-Paley :

$$\mathbf{v} = \sum_{n=-1}^{\infty} \Delta_n \mathbf{v}$$

où $\Delta_n$ est le projecteur sur les fréquences $|\xi| \sim 2^n$.

## 7.2 Équation par niveau

L'équation de Navier-Stokes projetée au niveau $n$ :

$$\frac{\partial \mathbf{v}_n}{\partial t} + \Delta_n[(\mathbf{v} \cdot \nabla)\mathbf{v}] = -\Delta_n \nabla p + \nu \nabla^2 \mathbf{v}_n$$

Le terme non-linéaire couple les échelles :

$$\Delta_n[(\mathbf{v} \cdot \nabla)\mathbf{v}] = \sum_{j,k} \Delta_n[(\mathbf{v}_j \cdot \nabla)\mathbf{v}_k]$$

## 7.3 Bilan d'énergie par niveau

$$\frac{d}{dt}\|\mathbf{v}_n\|_{L^2}^2 = -2\nu \|\nabla \mathbf{v}_n\|_{L^2}^2 + T_n$$

où $T_n$ est le transfert net d'énergie :

$$T_n = -2 \int \mathbf{v}_n \cdot \Delta_n[(\mathbf{v} \cdot \nabla)\mathbf{v}] \, d\mathbf{x}$$

## 7.4 Distribution variationnelle

Posons $q_n(\mathbf{v}_n, t)$ une distribution gaussienne :

$$q_n(\mathbf{v}_n) = \mathcal{N}(\boldsymbol{\mu}_n, \Sigma_n)$$

où $\boldsymbol{\mu}_n$ est la moyenne et $\Sigma_n$ la covariance dans l'espace des modes de Fourier au niveau $n$.

## 7.5 Énergie libre variationnelle explicite

$$\mathcal{F}_n = \frac{1}{2}\text{Tr}(\Sigma_{n-1}^{-1}\Sigma_n) - \frac{1}{2}\log\det(\Sigma_{n-1}^{-1}\Sigma_n) - \frac{d_n}{2} + \frac{1}{2}\|\boldsymbol{\mu}_n\|^2$$

où $d_n$ est la dimension de l'espace des modes au niveau $n$.

## 7.6 Dynamique de la variance

En approximation gaussienne, la variance $\sigma_n^2 = \text{Tr}(\Sigma_n)/d_n$ évolue selon :

$$\frac{d\sigma_n^2}{dt} = \underbrace{\phi_n}_{\text{flux entrant}} - \underbrace{2\gamma_n \sigma_n^2}_{\text{dissipation}} + \underbrace{c_n}_{\text{couplage}}$$

avec $\gamma_n = \nu k_n^2 \sim 4^n \nu k_0^2$.

## 7.7 Condition de cristallisation explicite

Le niveau $n$ cristallise si et seulement si :

$$2\gamma_n > \frac{\partial \phi_n}{\partial \sigma_n^2} + \frac{\partial c_n}{\partial \sigma_n^2}$$

c'est-à-dire si la dissipation est plus forte que la sensibilité du flux et du couplage à l'incertitude.

---

# 8. Pistes de Preuve

## 8.1 Stratégie générale

1. **Montrer la cristallisation du niveau 0** (grandes échelles) — c'est le cas "facile", essentiellement la théorie des solutions faibles de Leray

2. **Propagation de la cristallisation** : si les niveaux $0, ..., n-1$ ont cristallisé, montrer que le niveau $n$ cristallise aussi

3. **Terminaison** : montrer qu'il existe $N^*$ tel que $\Phi_n \approx 0$ pour $n > N^*$

## 8.2 Outils potentiels

**Inégalités de Bernstein** : contrôle des normes de $\mathbf{v}_n$ en fonction de $n$

$$\|\nabla^k \mathbf{v}_n\|_{L^p} \lesssim 2^{nk} \|\mathbf{v}_n\|_{L^p}$$

**Lemme de Grönwall récursif** : si $\frac{d\mathcal{F}_n}{dt} \leq -\alpha_n \mathcal{F}_n + \beta_n$ avec $\alpha_n = c \cdot 4^n$, alors :

$$\mathcal{F}_n(t) \leq \mathcal{F}_n(0) e^{-\alpha_n t} + \frac{\beta_n}{\alpha_n}$$

et $\mathcal{F}_n \to \beta_n/\alpha_n < \infty$ quand $t \to \infty$.

**Estimations de Bony** : contrôle du terme non-linéaire par paraproduct

## 8.3 Le point crucial

Tout repose sur la **borne du flux cascadant** $\Phi_n$.

Si on peut montrer :

$$\Phi_n \leq C \cdot \varepsilon \cdot f(n)$$

avec $f(n)$ sous-exponentiel (polynomial, par exemple), alors $\gamma_n = 4^n \gamma_0$ gagne pour $n$ grand.

**C'est exactement ce que la théorie K41 de Kolmogorov prédit** ($\Phi_n \approx \varepsilon$ = constante dans la zone inertielle), mais le prouver rigoureusement à partir des équations est le cœur du problème.

---

# 9. Discussion

## 9.1 Ce que cette reformulation apporte

1. **Nouvelle perspective** : le problème de régularité devient un problème de terminaison de hiérarchie

2. **Outils bayésiens** : accès aux inégalités variationnelles, bornes entropiques, etc.

3. **Intuition physique renforcée** : la cristallisation récursive formalise la cascade de Kolmogorov

4. **Critère de singularité** : une singularité = hiérarchie infinie en temps fini

## 9.2 Difficultés restantes

1. **Formaliser le couplage** : le terme $\mathcal{C}_n$ mélange les échelles de manière complexe

2. **Passage du probabiliste au déterministe** : montrer que la cristallisation de $q_n$ implique la régularité de $\mathbf{v}_n$

3. **Uniformité en $n$** : s'assurer que les constantes ne dégénèrent pas

## 9.3 Connexion avec les approches existantes

| Approche | Lien avec SDEB |
|----------|----------------|
| Solutions faibles de Leray | Cristallisation partielle (énergie bornée, pas l'enstrophie) |
| Critère de Beale-Kato-Majda | Condition pour que la hiérarchie ne termine pas |
| Espaces de Besov | Espace naturel pour la décomposition multi-échelle |
| Théorie K41 | Version phénoménologique de notre hiérarchie |

## 9.4 Et si la conjecture est fausse ?

Si des singularités existent, le cadre SDEB prédit :

- Il existe des conditions initiales pour lesquelles la hiérarchie **ne termine pas**
- Le flux cascadant croît super-exponentiellement
- La "cristallisation pathologique" crée une concentration de vorticité infinie

Cela donnerait un **critère constructif** pour chercher des singularités : trouver des données initiales qui empêchent la cristallisation récursive.

---

# 10. Conclusion et Programme de Recherche

## 10.1 Résumé

Nous avons proposé une reformulation du problème de régularité de Navier-Stokes 3D dans le cadre SDEB :

1. Le fluide est une **hiérarchie récursive** de structures dissipatives
2. Chaque échelle **cristallise** (converge) et devient le **prior** de l'échelle suivante
3. La **dissipation croît exponentiellement** avec le niveau ($\gamma_n \sim 4^n$)
4. Une **singularité** correspondrait à une hiérarchie qui ne termine pas
5. La croissance de la dissipation devrait **garantir la terminaison**

## 10.2 Programme de recherche

**Court terme** :
- [ ] Formaliser rigoureusement la décomposition SDEB
- [ ] Prouver la cristallisation du niveau 0
- [ ] Établir le lemme de propagation (niveau $n-1$ → niveau $n$)

**Moyen terme** :
- [ ] Borner le flux cascadant $\Phi_n$
- [ ] Contrôler le couplage non-linéaire $\mathcal{C}_n$
- [ ] Établir l'inégalité de Grönwall récursive

**Long terme** :
- [ ] Prouver la terminaison de la hiérarchie
- [ ] En déduire la régularité globale
- [ ] Ou identifier les obstructions et caractériser les singularités potentielles

## 10.3 Mot de la fin

Cette reformulation ne résout pas (encore) le problème du millénaire. Mais elle offre un **angle d'attaque nouveau**, ancré dans la physique des structures dissipatives et le formalisme bayésien.

Si Kolmogorov avait raison — si la cascade est bien auto-régulée et termine toujours à l'échelle dissipative — alors le cadre SDEB fournit peut-être le langage pour le prouver.

Et si des singularités existent, ce cadre nous dit exactement **quoi chercher** : des conditions initiales qui brisent la récursion, des configurations où le flux croît plus vite que la dissipation, des hiérarchies qui refusent de cristalliser.

Dans les deux cas, c'est un pas en avant.

---

# Références

## Navier-Stokes et régularité

- Leray, J. (1934). Sur le mouvement d'un liquide visqueux emplissant l'espace. *Acta Mathematica*, 63, 193-248.
- Ladyzhenskaya, O.A. (1969). *The Mathematical Theory of Viscous Incompressible Flow*. Gordon and Breach.
- Beale, J.T., Kato, T., & Majda, A. (1984). Remarks on the breakdown of smooth solutions for the 3-D Euler equations. *Communications in Mathematical Physics*, 94, 61-66.
- Fefferman, C. (2000). Existence and smoothness of the Navier-Stokes equation. *Clay Mathematics Institute Millennium Problems*.

## Turbulence et cascade

- Kolmogorov, A.N. (1941). The local structure of turbulence in incompressible viscous fluid for very large Reynolds numbers. *Doklady Akademii Nauk SSSR*, 30, 299-303.
- Frisch, U. (1995). *Turbulence: The Legacy of A.N. Kolmogorov*. Cambridge University Press.

## Analyse harmonique et espaces de Besov

- Bony, J.-M. (1981). Calcul symbolique et propagation des singularités pour les équations aux dérivées partielles non linéaires. *Annales scientifiques de l'École normale supérieure*, 14(2), 209-246.
- Bahouri, H., Chemin, J.-Y., & Danchin, R. (2011). *Fourier Analysis and Nonlinear Partial Differential Equations*. Springer.

## Structures dissipatives et inférence bayésienne

- Prigogine, I. (1977). *Time, Structure and Fluctuations*. Nobel Lecture.
- Amari, S. (1998). Natural gradient works efficiently in learning. *Neural Computation*, 10(2), 251-276.
- Friston, K. (2010). The free-energy principle: a unified brain theory? *Nature Reviews Neuroscience*, 11, 127-138.

---

*Document de travail. Les conjectures présentées ici sont des propositions théoriques nécessitant une validation rigoureuse. Toute critique constructive est bienvenue.*


