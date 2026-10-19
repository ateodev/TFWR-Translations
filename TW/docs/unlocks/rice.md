[<-採礦](docs/unlocks/mining.md) <right>[竹子->](docs/unlocks/bamboo.md)
<right>[石化南瓜->](docs/unlocks/petrified_pumpkins.md)
<right>[珍珠岩與壤土->](docs/unlocks/special_soils.md)
---
# 水稻

在地表和 `Grounds.Dirt` 層下方，你可能注意到了一層薄薄的 `Grounds.Clay`。這種肥沃又濕潤的地塊非常適合種植水稻幼苗。

和草或灌木一樣，只要無人機位於 `Grounds.Clay` 地塊上方，就可以用 `plant(Entities.Rice)` 把水稻幼苗種進黏土，再用 `can_harvest()` 檢查水稻是否完全長成，最後用 `harvest()` 收穫稻米。

種下水稻後，地塊會變成 `Grounds.Rice_Terrace`，為水稻成熟提供理想環境。水稻完全長成後，地塊會變乾，變成 `Grounds.Dry_Rice_Terrace`，無法再種水稻。好在這層黏土有好幾個地塊厚，你可以用 `dig()` 挖掉這個地塊，在下方的 `Grounds.Clay` 上種新的水稻。如果這層黏土用完了，你也隨時可以使用 `clear()` 重設世界，再挖到新的一層。

下面的程式碼可以幫助你向下挖掘，直到找到黏土。

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

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [地下感官](docs/unlocks/underground_senses.md)      [If 陳述式](docs/scripting/if.md)      [For 迴圈](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
