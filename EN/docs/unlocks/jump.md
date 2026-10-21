[<- Coal](docs/unlocks/coal.md)
---
# Jumping

Your drone has unlocked the `jump()` command.

This command allows you to target certain unlocks and jump forward to them. It is especially useful for debugging or jumping forward to an ore vein that you have recently missed. You use it by passing it an unlock as an argument, such as `Unlocks.Iron`.

After jumping, the target unlock should be within 3 blocks of the top block surface. `jump()` can only be used once per program execution, further jump attempts will produce an error.

`jump()` only works with the following mining unlocks:
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

---

[jump()](functions/jump)
