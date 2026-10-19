[<-煤炭](docs/unlocks/coal.md) <right>[石英->](docs/unlocks/quartz.md)
<right>[鐵礦探查->](docs/unlocks/prospecting.md)
<right>[藏寶圖->](docs/unlocks/treasure_map.md)
---
# 鐵礦

在 `Grounds.Dirt` 中找到煤炭後，你可以繼續往下挖，穿過 `Grounds.Clay` 層進入 `Grounds.Rock`，尋找鐵礦。

與煤炭礦脈不同，鐵礦脈也會縱向延伸。但同一條礦脈中的鐵礦地塊總是直接相鄰，從不只以對角線相連。

不過鐵礦脈一開始很小，要找到還需要一點運氣。繼續解鎖鐵礦會增大礦脈的最大規模，也會讓它們更容易碰巧找到。但想穩定地找到它們，你應該解鎖[鐵礦探查](docs/unlocks/prospecting.md)。

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

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [鐵礦探查](docs/unlocks/prospecting.md)      [地下感官](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
