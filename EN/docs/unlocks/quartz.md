[<- Iron](docs/unlocks/iron.md) <right>[Mushroom ->](docs/unlocks/mushroom.md)
---
# Quartz

Continuing from the iron veins in `Grounds.Rock`, you find quartz in the lower part of the rock layer and into the hard `Grounds.Dirt` below (check the hardness using `get_hardness()` from the [underground senses](docs/unlocks/underground_senses.md) unlock).

The following code snippet lets your drone dig past the dirt and deep into the rock layer. Then, with a bit of luck, a quartz vein will be nearby, in which case your drone will print the distance to it.
{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite"]
}
#SETUP
move(East)
move(North)
#CODE
while get_ground_type() != Grounds.Rock:
    dig()
for i in range(30):
    dig()

print(prospect_quartz())
move(South)
print(prospect_quartz())
}}

## Vein Structure
Quartz grows in needle-shaped veins that form vertical columns, making them quite difficult to find through trial and error.

## Prospecting Quartz
Luckily, we can use our iron and mangle it into something similar to a dowsing rod that allows us to locate these quartz veins more easily. The command for this is `prospect_quartz()`.

`prospect_quartz()` works differently from `prospect_iron()`. Instead of returning the direction for the drone to move towards the closest iron ore, it returns the exact 3D distance between the closest Quartz block and the drone (Euclidean distance).

Executing `prospect_quartz()` costs 1 iron, so it might be a good idea to use the command sparingly.

If `prospect_quartz()` can't find any nearby quartz, or if you don't have enough iron to perform the search, it returns `None`.

## Strategy
<spoiler=show hint>
You can repeatedly prospect and move to see how the distance changes, telling you if you move closer or further away from a vein. You can use 2D geometry to find the intersection between two or more circles to find the horizontal position of a vein and dig down. Or you can use full triliteration to intersect three spheres and find the exact 3D position.

Note that there aren't any built-in math functions for square root, trigonometry or vectors, you'll have to implement them yourself. Also note that there can be multiple veins in the vicinity, so if you take multiple nearby measurements, they might not point to the same vein and lead you astray.
</spoiler>

---

[Stats](docs/stats.md)      [Mining](docs/unlocks/mining.md)      [Underground Senses](docs/unlocks/underground_senses.md)      [Variables](docs/scripting/variables.md)      [Operators](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
