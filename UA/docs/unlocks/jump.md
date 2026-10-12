[<- Вугілля](docs/unlocks/coal.md)
---
# Стрибок

Ваш дрон розблокував команду `jump()`.

Ця команда дозволяє вибрати певне розблокування і перестрибнути прямо до нього. Вона особливо корисна для налагодження або щоб перестрибнути до рудної жили, яку ви нещодавно пропустили. Використовуйте її, передавши розблокування як аргумент, наприклад `Unlocks.Iron`.

`jump()` працює лише для розблокувань, що трапляються під землею, наприклад `jump(Unlocks.Rice)` або `jump(Unlocks.Iron)`.

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

Стрибок не гарантує, що ви опинитеся прямо біля цілі, тож, можливо, доведеться трохи пошукати, але гарантовано, що ціль десь поруч.

`jump()` можна використати лише один раз за виконання програми.

---

[jump()](functions/jump)
