[<- Видобуток](docs/unlocks/mining.md) <right>[Бамбук ->](docs/unlocks/bamboo.md)
<right>[Скам'янілі гарбузи ->](docs/unlocks/petrified_pumpkins.md)
<right>[Перліт і суглинок ->](docs/unlocks/special_soils.md)
---
# Рис

Під поверхнею та шаром `Grounds.Dirt` ви могли помітити тонкий пласт `Grounds.Clay`. Виявляється, цей родючий і просочений водою ґрунт ідеально підходить для висаджування розсади рису.

Як і з травою чи кущами, поки дрон перебуває над блоком `Grounds.Clay`, можна за допомогою `plant(Entities.Rice)` висадити розсаду рису в глину, потім за допомогою `can_harvest()` перевірити, чи рис повністю виріс, і нарешті за допомогою `harvest()` зібрати рис.

Щойно ви посадите рис, ґрунт перетвориться на `Grounds.Rice_Terrace`, щоб забезпечити рису ідеальні умови для дозрівання. Коли рис повністю виросте, ґрунт висохне, перетвориться на `Grounds.Dry_Rice_Terrace` і більше не придатний для садіння рису. На щастя, пласт має кілька блоків завтовшки, тож можна прибрати блок за допомогою `dig()` і посадити новий рис на `Grounds.Clay` нижче. А якщо пласт закінчиться, завжди можна виконати `clear()` для світу й докопатися до свіжого пласта.

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
