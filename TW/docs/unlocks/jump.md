[<- 煤炭](docs/unlocks/coal.md)
---
# 跳躍

你的無人機解鎖了 `jump()` 指令。

這個指令讓你可以指定某些解鎖項並直接跳到它們那裡。它在偵錯或跳到你剛錯過的礦脈時特別有用。使用時傳入一個解鎖項作為引數，例如 `Unlocks.Iron`。

`jump()` 只對出現在地底的解鎖項有效，例如 `jump(Unlocks.Rice)` 或 `jump(Unlocks.Iron)`。

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
    "items": [],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 1,
    "digging_speed": 3,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms"],
    "starting_chunk": 0
}
#CODE
dig()
dig()
dig()
jump(Unlocks.Iron)
do_a_flip()
}}

跳躍不保證會把你直接帶到目標解鎖項，所以你可能還是得四處找一下，但可以保證目標就在附近。

每次執行程式只能使用一次 `jump()`。

---

[jump()](functions/jump)
