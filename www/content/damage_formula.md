---
layout: page
title: The (Might) Damage Formula
---

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>

*additional testing required for precision*

The full damage formula is comprised of 5 components.
\\[
D = B \times S \times O \times I \times P 
\\]
where \( D \) is the final **d**amage dealt value, with components

* \( B \): **b**ase damage
* \( S \): **s**tat multiplier
* \( O \): (user's) **o**utgoing damage modifier
* \( I \): (target's) **i**ncoming damage modifier
* \( P \): (user's) defense **p**enetration modifier

There are two separate modifiers which will clamp the final value \( D \). One occurs when the target's remaining health is less than \( D \), at which then the actual displayed damage is given as the remaining health, or when damaging certain objects, at which then the displayed damage is fixed. The other is just specific mechanics.

\( B \) is uniformly randomly generated from an interval with inclusive integer endpoints. This interval is dependent on the specific power or weapon combo used and (when applicable) the presence of PI. See [here](powers/index) for a list of powers and their base damages.

\( S \) is based on your Might and Precision. For superpowers, \( S = \text{Might} / 200 \). [further testing for prec required]

\( O \) consists of the user's percentage (point) damage adjustments. These are applied additively.

Source | Percent
--- | ---
being in Damage role | 10%
Max Damage hand mod | 2%
Core Strength | 2%
Transformation Card | -21/19/17/15% 

\( I \) depends heavily on the target's defense statistic. At each CR, there is an expected defense, which we can denote \( \Delta_{CR} \); this should be equal to your defense if you were wearing a full set of DPS gear at the same item level with no additional defense modifiers, and is the defense that most enemies will have. Then \( I = 0.8 \times \text{Defense} / \Delta_{CR} \).
Bosses in difficulty tiers higher than elite have increased defense. In raids with stages of Elite, each boss has an additive 25% increase in their defense, up to 100% (doubled) in Critical. Elite Plus bosses also have this doubled defense.

\( P \) is basically only affected by whether or not the user has the Penetrating Strikes chest mod. It technically modifies \( I \), but is applied only for yourself, and only to the target's current defense, therefore after any of the target's defense modifiers. With the mod, \( P = 1 / 0.98 \), otherwise \( P = 1 \).





\\(math \alpha \beta\\) test

\\[
equation test \alpha \beta \bar{x} X \sim \text{Unif} (a, b)
\\\\ asdf
\\ \begin{pmatrix}
1 & n
\\\\ n & 1
\end{pmatrix}
\\]

\\[\begin{align*}
another equation test &= asdf
\\ &= asdfweoi 234 \int_0^1 f (x) \ dx
\end{align*}\\]

\[\begin{align*}
another equation test &= asdf
\\ &= asdfweoi 234 \int_0^1 f (x) \ dx
\end{align*}\]

\(\begin{align*}
environment test
\end{align*}\)

```
asdfkjeifj = eifjeifj
```

sdkffkj

