# Data Files

Some of these are configurations for the website. Full data for powers is also stored here under the `powers` folder. Here are what the columns represent:

* `anm: {string}`: name of the power
* `lower: {int}`: the lowest base damage the power is capable of
* `upper: {int}`: the highest base damage the power is capable of
* `avg: {numeric}`: the average base damage of the power
* `ticks: {int}`: how many ticks of the base damage occurs; for certain combos or multi-part powers, this will be, and the full damage range will be represented in the previous variables
* `range: {string}`: pretty formatted base damage range
* `avg_td: {numeric}`: average total damage on cast
* `ct: {numeric}`: cast time of the power (how long it locks you out of another action)
* `dpct: {numeric}`: damage per cast time (basically DPS)
* `aoe: {boolean}`: is this power AoE?
* `aoe_dpct`: the power's DPCT if used in an AoE context
* `ttr`: time to reuse
    * for channeled powers: `cooldown - ct`, or 0 when this is negative
    * for non-channeled powers: `cooldown`

