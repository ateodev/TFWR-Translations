[<- 鐵](docs/unlocks/iron.md) <right>[蘑菇 ->](docs/unlocks/mushroom.md)
---
# 石英

石英以針狀礦脈生長在石層底部附近以及其下方的硬土中。這些礦脈呈垂直柱狀，靠反覆嘗試很難找到。

幸好，我們可以把鐵扭成類似探測杖的東西，讓我們更容易找到這些石英礦脈。對應的指令是 `prospect_quartz()`。

`prospect_quartz()` 的運作方式和 `prospect_iron()` 不同。它不會回傳最近石英礦的方向，而是回傳到最近石英的歐幾里得距離（3D 距離）。執行 `prospect_quartz()` 需要消耗 1 個鐵，所以最好省著點用。

如果 `prospect_quartz()` 在附近找不到任何石英，或者你的鐵不足以進行搜尋，它會回傳 `None`。

下面的程式碼片段會讓你的無人機挖穿泥土，深入岩層。然後，運氣好的話，附近就會有一條石英礦脈，這時無人機會印出到它的距離。

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
    "items": [{"item": "hay", "n": 100}, {"item": "iron", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite"]
}

#CODE
move(East)
move(North)
while get_ground_type() != Grounds.Rock:
    dig()
for i in range(30):
    dig()
do_a_flip()
do_a_flip()
print(prospect_quartz())
}}

---

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [地下感測](docs/unlocks/underground_senses.md)      [變數](docs/scripting/variables.md)      [運算子](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
