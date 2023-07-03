---
layout: page
title: Notes on Testing
---

Base damages were obtained on the test server. Here is a possible setup:

1. Create a fresh character on the test server.
2. Equip some amount of gear. Do not use any tactical mods.
3. (Optional) Spend SP in Superpowered and Might in order to have sufficient power to spam superpowers.
4. Set up an empty league hall for the sparring target.
5. Turn on combat logging.
6. Use the same superpower multiple times.

Once you've gathered sufficient data (I typically aim for at least 100 instances of damage), use the [damage formula](../damage_formula.md) to find the realized value of \\( B \\) for all data points.

You can then use any estimator for \\( B \sim \text{Unif} (a, b) \\). You can simply use the minimum and maximum values as estimates, though my preference is for the UMVUE, which is given by
\\[
\begin{aligned}
\hat{a} &= \frac{n}{n - 1} B_{(1)} - \frac{1}{n - 1} B_{(n)}
\\\\ \hat{b} &= \frac{n}{n - 1} B_{(n)} - \frac{1}{n - 1} B_{(1)}
\end{aligned}
\\]
Where \\( B_{(i)} \\) are the order statistics of the \\( n \\) calculated realizations of \\( B \\). Round these estimates to the nearest intgers; they should be fairly close already.

