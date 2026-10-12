[<- 採礦](docs/unlocks/mining.md) <right>[竹子 ->](docs/unlocks/bamboo.md)
<right>[石化南瓜 ->](docs/unlocks/petrified_pumpkins.md)
<right>[珍珠岩與壤土 ->](docs/unlocks/special_soils.md)
---
# 稻米

你注意到地表下方有一層薄薄的黏土。原來這片肥沃的土地非常適合種植稻秧。

稻米會讓它所種植的黏土乾涸。每個黏土方塊只能使用一次。幸好，這層黏土有好幾格厚。當然，你隨時可以 `clear()` 世界來讓黏土層回來。

下面的程式碼可以幫你向下挖掘直到找到黏土。

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 8,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(East)
#CODE
while get_ground_type() != Grounds.Clay:
    dig()
plant(Entities.Rice)
move(North)
do_a_flip()
}}

---

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [地下感測](docs/unlocks/underground_senses.md)      [if 陳述式](docs/scripting/if.md)      [for 迴圈](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
