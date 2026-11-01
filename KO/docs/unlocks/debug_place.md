[<- 대나무](docs/unlocks/bamboo.md)
---
# 알록달록 블록
이미 알고 있을 수도 있지만, `place()`를 사용하면 드론에게 블록을 배치하도록 할 수 있습니다. 이 해금 항목은 주변과 눈에 띄게 구별되는 세 색깔 블록인 `Grounds.Block_Red`, `Grounds.Block_Green`, `Grounds.Block_Blue`를 추가합니다.

색깔 블록으로 위치를 표시하거나 예쁜 무늬를 만들 수 있습니다.

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

## 배치 높이 제한
블록을 배치할 수 있는 높이에는 제한이 있으며, 완전히 축소했을 때 블록이 검게 흐려지기 시작하는 지점 정도까지입니다. 이 제한은 드러난 블록들의 평균 깊이에 따라 달라지므로, 농장을 고르게 쌓아 올리면 이 제한을 피할 수 있습니다.

---

[디버그](docs/scripting/debug.md)      [디버그 2](docs/unlocks/debug2.md)      [대나무](docs/unlocks/bamboo.md)

[place()](functions/place)
