[<-採礦](docs/unlocks/mining.md) <right>[鐵礦->](docs/unlocks/iron.md)
<right>[跳轉->](docs/unlocks/jump.md)
---
# 煤炭
地下藏著各種礦石，等著你去發現和挖掘。如果你挖穿地表進入 `Grounds.Dirt`，最先找到的礦石就是煤炭。

開採煤炭不需要任何特殊操作，只要在無人機正好位於 `Grounds.Coal` 地塊上方時執行 `dig()` 即可。使用 `get_ground_type()` 檢查無人機下方是什麼，使用 `get_ground_type(direction)` 檢查四個相鄰地塊。

下面的程式很適合作為尋找煤炭的起點。它會向下挖掘，尋找煤層。
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
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2,
    "exclude_unlocks": ["watering", "fertilizer"]
}
#SETUP
move(North)
move(East)
move(East)
#CODE
# 一直挖，直到出現煤炭地塊
while get_ground_type() != Grounds.Coal:
    dig()

# 開採煤炭
dig()
}}

## 關於坍方
注意，只有你直接挖掘的煤炭地塊才會給你煤炭，無人機周圍坍方的地塊不會。規劃如何開採煤炭時請記住這一點，盡量多挖出煤炭地塊，少因坍方損失。

## 礦脈結構
煤炭礦脈形成厚度為 1 個地塊的水平煤層，你得在挖掘泥土時碰運氣找到它們。煤層中的煤炭地塊大多直接相鄰，但有些也可能只以對角線相連。

煤礦會隨農場規模按比例擴大，因此可以考慮繼續解鎖[擴張](unlocks/expand)，以增加可開採的煤炭數量。

## 策略
<spoiler=顯示提示>
一個簡單的策略是把找到煤炭地塊的那個深度的所有地塊都挖掉，這對較小的農場尤其適用。想提高效率，可以用 `get_ground_type(direction)` 記錄見過煤炭地塊的位置，避免浪費時間在泥土地塊上移動。要特別注意別漏掉以對角線相連的地塊，如果只在煤炭地塊上移動，就會錯過它們。
</spoiler>

---

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [地下感官](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
