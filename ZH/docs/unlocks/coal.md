[<-采矿](docs/unlocks/mining.md) <right>[铁矿->](docs/unlocks/iron.md)
<right>[跳转->](docs/unlocks/jump.md)
---
# 煤炭

地下藏着各种矿石，等着你去发现和挖掘。如果你挖穿地表进入 `Grounds.Dirt`，最先找到的矿石就是煤炭。

煤炭矿脉形成厚度为 1 个地块的水平煤层，你得在挖掘泥土时碰运气找到它们。煤层中的煤炭地块大多直接相邻，但有些也可能只以对角线相连。

开采煤炭无需任何特殊操作，只要在无人机正好位于 `Grounds.Coal` 地块上方时执行 `dig()` 即可。使用 `get_ground_type()` 检查无人机下方是什么，使用 `get_ground_type(direction)` 检查四个相邻地块。

注意，只有你直接挖掘的煤炭地块才会给你煤炭，无人机周围塌方的地块不会。规划如何开采煤炭时请记住这一点，尽量多挖出煤炭地块，少因塌方损失。

煤矿会随农场规模按比例扩大，因此可以考虑继续解锁[扩张](unlocks/expand)，以增加可开采的煤炭数量。

下面的程序很适合用来寻找煤炭。它会向下挖掘寻找煤炭层，然后往东西两侧挖掘，试着找到更多煤炭。

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
do_a_flip()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

一个简单的策略是把找到煤炭地块的那个深度的所有地块都挖掉，这对较小的农场尤其适用。想提高效率，可以用 `get_ground_type(direction)` 记录见过煤炭地块的位置，避免浪费时间在泥土地块上移动。要特别注意别漏掉对角线相连的地块，如果只在煤炭地块上移动，就会错过它们。

---

[统计数据](docs/stats.md)      [采矿](docs/unlocks/mining.md)      [地下感官](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
