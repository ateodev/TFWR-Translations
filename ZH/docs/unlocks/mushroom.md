[<-石英](docs/unlocks/quartz.md) <right>[炸药->](docs/unlocks/dynamite.md)
---
# 蘑菇
地下有许多种蘑菇成群生长。挖掘时寻找一层 `Grounds.Mushroom`。随后，可以对地块使用 `measure()`，获取蘑菇类型的编号，范围为 `0` 到 `5`。

下面的代码会找到一些蘑菇，并打印它们的类型：
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
# 处理一排蘑菇
for i in range(get_world_size()):
    # 向下挖到最上面的蘑菇地块
    while get_ground_type() != Grounds.Mushroom:
        dig()

    # 打印蘑菇类型编号
    print(measure())

    move(East)
}}

## 如何收集蘑菇
同类蘑菇喜欢长在一起，却又很害羞，不会叠着长。用 `push(direction)` 推动无人机下方的蘑菇地块。

把两个相同类型的蘑菇地块叠在一起，它们就会被自动收获，产出蘑菇。

下面的代码会先腾出空间，然后推动一个蘑菇，直到它与下方的蘑菇类型相同：
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
    # 腾出空间，以便向东推动蘑菇地块
    move(East)
    while get_pos_z() > depth - 1:
        dig()
    # 退回去推动地块，然后跟上被推动的地块
    move(West)
    push(East) # 推动蘑菇！
    move(East)
}}

# 推动地块
使用 `can_push(direction)` 可以检查无人机下方的地块能否推动，以及指定方向上是否有东西挡路。

`push(direction)` 会推动地块，并返回是否成功。

只有蘑菇地块可以推动。地块不能向上推动；如果有其他地块挡路，推动也会失败。地块被推到空中后，会落到下方的第一个地块上。

# 策略
<spoiler=提示>
别忘了，可以调用 `place(Grounds.Dirt)` 在无人机下方放置地块。这有助于填平坑洞，让你能将其他地块推过去。
</spoiler>

---

[统计数据](docs/stats.md)      [地下感官](docs/unlocks/underground_senses.md)      [字典](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
