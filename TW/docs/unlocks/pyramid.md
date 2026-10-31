[<-竹子](docs/unlocks/bamboo.md)
---
# 金字塔
現在地下會出現古代金字塔，你可以從中收穫能量，讓無人機加速！

金字塔由沙地塊（`Grounds.Sand`）構成，下方是一層石灰岩（`Grounds.Limestone`）地基。由於年代久遠、遭受侵蝕，找到時總有一部分損壞。石灰岩地基始終完整，但沙層會出現坑洞。

下面展示了一座金字塔遺跡挖出後的樣子：
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
    "items": [{"item": "hay", "n": 100}, {"item": "block", "n": 100}],
    "world_size": {"x": 6, "y": 6},
    "execution_speed": 32,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 7,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite", "quartz"]
}
#SETUP
jump(Unlocks.Pyramid)
move(North)
#CODE
# 往下挖，尋找金字塔地基
while get_ground_type() != Grounds.Limestone:
    dig()

z = get_pos_z() # 記住地基的深度

# 挖掉所有不屬於金字塔的地塊
for i in range(6):
    for j in range(6):
        while (get_ground_type() != Grounds.Limestone
                and get_ground_type() != Grounds.Sand
                and get_pos_z() > z):
            dig()
        move(North)
    move(East)
}}

## 修復金字塔
如你所見，沙層裡有幾個坑洞需要填補。填滿這些坑洞、將金字塔修復還原後，金字塔會自行崩塌，並在石灰岩底座中央產生一株巨大的向日葵。收穫它即可獲得 `Items.Power`。修復的金字塔越大，獲得的能量越多。

使用 `place(Grounds.Sand)` 指令放置地塊，就能修復金字塔。沙是特殊地塊，缺乏適當支撐時會立即塌方。每次放置沙地塊時，必須將其直接放在石灰岩上，或放在 3x3 的沙地塊上。下面是一座用於演示的手工建造小金字塔。當然，自己建造的金字塔不會提供能量：

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
    "items": [{"item": "hay", "n": 100}, {"item": "block", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 4,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#CODE
# 我們需要一個石灰岩地基來放沙
for i in range(3):
    for j in range(3):
        place(Grounds.Limestone)
        move(North)
    move(East)

# 在石灰岩上放一層 3x3 的沙
for i in range(3):
    for j in range(3):
        place(Grounds.Sand)
        move(North)
    move(East)

# 嘗試再放一層 3x3 的沙
# 注意，只有中間的地塊有支撐並留下來
for i in range(3):
    for j in range(3):
        place(Grounds.Sand)
        move(North)
    move(East)
}}

正確修復的金字塔，底部是一塊邊長為奇數（如 5x5）的正方形石灰岩地基。其上是一層同樣規模的沙地塊（5x5），再向上逐層縮小：3x3，最後是 1x1。

金字塔上方的地塊總是泥土。如果想更有效率地挖出金字塔，可以利用這一點。

## 能量
只要有能量，無人機就會以兩倍的速度執行。
無人機每 30 次行動（如移動、收穫、種植……）消耗 1 點能量。
執行其他程式碼陳述式也會消耗能量，但比無人機行動少得多。

總的來說，所有可以透過提升速度來加速的東西都可以使用能量進行加速。
在不考慮速度倍率的情況下，任何使用能量加速的東西消耗的能量都與執行時間成正比。

能量不會影響 `dig()`。

---

[統計資料](docs/stats.md)      [地下感官](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [use_item()](functions/use_item)      [place()](functions/place)
