[<- Железо](docs/unlocks/iron.md)
---
# Карта сокровищ

Легенды рассказывают о неуловимом кладе, спрятанном давно погибшим забывчивым пиратом — или что-то в этом роде. Что, если он отметил путь к кладу на карте, а затем потерял ее? Вдруг карта выпала, когда пирата загнала в угол река лавы, и сохранилась под слоем базальта? Возможно, поиски стоит начать с измерения базальта.

<spoiler=Расскажи подробнее>
Ищи слой `Grounds.Basalt`. Попробуй измерить базальт и посмотри, что он сообщит. Подсказка может привести к карте сокровищ, а изучение карты наверняка откроет путь к самому кладу — но сможешь ли ты расшифровать ее указания?
</spoiler>

<spoiler=Просто скажи, как это сделать>
Ладно, вот что нужно сделать: найди слой `Grounds.Basalt` и блок `Grounds.Treasure_Map` прямо под ним. Вызови `measure()` на базальте, чтобы получить координаты `(x, y)` находящегося под ним блока карты.

Вызови `measure()` на блоке карты, чтобы получить путь к сокровищу в виде строки с буквами направлений. N, E, S и W означают соответственно `North`, `East`, `South` и `West`, а D — «вниз» или «копать». Эти буквы описывают путь из блоков `Grounds.Treasure_Path`, ведущий к кладу.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 6},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "hay", "n": 100}, {"item": "iron", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "digging_speed": 10,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 3,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron"]
}

#SETUP
jump(Unlocks.Treasure_Map)
#CODE
while get_ground_type() != Grounds.Basalt:
    dig()

do_a_flip()
map_pos = measure()

while get_pos_x() < map_pos[0]:
    move(East)
while get_pos_y() < map_pos[1]:
    move(North)

while get_ground_type() != Grounds.Treasure_Map:
    dig()

do_a_flip()
instructions = measure()
dig()
}}

С помощью цикла `for` можно обработать строку буква за буквой:
```
path = measure()
for letter in path:
    do_something(letter)
```

Искать клад должен дрон, раскопавший блок карты. Ему нужно все время оставаться над блоками `Grounds.Treasure_Path`. Если он собьется с пути, путь разрушится и клад будет потерян.

В конце пути находится блок `Grounds.Treasure_Goal`. Если дрон не сходил с пути, над этим блоком появится `Entities.Underground_Treasure`. Дрон может забрать сундук командой `harvest()` и получить золото.

Количество золота пропорционально длине пути к сокровищу. Улучшение технологии «Карта сокровищ» увеличивает глубину пути, а улучшение «Расширения» позволяет ему больше сдвигаться в стороны. Оба улучшения увеличивают длину пути и количество найденного золота.
</spoiler>

---

[Статистика](docs/stats.md)      [Цикл For](docs/scripting/for.md)      [Кортежи](docs/scripting/tuples.md)      [Подземные датчики](docs/unlocks/underground_senses.md)

[harvest()](functions/harvest)      [move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)
