[<- 석탄](docs/unlocks/coal.md)
---
# 점프

드론이 `jump()` 명령을 해금했습니다. `Unlocks.Iron`처럼 해금 항목을 인수로 전달해 사용합니다.

이 명령을 사용하면 땅속에 숨겨진 특정 해금 항목을 지정해 그곳까지 즉시 내려갈 수 있습니다. 디버깅하거나 최근에 놓친 광맥으로 건너뛸 때 특히 유용합니다.

점프한 뒤에는 목표 해금 항목이 맨 위 블록 표면에서 3블록 이내에 있을 것입니다. `jump()`는 프로그램 실행당 한 번만 사용할 수 있으며, 그 이상 점프를 시도하면 오류가 발생합니다.

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
    "items": [{"item": "hay", "n": 10}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms"],
    "starting_chunk": 0
}
#CODE
jump(Unlocks.Rice)

for i in range(get_world_size()):
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## 호환되는 해금 항목
`jump()`는 다음 채광 해금 항목에만 사용할 수 있습니다.
- Coal
- Iron
- Quartz
- Rice
- Petrified_Pumpkins
- Special_Soils
- Pyramid
- Treasure_Map
- Mushrooms
- Dynamite

---

[jump()](functions/jump)
