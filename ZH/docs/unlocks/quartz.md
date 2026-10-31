[<-铁矿](docs/unlocks/iron.md) <right>[蘑菇->](docs/unlocks/mushroom.md)
---
# 石英
从 `Grounds.Rock` 中的铁矿脉继续往下，你会在岩石层下部及其下方坚硬的 `Grounds.Dirt` 中找到石英（可以用[地下感官](docs/unlocks/underground_senses.md)解锁项中的 `get_hardness()` 检查硬度）。

下面的代码片段会挖穿泥土，进入岩石层。接着它会一边挖掘一边不断探查石英，直到距离小于 2。最后，它会打印最终得到的探查距离。
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
# 向下挖到岩石层
while get_ground_type() != Grounds.Rock:
    dig()

# 继续挖掘，直到靠近石英矿脉
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# 打印到矿脉的最终距离
print(prospect_quartz())
}}

## 矿脉结构
石英矿脉呈针状，形成垂直的柱状结构，单凭碰运气很难挖掘到。

## 探查石英
好在我们可以把铁矿加工成类似探矿杖的东西，更容易找到石英矿脉。对应的命令是 `prospect_quartz()`。

`prospect_quartz()` 的工作方式与 `prospect_iron()` 不同。它不会返回让无人机朝最近铁矿石移动的方向，而是返回最近的石英地块与无人机之间精确的三维距离（欧几里得距离）。

执行 `prospect_quartz()` 命令需消耗 1 份铁矿，最好省着用。

如果附近没有石英，或者铁矿不足以执行探查，`prospect_quartz()` 就会返回 `None`。

## 策略
<spoiler=显示提示>你可以反复探查并移动，观察距离如何变化。在平坦的地面上，尽量让距离变小，就有可能来到石英矿脉的上方。你可以采用类似二分查找的策略，尽量减少 `prospect_quartz()` 的调用次数以及它们消耗的铁矿。

更复杂的策略可以用二维几何求出两个或多个圆的交点。你也可以挑战高难度，用完整的三边测量求三个球体的交点，找出矿脉精确的三维位置。

注意，求平方根可以使用幂运算符，例如要求 16 的平方根，可以用 `16**0.5`。游戏没有提供三角函数或向量等内置数学函数，你需要自己实现。

另外，附近可能有多条矿脉，所以在相近位置多次测量时，结果未必指向同一条矿脉。</spoiler>

---

[统计数据](docs/stats.md)      [采矿](docs/unlocks/mining.md)      [地下感官](docs/unlocks/underground_senses.md)      [变量](docs/scripting/variables.md)      [运算符](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
