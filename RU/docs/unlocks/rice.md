[<- Добыча](docs/unlocks/mining.md) <right>[Бамбук ->](docs/unlocks/bamboo.md)
<right>[Окаменевшие тыквы ->](docs/unlocks/petrified_pumpkins.md)
<right>[Перлит и суглинок ->](docs/unlocks/special_soils.md)
---
# Рис

Под поверхностью и слоем `Grounds.Dirt` ты мог заметить тонкий пласт `Grounds.Clay`. Оказывается, эта плодородная и пропитанная водой земля идеально подходит для посадки риса.

Как и с травой или кустами, пока дрон находится над блоком `Grounds.Clay`, можно с помощью `plant(Entities.Rice)` посадить рассаду риса в глину, затем с помощью `can_harvest()` проверить, вырос ли рис полностью, и наконец с помощью `harvest()` собрать рис.

Как только ты сажаешь рис, земля превращается в `Grounds.Rice_Terrace`, чтобы рису было идеально созревать. Когда рис полностью вырастет, земля высохнет, превратится в `Grounds.Dry_Rice_Terrace` и больше не подойдет для посадки риса. К счастью, пласт толщиной в несколько блоков, так что можно убрать блок с помощью `dig()` и посадить новый рис на `Grounds.Clay` ниже. А если пласт закончится, всегда можно вызвать `clear()` для мира и докопаться до нового пласта.

Следующий код может пригодиться, чтобы копать вниз, пока не найдется глина.

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

[Статистика](docs/stats.md)      [Добыча](docs/unlocks/mining.md)      [Подземные датчики](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [Цикл For](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
