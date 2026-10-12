[<- 煤炭](docs/unlocks/coal.md) <right>[石英 ->](docs/unlocks/quartz.md)
<right>[鐵礦探勘 ->](docs/unlocks/prospecting.md)
<right>[藏寶圖 ->](docs/unlocks/treasure_map.md)
---
# 鐵

你在黏土下方的石層中發現了鐵礦脈。

鐵礦脈一開始很小，需要一點運氣才能找到。隨著這個解鎖項的等級提高，礦脈的最大規模也會增加。如果想要更穩定地找到鐵，也可以看看礦石探勘解鎖項。

鐵礦脈一定是連續的，不會斜向跳躍。如果你找到一塊鐵，記得在它下方或旁邊尋找更多，確保收集整條礦脈。

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

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [鐵礦探勘](docs/unlocks/prospecting.md)      [地下感測](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
