[<- Видобуток](docs/unlocks/mining.md) <right>[Бамбук ->](docs/unlocks/bamboo.md)
<right>[Скам'янілі гарбузи ->](docs/unlocks/petrified_pumpkins.md)
<right>[Перліт і суглинок ->](docs/unlocks/special_soils.md)
---
# Рис

Під поверхнею ви помітили тонкий пласт глини. Виявляється, цей родючий ґрунт ідеально підходить для висаджування розсади рису.

Рис висушує глину, на якій його посаджено. Кожен блок глини можна використати лише раз. На щастя, пласт має кілька блоків завтовшки. І, звісно, завжди можна просто виконати `clear()`, щоб повернути пласт глини.

Цей код допоможе копати вниз, доки не знайдеться глина.

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

[Статистика](docs/stats.md)      [Видобуток](docs/unlocks/mining.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [Цикл for](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
