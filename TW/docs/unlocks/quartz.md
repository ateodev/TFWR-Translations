[<-鐵礦](docs/unlocks/iron.md) <right>[蘑菇->](docs/unlocks/mushroom.md)
---
# 石英
從 `Grounds.Rock` 中的鐵礦脈繼續往下，你會在岩石層下部及其下方堅硬的 `Grounds.Dirt` 中找到石英（可以用[地下感官](docs/unlocks/underground_senses.md)解鎖項中的 `get_hardness()` 檢查硬度）。

下面的程式碼片段會挖穿泥土，進入岩石層。接著它會一邊挖掘一邊持續探查石英，直到距離小於 2 為止。最後，它會列印出最終得到的探查距離。
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
    "items": [{"item": "block", "n": 1}, {"item": "iron", "n": 100}],
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
# 往下挖到岩石層
while get_ground_type() != Grounds.Rock:
    dig()

# 繼續挖，直到石英礦脈就在附近
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# 列印到礦脈的最終距離
print(prospect_quartz())
}}

## 礦脈結構
石英礦脈呈針狀，形成垂直的柱狀結構，單憑碰運氣很難挖掘到。

## 探查石英
好在我們可以把鐵礦加工成類似探礦杖的東西，更容易找到石英礦脈。對應的指令是 `prospect_quartz()`。

`prospect_quartz()` 的工作方式與 `prospect_iron()` 不同。它不會回傳無人機該往哪個方向移動才能接近最近的鐵礦石，而是回傳最近的石英地塊與無人機之間的精確三維距離（歐幾里得距離）。

執行 `prospect_quartz()` 指令需消耗 1 份鐵礦，最好省著用。

如果附近沒有石英，或者鐵礦不足以執行探查，`prospect_quartz()` 就會回傳 `None`。

## 策略
<spoiler=顯示提示>你可以反覆探查並移動，觀察距離如何變化。在平坦的表面上，設法讓距離縮到最小，就能讓你來到石英礦脈的上方。你可以使用類似二分搜尋的策略，盡量減少 `prospect_quartz()` 的呼叫次數，以及這些呼叫消耗的鐵礦。

更進階的策略可以用二維幾何求出兩個或多個圓的交點，你也可以挑戰困難路線，用完整的三邊測量求三個球體的交點，找出礦脈精確的三維位置。

注意，要計算平方根，可以使用冪運算子，例如要取得 16 的平方根，就用 `16**0.5`。遊戲沒有提供三角函數或向量的內建數學函數，你需要自己實作。

另外，附近可能有多條礦脈，所以在相近位置多次測量時，結果未必指向同一條礦脈。</spoiler>

---

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [地下感官](docs/unlocks/underground_senses.md)      [變數](docs/scripting/variables.md)      [運算子](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
