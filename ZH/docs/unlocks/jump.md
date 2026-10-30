[<-煤炭](docs/unlocks/coal.md)
---
# 跳转

无人机已解锁 `jump()` 命令。使用时，传入一个解锁项作为参数，例如 `Unlocks.Iron`。

此命令可以指定某些藏在地下的解锁项，让无人机瞬间向下跳转到它们那里。调试程序，或者直接跳到刚刚错过的矿脉时，这特别有用。

跳转后，目标解锁项应位于最上层地块表面以下 3 个地块以内。每次执行程序只能使用一次 `jump()`，再次尝试跳转会产生错误。

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

## 兼容的解锁项
`jump()` 只适用于以下采矿解锁项：
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
