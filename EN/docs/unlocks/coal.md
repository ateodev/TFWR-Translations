[<- Mining](docs/unlocks/mining.md) <right>[Iron ->](docs/unlocks/iron.md)
<right>[Jumping ->](docs/unlocks/jump.md)
---
# Coal

Different ores are hidden underground, waiting for you to find them and dig them up. If you dig through the surface into `Grounds.Dirt`, the first ore you find is coal.

Its veins form horizontal 1-block thick sheets that you have to find by chance while digging through dirt. The coal blocks inside a sheet sit mostly directly next to each other but some of them can also only be connected diagonally.

You don't have to do anything special to mine coal, just execute `dig()` while the drone is directly on top of a `Grounds.Coal` block. Use `get_ground_type()` to check what is under the drone and `get_ground_type(direction)` to check the four adjacent blocks.

Note that you only get coal for the coal blocks you directly dig into, not for any blocks that cave in around the drone. Keep this in mind when thinking about how to mine coal, so that you can maximize the coal blocks you mine versus the ones that are lost to cave-in.

The coal mines will grow proportionally with the farm size, so consider further unlocking [expand](unlocks/expand) to increase the amount of coal you can mine.

The following program is a good starting point for finding coal. It digs down in search of a coal sheet, then digs to its east and west in hopes of finding more coal.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2
}
#SETUP
move(North)
move(East)
move(East)
#CODE
while get_ground_type() != Grounds.Coal:
    dig()
do_a_flip()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

A simple strategy, especially for smaller farms, is to just dig up all blocks at the depth you found a coal block. To increase efficiency, you can keep track of where you've seen coal blocks using `get_ground_type(direction)` and avoid losing time moving over dirt blocks. You'll need to take extra care not to miss the diagonal connections, which you'll miss when only moving over coal blocks.

---

[Stats](docs/stats.md)      [Mining](docs/unlocks/mining.md)      [Underground Senses](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
