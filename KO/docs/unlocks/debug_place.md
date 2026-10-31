[<- 대나무](docs/unlocks/bamboo.md)
---
# 알록달록 블록
이미 알고 있을 수도 있지만 `place()`를 사용하면 드론에게 블록을 배치하도록 할 수 있습니다. 이 해금 항목으로 주변과 시각적으로 구분되는 세 가지 색상 블록 `Grounds.Block_Red`, `Grounds.Block_Green`, `Grounds.Block_Blue`를 추가할 수 있습니다.

색상 블록은 무언가를 표시하거나 예쁜 무늬를 만드는 데 사용할 수 있습니다.

새 블록을 배치하려면
{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 10},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "block", "n": 100}],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 5,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"],
    "starting_chunk": 2
}
#SETUP
move(East)
move(North)
#CODE
place(Grounds.Block_Green)
move(East)

place(Grounds.Block_Blue)
move(East)

place(Grounds.Block_Green)
move(North)

place(Grounds.Block_Blue)
move(North)

place(Grounds.Block_Green)
move(West)

place(Grounds.Block_Blue)
move(West)

place(Grounds.Block_Green)
move(South)

place(Grounds.Block_Blue)
move(East)

place(Grounds.Block_Red)
place(Grounds.Block_Red)

do_a_flip()
}}
---

[디버그](docs/scripting/debug.md)      [디버그 2](docs/unlocks/debug2.md)      [대나무](docs/unlocks/bamboo.md)

[place()](functions/place)
