[<-鐵礦](docs/unlocks/iron.md) <right>[蘑菇->](docs/unlocks/mushroom.md)
---
# 石英

從 `Grounds.Rock` 中的鐵礦脈繼續往下，你會在岩石層下部及其下方堅硬的 `Grounds.Dirt` 中找到石英（可以用[地下感官](docs/unlocks/underground_senses.md)解鎖項中的 `get_hardness()` 檢查硬度）。

石英礦脈呈針狀，形成垂直的柱狀結構，單憑碰運氣很難挖掘到。

好在我們可以把鐵礦加工成類似探礦杖的東西，更容易找到石英礦脈。對應的指令是 `prospect_quartz()`。

`prospect_quartz()` 的工作方式與 `prospect_iron()` 不同。它不會回傳最近石英礦石的方向，而是回傳到最近石英的歐幾里得距離（三維距離）。執行 `prospect_quartz()` 指令需消耗 1 份鐵礦，最好省著用。

如果附近沒有石英，或者鐵礦不足以執行探查，`prospect_quartz()` 就會回傳 `None`。

下面的程式碼片段會讓無人機挖穿泥土，深入岩石層。運氣好的話，附近就有一條石英礦脈，無人機會列印出到它的距離。

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

你可以反覆探查並移動，觀察距離如何變化，從而判斷自己是在靠近還是遠離礦脈。可以用二維幾何求出兩個或多個圓的交點，找到礦脈的水平位置後向下挖。也可以用完整的三邊測量求三個球體的交點，找出精確的三維位置。

注意，遊戲沒有提供平方根、三角函數或向量等基礎數學函數，你需要自己實作。另外，附近可能有多條礦脈，所以在相近位置多次測量時，結果未必指向同一條礦脈，可能會把你帶偏。

---

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [地下感官](docs/unlocks/underground_senses.md)      [變數](docs/scripting/variables.md)      [運算子](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
