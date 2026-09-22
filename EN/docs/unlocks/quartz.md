[<- Iron](docs/unlocks/iron.md) <right>[Mushroom ->](docs/unlocks/mushroom.md)
---
# Quartz

Quartz grows in needle-shaped veins near the bottom of the stone layer and in the hard dirt below it. The veins form vertical columns, making them quite difficult to find through trial and error.

Luckily, we can use our iron and mangle it into something similar to a dowsing rod that allows us to locate these quartz veins more easily. The command for this is `prospect_quartz()`.

`prospect_quartz()` works differently from `prospect_iron()`. Instead of returning the direction to the closest quartz ore, it returns the Euclidean distance (3D distance) to the closest quartz. Executing `prospect_quartz()` costs 1 iron, so it might be a good idea to use the command sparingly.

If `prospect_quartz()` can't find any nearby quartz, or if you don't have enough iron to perform the search, it returns `None`.

The following code snippet lets your drone dig past the rock layer. Then, with a bit of luck, a quartz vein will be nearby, in which case your drone will print the distance to it.

`while get_ground_type() != Grounds.Rock:
        dig()
while get_ground_type() != Grounds.Dirt:
        dig()
print(prospect_quartz())
`

---

[Stats](docs/stats.md)      [Mining](docs/unlocks/mining.md)      [Underground Senses](docs/unlocks/underground_senses.md)      [Variables](docs/scripting/variables.md)      [Operators](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
