[<-水稻](docs/unlocks/rice.md) <right>[彩色地块->](docs/unlocks/debug_place.md)
<right>[金字塔->](docs/unlocks/pyramid.md)
---
# 竹子
竹子是一种向上生长的植物。无人机需要定期摘掉它的棕色果实，它才能继续生长。新解锁的 `hover` 命令可以帮我们做到这一点。

竹子需要种在耕过的土壤（`Grounds.Soil`）上，种植竹子需要消耗水稻。

下面的代码会种下竹子，并等待它长到结出第一个果实。
{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
move(East) # 移开，让竹子生长
}}

## 果实
竹子每秒长高 1 个地块。

竹子每长几个地块就会结出果实。这时竹子会停止生长，你需要让无人机飞入竹子，摘掉果实。

要摘果实，首先需要用 `hover` 升到正确的高度。然后用 `move` 飞入果实将其摘掉，再用 `move` 移开，让竹子继续生长。

你可以对竹子使用 `measure()`，查看下一个果实会出现在什么高度。`measure()` 从 `0` 开始计数，所以 `hover(measure())` 会把无人机带到果实将要出现的高度。

{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
hover(measure()) # 悬停到果实旁边的高度

move(East) # 移开，等待竹子生长
for i in range(3):
    do_a_flip()

move(West) # 摘掉果实
move(East) # 再次移开
}}

## 悬停
`hover` 命令接受一个参数，即悬停的高度，取值为 `0` 到 `18` 之间的数字。无人机的默认悬停高度为 `1`。`hover` 无法向下移入实心实体，所以如果无人机已经位于竹子上方，执行 `hover(0)` 并不能让它进入竹子。

如果无人机成功悬停到指定高度，`hover` 会返回 `True`，否则返回 `False`。

此外，还有 `get_hover` 命令，它会返回无人机当前的悬停高度。

如果在悬停时使用 `dig`、`harvest` 或 `plant`，无人机会回到默认悬停高度（`1`）。

最后，`get_pos_z()` 不受悬停影响。它始终返回无人机下方地块的 z 坐标。

## 收获竹子
虽然也可以使用 `harvest()`，但收获竹林的推荐方法是让无人机在悬停高度 `0`（`hover(0)`）飞入竹子。这样可以一次收获整株竹子。

如果想在收获竹子的同时不摧毁它，可以在任意高度用 `move` 飞入竹子，例如 `hover(3)`。这样会收获从该高度往上的所有竹节，但竹子会继续存活。以这种方式部分收获的竹子会重新长出果实，所以你需要再次摘掉它们。

无论哪种方式，产量都等于被摧毁竹节数量的平方，所以竹子长得越高，产量就越高。

---

[统计数据](docs/stats.md)      [For 循环](docs/scripting/for.md)      [变量](docs/scripting/variables.md)      [If 语句](docs/scripting/if.md)      [函数](docs/scripting/functions.md)      [水稻](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
