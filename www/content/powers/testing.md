---
layout: page
title: Notes on Testing
---

<a name="section1"></a>
# Base Damages

Base damages were obtained on the test server. Here is a possible setup:

1. Create a fresh character on the test server.
2. Equip some amount of gear. Do not use any tactical mods.
3. (Optional) Spend SP in Superpowered and Might in order to have sufficient power to spam superpowers.
4. Set up an empty league hall for the sparring target.
5. Turn on combat logging.
6. Use the same superpower multiple times.

Once you've gathered sufficient data (I typically aim for at least 100 instances of damage), use the [damage formula](../damage_formula.md) to find the realized value of \\( B \\) for all such data points.

You can then use any estimator for \\( B \sim \text{Unif} (a, b) \\). The most basic one would be the minimum and maximum values as estimates, though my preference is for the UMVUE, which is given by
\\[
\begin{aligned}
\hat{a} &= \frac{n}{n - 1} B_{(1)} - \frac{1}{n - 1} B_{(n)}
\\\\ \hat{b} &= \frac{n}{n - 1} B_{(n)} - \frac{1}{n - 1} B_{(1)}
\end{aligned}
\\]
Where \\( B_{(i)} \\) are the order statistics of the \\( n \\) calculated realizations of \\( B \\). Round these estimates to the nearest intgers; they should be fairly close already.

---

<a name="section2"></a>
# Animation Time

Gameplay was recorded at 60 FPS.

Suppose you are trying to test the animation time of power `A`. You will need any other power to help you test, call it `B`.

1. Cast power `A`. Note that frame at which its icon turns red, i.e. when it goes on cooldown, and call this time `start`.
2. Spam power `B`. Note the frame at which its icon turns red, i.e. when it goes on cooldown, and call this time `stop`.

Then the animation time of power `A` is found by `start - stop`.

Some human error, server lag, etc. is to be expected during this process, so this should be repeated several times. I used the most replicable results to match actual DPS as much as possible, being conservative (tending towards longer times).

`Time to Reuse` is generally equal to `cooldown - animation time`, though may differ in the case of channels.

