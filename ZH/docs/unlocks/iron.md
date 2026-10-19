[<-煤炭](docs/unlocks/coal.md) <right>[石英->](docs/unlocks/quartz.md)
<right>[铁矿探查->](docs/unlocks/prospecting.md)
<right>[藏宝图->](docs/unlocks/treasure_map.md)
---
# 铁矿

在 `Grounds.Dirt` 中找到煤炭后，你可以继续往下挖，穿过 `Grounds.Clay` 层进入 `Grounds.Rock`，寻找铁矿。

与煤炭矿脉不同，铁矿脉也会纵向延伸。但同一条矿脉中的铁矿地块总是直接相邻，从不只以对角线相连。

不过铁矿脉一开始很小，要找到还需要一点运气。继续解锁铁矿会增大矿脉的最大规模，也会让它们更容易碰巧找到。但想稳定地找到它们，你应该解锁[铁矿探查](docs/unlocks/prospecting.md)。

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
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#SETUP
jump(Unlocks.Iron)
#CODE
for i in range(4):
    dig()
do_a_flip()
}}

---

[统计数据](docs/stats.md)      [采矿](docs/unlocks/mining.md)      [铁矿探查](docs/unlocks/prospecting.md)      [地下感官](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
