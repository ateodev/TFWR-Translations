[<- Вугілля](docs/unlocks/coal.md)
---
# Стрибок

Ваш дрон розблокував команду `jump()`. Використовуйте її, передавши розблокування як аргумент, наприклад `Unlocks.Iron`.

Ця команда дозволяє вибрати певні розблокування, сховані під землею, і миттєво перестрибнути вниз прямо до них. Вона особливо корисна для налагодження або щоб перестрибнути до рудної жили, яку ви нещодавно пропустили.

Після стрибка цільове розблокування має бути не далі ніж за 3 блоки від верхньої поверхні блоків. `jump()` можна використати лише один раз за виконання програми, подальші спроби стрибнути спричинять помилку.

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

## Сумісні розблокування
`jump()` працює лише з такими розблокуваннями видобутку:
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
