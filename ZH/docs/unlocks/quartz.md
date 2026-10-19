[<-铁矿](docs/unlocks/iron.md) <right>[蘑菇->](docs/unlocks/mushroom.md)
---
# 石英

从 `Grounds.Rock` 中的铁矿脉继续往下，你会在岩石层下部及其下方坚硬的 `Grounds.Dirt` 中找到石英（可以用[地下感官](docs/unlocks/underground_senses.md)解锁项中的 `get_hardness()` 检查硬度）。

石英矿脉呈针状，形成垂直的柱状结构，单凭碰运气很难挖掘到。

好在我们可以把铁矿加工成类似探矿杖的东西，更容易找到石英矿脉。对应的命令是 `prospect_quartz()`。

`prospect_quartz()` 的工作方式与 `prospect_iron()` 不同。它不会返回最近石英矿石的方向，而是返回到最近石英的欧几里得距离（三维距离）。执行 `prospect_quartz()` 命令需消耗 1 份铁矿，最好省着用。

如果附近没有石英，或者铁矿不足以执行探查，`prospect_quartz()` 就会返回 `None`。

下面的代码片段会让无人机挖穿泥土，深入岩石层。运气好的话，附近就有一条石英矿脉，无人机会打印出到它的距离。

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

你可以反复探查并移动，观察距离如何变化，从而判断自己是在靠近还是远离矿脉。可以用二维几何求出两个或多个圆的交点，找到矿脉的水平位置后向下挖。也可以用完整的三边测量求三个球体的交点，找出精确的三维位置。

注意，游戏没有提供平方根、三角函数或向量等基础数学函数，你需要自己实现。另外，附近可能有多条矿脉，所以在相近位置多次测量时，结果未必指向同一条矿脉，可能会把你带偏。

---

[统计数据](docs/stats.md)      [采矿](docs/unlocks/mining.md)      [地下感官](docs/unlocks/underground_senses.md)      [变量](docs/scripting/variables.md)      [运算符](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
