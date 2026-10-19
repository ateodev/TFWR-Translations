[<- 채광](docs/unlocks/mining.md) <right>[대나무 ->](docs/unlocks/bamboo.md)
<right>[화석화된 호박 ->](docs/unlocks/petrified_pumpkins.md)
<right>[진주암과 양토 ->](docs/unlocks/special_soils.md)
---
# 벼

지표와 `Grounds.Dirt` 층 아래에서 얇은 `Grounds.Clay` 층을 발견하셨을지도 모릅니다. 이 비옥하고 물기를 머금은 땅은 벼 모를 심기에 안성맞춤이죠.

풀이나 덤불과 마찬가지로 드론이 `Grounds.Clay` 블록 위에 있는 동안 `plant(Entities.Rice)`로 점토에 벼 모를 심고, `can_harvest()`로 벼가 다 자랐는지 확인한 뒤, 마지막으로 `harvest()`로 쌀을 얻을 수 있습니다.

벼를 심으면 땅이 벼가 자라기에 완벽한 환경인 `Grounds.Rice_Terrace`로 바뀝니다. 벼가 다 자라면 땅이 말라 `Grounds.Dry_Rice_Terrace`로 바뀌고 더 이상 벼를 심을 수 없습니다. 다행히 층이 몇 블록 두께이므로 `dig()`로 블록을 파내고 그 아래의 `Grounds.Clay`에 새 벼를 심을 수 있습니다. 층을 다 쓰면 언제든 `clear()`로 세계를 초기화하고 새 층까지 파 내려가면 됩니다.

점토를 찾을 때까지 굴착하는 데는 다음 코드가 유용합니다.

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 8,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(East)
#CODE
while get_ground_type() != Grounds.Clay:
    dig()
plant(Entities.Rice)
move(North)
do_a_flip()
}}

---

[통계](docs/stats.md)      [채광](docs/unlocks/mining.md)      [지하 감지](docs/unlocks/underground_senses.md)      [If문](docs/scripting/if.md)      [for 루프](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
