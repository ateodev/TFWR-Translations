[<-石英](docs/unlocks/quartz.md) <right>[炸藥->](docs/unlocks/dynamite.md)
---
# 蘑菇
地下有許多種蘑菇成群生長。挖掘時尋找一層 `Grounds.Mushroom`。隨後，可以對地塊使用 `measure()`，以數字形式取得蘑菇類型，範圍從 `0` 到 `5`。

下面的程式碼會找到一些蘑菇，並列印它們的類型：
{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 6},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "digging_speed": 6,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron"]
}
#SETUP
jump(Unlocks.Mushrooms)
#CODE
# 處理一排蘑菇
for i in range(get_world_size()):
    # 往下挖到最上方的蘑菇地塊
    while get_ground_type() != Grounds.Mushroom:
        dig()

    # 列印蘑菇類型的編號
    print(measure())

    move(East)
}}

## 如何收集蘑菇
同類蘑菇喜歡待在一起，卻又有點太害羞，不會疊著長。使用 `push(direction)` 可以推動無人機下方的蘑菇地塊。

把兩個相同類型的蘑菇地塊疊在一起，它們就會被自動收穫，讓你獲得蘑菇。

下面的程式碼會先騰出空間，然後推動一個蘑菇地塊，直到它與下方的蘑菇相符為止：
{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 6},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "digging_speed": 6,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 3,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron", "special_soils"]
}
#SETUP
jump(Unlocks.Mushrooms)
#CODE
while get_ground_type() != Grounds.Mushroom:
    dig()

depth = get_pos_z()
for i in range(2):
    # 騰出空間，以便把蘑菇地塊往東推
    move(East)
    while get_pos_z() > depth - 1:
        dig()
    # 移回去、推動，再跟上被推動的地塊
    move(West)
    push(East) # 推動蘑菇！
    move(East)
}}

# 推動地塊
使用 `can_push(direction)` 可以檢查無人機下方的地塊能否推動，以及指定方向上是否有東西擋路。

`push(direction)` 會推動地塊，並回傳是否成功。

只有蘑菇地塊可以推動。地塊不能向上推動；如果有其他地塊擋路，推動也會失敗。地塊被推到空中後，會落到下方的第一個地塊上。

# 策略
<spoiler=提示>
別忘了，可以呼叫 `place(Grounds.Dirt)` 在無人機下方放置地塊。這有助於填平坑洞，讓你能將其他地塊推過去。
</spoiler>

---

[統計資料](docs/stats.md)      [地下感官](docs/unlocks/underground_senses.md)      [字典](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
