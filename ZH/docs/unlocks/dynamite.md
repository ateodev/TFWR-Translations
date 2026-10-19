[<-蘑菇](docs/unlocks/mushroom.md) <right>[爆破钻头 ->](docs/unlocks/explosive_drill.md)
---
# 炸药

这种革命性的爆炸物是以前的采矿队留下的。（不）幸运的是，你的钻头正好能引爆炸药，把周围的地块炸开。

想安全地开采炸药，就要找到一层 `Grounds.Dynamite`，其正下方紧接着一层 `Grounds.Soot`。上层的炸药已经老化，其中一些地块可以安全挖掘。不过，还有一些炸药地块是实弹，挖到就会爆炸。

{{codeexample 
{
    "camera_position": {"x": -5, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 900, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}],
    "world_size": {"x": 11, "y": 11},
    "execution_speed": 8,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 5,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(5):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [East, South, West, West, North, North, East, East, South, West]
def dig_dynamite_neighbors():
    for dir in circle_directions:
        move(dir)
        while get_ground_type() != Grounds.Soot:
            dig()

while get_ground_type() == Grounds.Soot and measure() == 0:
    dig_dynamite_neighbors()
    move(circle_directions[random() * len(circle_directions)])
}}

你能找出并挖掘所有哑弹炸药地块，只留下实弹地块吗？炸药层消失时，每个周围只剩实弹地块或黑烟地块的实弹地块，都会给你产出额外的炸药。

好在下方的黑烟地块可以帮忙：它们能检测相邻的炸药地块中有多少是实弹炸药。不过，它们只告诉你总数，不会指出具体是哪些地块，因此你需要结合多个黑烟地块的读数自行推断。

在黑烟地块上调用 `measure()`，会返回上方炸药层中八个相邻地块中的炸药数量。结果介于 `0`（没有实弹炸药）和 `8`（每个相邻地块都有实弹炸药）之间。

炸药层中第一次挖到的一定是哑弹。每挖掉一个炸药地块都会产出少量炸药。炸药层被摧毁时，无论是成功挖光哑弹，还是不慎挖中实弹炸药，你都会获得额外的炸药，其数量等于完全显露的实弹炸药地块数的平方。

如果挖到实弹炸药，两个地层都会爆炸。在挖入 `Grounds.Dynamite` 后，可以使用 `get_ground_type()` 检查是否发生了爆炸。如果地块不是 `Grounds.Soot`，说明解谜失败。反之，如果挖掉最后一个哑弹地块，所有炸药地块都会消失，你会获得该谜题奖励的最大产量。黑烟层会保留，但 `measure()` 返回 `None`，表示谜题已成功解开。

`# 挖掘炸药地块并检查谜题状态
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # 挖到实弹炸药，未能解开谜题
        return False
    elif measure() == None:
        # 挖掉最后一个哑弹地块，成功解开谜题
        return True
    else:
        # 测量得到一个数字，谜题仍在进行中
        return None
`

炸药层中的实弹炸药数量会随着深度增加，找出它们也会越来越难。炸药总数会随农场规模增加，清理一层炸药可能获得的最大产量也随之增加。

收集到的炸药可以通过 `use_item(Items.Dynamite)` 使用，并立即在无人机下方爆炸。

升级炸药后，挖掘炸药地块和完全显露的实弹地块时的产量会提高，还会使炸药爆炸的能量提高 30%。

---

[统计数据](docs/stats.md)      [地下感官](docs/unlocks/underground_senses.md)      [字典](docs/scripting/dicts.md)      [集合](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
