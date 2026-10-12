[<- Видобуток](docs/unlocks/mining.md)
---
# Підземні сенсори

Додамо кілька сенсорів, щоб ваш дрон міг орієнтуватися під землею.

Тепер за допомогою `get_pos_z()` можна дізнатися висоту дрона (починається з 0 і стає від'ємною, коли дрон спускається).

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#CODE
move(North)
move(North)
move(East)
dig()
dig()
dig()
print(get_pos_z())
}}

`get_ground_type()` повертає тип ґрунту під дроном. Можна передати аргумент напрямку, наприклад `get_ground_type(North)`, щоб дізнатися тип ґрунту сусідньої клітинки.

Ось як перевірити, чи блок під дроном — земля:

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
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#CODE
dig()
if get_ground_type() == Grounds.Dirt:
    do_a_flip()
}}


`get_hardness()` повертає твердість клітинки ґрунту під дроном. Можна передати аргумент напрямку, наприклад `get_hardness(North)`. Що вища твердість клітинки, то довше її копати.

`get_stability()` повертає стійкість клітинки ґрунту під дроном. Можна передати аргумент напрямку, наприклад `get_stability(North)`. Стійкість 1 означає, що блок витримує перепад висоти 1, перш ніж обвалиться.

Зауважте, що чотири блоки безпосередньо поруч із дроном зникають незалежно від їхньої стійкості, коли дрон копає вниз, якщо тільки блок не має особливої функції. Наприклад, глина, залізо та кварц за цим правилом не зникають. Проте вони все одно можуть обвалитися через недостатню стійкість блоку.
---

[Видобуток](docs/unlocks/mining.md)      [Сенсори](docs/unlocks/senses.md)

[get_pos_z()](functions/get_pos_z)      [get_ground_type()](functions/get_ground_type)      [get_hardness()](functions/get_hardness)      [get_stability()](functions/get_stability)
