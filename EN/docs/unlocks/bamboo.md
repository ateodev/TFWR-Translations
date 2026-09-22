[<- Rice](docs/unlocks/rice.md) <right>[Placing Blocks to Debug ->](docs/unlocks/debug_place.md)
---
# Bamboo

What better way to use our newfound vertical space than to plant bamboo?

Bamboo is a plant that can grow up to 6 blocks tall. It will only grow taller while there is no drone above it, so make sure to move the drone away after using `plant(Entities.Bamboo)`. Planting bamboo costs rice.

Bamboo produces flowers when it reaches a certain height, chosen randomly from 2 to 6 blocks. You can use `measure()` on the bamboo to check the height at which it will flower.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 1000, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": false,
    "items": [{"item": "rice", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
print(measure())
move(East)

for i in range(5):
    do_a_flip() # wait a bit to see it grow.
}}

Bamboo prefers to be harvested at the spot where it flowers. While you can use `harvest()` on a bamboo whenever you want, the yield will be divided by eight for every block of difference from that - so if its flower is at height 3 but you harvest it 2 blocks above that, the yield will be divided by 64.

To control a bamboo's height, fly into it with your drone when the drone is at the desired height. The newly unlocked `place()` command helps with this.

You can use `place(Grounds.Dirt)` to stack blocks next to the bamboo and climb to the desired height. Then use `move()` to fly into the bamboo from the side and knock down the pieces you don't want before calling `harvest()`. When timing bamboo growth, keep in mind that bamboo always grows exactly one block per second.

Using `place(Grounds.Dirt)` costs you 1 block! You can also place other grounds such as `Grounds.Rock` or `Grounds.Limestone`, but not special blocks such as `Grounds.Clay`.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 1000, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": false,
    "items": [{"item": "block", "n": 100}, {"item": "rice", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
for i in range(5):
    dig()
place(Grounds.Dirt)
plant(Entities.Bamboo)
print(measure())
move(East)
dig()
for i in range(2):
    place(Grounds.Dirt)

for i in range(6):
    do_a_flip() # wait a bit for it to grow
move(West)
harvest()
}}

---

[Stats](docs/stats.md)      [For Loop](docs/scripting/for.md)      [Variables](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Functions](docs/scripting/functions.md)      [Rice](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [place()](functions/place)      [measure()](functions/measure)
