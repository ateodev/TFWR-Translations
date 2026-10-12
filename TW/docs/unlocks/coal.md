[<- 採礦](docs/unlocks/mining.md) <right>[鐵 ->](docs/unlocks/iron.md)
<right>[跳躍 ->](docs/unlocks/jump.md)
---
# 煤炭

原來地表正下方的土層是尋找煤礦的好地方。

煤炭會隨機生成在厚度為 1 格的水平薄層中。薄層的大小會隨你的世界大小等比例增長，所以你可能會想擴大世界來找到更多煤炭！

下面的程式是尋找煤炭的好起點。它會向下挖掘尋找煤層，然後往東西兩側挖掘，希望找到更多煤炭。

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
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

---

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [地下感測](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
