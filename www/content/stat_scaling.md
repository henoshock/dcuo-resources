---
layout: page
title: How Stats Scale
---

*note: this page contains largely technical information*

Here are a few terms:
* Item Level (ilvl): the item level of a piece of gear
* Combat Rating (CR): a numerical measure of your average stats from gear

Some general observations:
* The amount of stats gear and SP give follow exponential growth based on ilvl and points invested, respectively.
    * The growth coefficient is 1.4%; stats will be approximately doubled every 50 ilvls/points.
* DPS gear grants more additional precision than it does additional might.
* Tank gear innately has ~53% more Defense than other roles.
* OP gear considers every stat as a *primary stat*, except for power (which is never a primary stat).

# Gear

Here we focus on how the amount of stats a certain piece of gear gives is determined.

## Combat Rating

There are 13 different types of gear, which we can split into 8 pieces of *armor* and 5 *accessories*:
<table>
    <thead>
        <tr>
            <th>Type</th>
            <th>Name</th>
            <th>Weight</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=8>Armor</td>
            <td>Chest</td>
            <td>12%</td>
        </tr>
        <tr>
            <td>Leg</td>
            <td>12%</td>
        </tr>
        <tr>
            <td>Head</td>
            <td>11%</td>
        </tr>
        <tr>
            <td>Shoulder</td>
            <td>10%</td>
        </tr>
        <tr>
            <td>Back</td>
            <td>8%</td>
        </tr>
        <tr>
            <td>Waist</td>
            <td>7%</td>
        </tr>
        <tr>
            <td>Hands</td>
            <td>6%</td>
        </tr>
        <tr>
            <td>Feet</td>
            <td>6%</td>
        </tr>
        <tr>
            <td rowspan=5>Accessories</td>
            <td>Weapon</td>
            <td>10%</td>
        </tr>
        <tr>
            <td>Neck</td>
            <td>5%</td>
        </tr>
        <tr>
            <td>Ring</td>
            <td>4%</td>
        </tr>
        <tr>
            <td>Face</td>
            <td>3%</td>
        </tr>
        <tr>
            <td>Trinket</td>
            <td>2%</td>
        </tr>
    </tbody>
</table>

Each piece of gear has an *item level* (ilvl); Combat Rating (CR) is equal to 115% of the weighted average of your gear's ilvls.

For a given item level, the amount of stats each piece of gear, relative to other pieces of gear, is given by the ratio of their CR weights. For example, a weapon has a weight of 10%. A neck piece has a weight of 5%, and will give half the amount of stats as the weapon.

## Gear Stat Calculation

Each piece of gear is intended for a particular role. The amount of stats that a piece of gear gives is found by
\\[
S_\text{Gear} = A_\text{Gear} \times W \times (1 + R) \times 1.014^{\text{ilvl} - 1}
\\]
where \\( S_\text{Gear} \\) is the amount of **s**tats the gear gives, with components

* \\( A_\text{Gear} \\): base stat amount, dependent on the specific stat in question
* \\( W \\): the weight given to that type of gear in the CR calculation (as a percentage)
* \\( R \\): multiplier for additional stats given to the *primary stats* for a certain role

For non-tank gear, only "armor" type gear has defense, and is calculated with the above formula. For tank gear, all gear has the full amount of defense as calculated with the above formula.

The base stats \\( A_\text{Gear} \\) are given below.
| Stat | A_\text{Gear} |
|---|---|
| Health | 2000 |
| Defense | 1352 |
| Power | 1000 |
| Precision | 400 |
| Might | 800 |
| Restoration | 400 |
| Vitalization | 250 |
| Dominance | 400 |
| Weaponization Rating | 800 |
| Weapon DPS | 2000 |

The primary stats for each role are given below.
<table>
    <thead>
        <tr>
            <th>Role</th>
            <th>Stats</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=3>DPS</td>
            <td>Might</td>
        </tr>
        <tr>
            <td>Precision</td>
        </tr>
        <tr>
            <td>Weaponization Rating</td>
        </tr>
        <tr>
            <td rowspan=3>Tank</td>
            <td>Health</td>
        </tr>
        <tr>
            <td>Defense</td>
        </tr>
        <tr>
            <td>Dominance</td>
        </tr>
        <tr>
            <td rowspan=1>Healer</td>
            <td>Restoration</td>
        </tr>
        <tr>
            <td rowspan=2>Controller</td>
            <td>Vitalization</td>
        </tr>
        <tr>
            <td>Dominance</td>
        </tr>
    </tbody>
</table>

The role tuning multipliers \\( R \\) are given below. When the stat is not a primary stat of the role, then \\( R = 0 \\).
| Stat | \\( R \\) |
| --- | --- |
| Health | 10% |
| Defense | 10% |
| Precision | 12.5% |
| Might | 10% |
| Restoration | 20% |
| Vitalization | 20% |
| Dominance | 10% |
| Weaponization Rating | 10% |

---

# Stat Points (SP)

There are 6 different categories that you can invest SP into. The amount of stats that category will give you is determined by the amount of points you put into that category:

\\[
S_\text{SP} = A_\text{SP} \times 1.014^{\text{points} - 1}
\\]

The values of \\( A_\text{SP} \\) for the different stats is given by the amount of stats you get when you put only 1 point into that category.
| Stat | \\( A_\text{SP} \\) |
|---|---|
| Health | 400 |
| Power | 300 |
| Precision | 100 |
| Might | 80 |
| Restoration | 80 |
| Vitalization | 45 |
| Dominance | 80 |

The 286th point into a category will give slightly less stats than following this formula, but this formula works for all other amounts of points.

---

Disclaimer: The formulas given are not exact. Some discrepancies will arise at certain ilvls or SP, though only differ from actual values by at most 1. I have not been able to figure out why this happens, but I would guess that it's something to do with rounding.

