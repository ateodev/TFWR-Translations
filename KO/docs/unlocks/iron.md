[<- 석탄](docs/unlocks/coal.md) <right>[석영 ->](docs/unlocks/quartz.md)
<right>[철 탐사 ->](docs/unlocks/prospecting.md)
<right>[보물지도 ->](docs/unlocks/treasure_map.md)
---
# 철

`Grounds.Dirt`에서 석탄을 찾았다면 `Grounds.Clay` 층을 지나 `Grounds.Rock`까지 더 깊이 파 내려가 철을 찾을 수 있습니다.

석탄 광맥과 달리 철 광맥은 수직으로도 뻗어 있습니다. 하지만 한 광맥의 철 블록은 항상 서로 바로 붙어 있으며, 대각선으로만 이어지는 일은 없습니다.

하지만 철 광맥은 처음에는 작아서 찾으려면 약간의 운이 필요합니다. 철을 더 해금하면 광맥의 최대 크기가 커지고 우연히 찾기도 조금 쉬워집니다. 하지만 안정적으로 찾으려면 [철 탐사](docs/unlocks/prospecting.md)를 해금하는 것이 좋습니다.

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

[통계](docs/stats.md)      [채광](docs/unlocks/mining.md)      [철 탐사](docs/unlocks/prospecting.md)      [지하 감지](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
