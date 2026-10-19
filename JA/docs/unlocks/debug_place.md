[<- 竹](docs/unlocks/bamboo.md)
---
# カラフルなブロック

ご存じのとおり、`place()`を使うとドローンにブロックを配置させることができます。このアンロックでは、周囲と見分けやすい3つの色付きブロック、`Grounds.Red_Block`、`Grounds.Green_Block`、`Grounds.Blue_Block`が追加されます。

次のように新しいブロックを配置します：

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 10},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "block", "n": 100}],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 5,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"],
    "starting_chunk": 2
}
#SETUP
move(East)
move(North)
#CODE
place(Grounds.Green_Block)
move(East)

place(Grounds.Blue_Block)
move(East)

place(Grounds.Green_Block)
move(North)

place(Grounds.Blue_Block)
move(North)

place(Grounds.Green_Block)
move(West)

place(Grounds.Blue_Block)
move(West)

place(Grounds.Green_Block)
move(South)

place(Grounds.Blue_Block)
move(East)

place(Grounds.Red_Block)
place(Grounds.Red_Block)

do_a_flip()
}}
---

[デバッグ](docs/scripting/debug.md)      [デバッグ 2](docs/unlocks/debug2.md)      [竹](docs/unlocks/bamboo.md)

[place()](functions/place)
