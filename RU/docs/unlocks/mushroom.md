[<- Кварц](docs/unlocks/quartz.md) <right>[Динамит ->](docs/unlocks/dynamite.md)
---
# Грибы

Под землей растут колонии разных видов грибов. Во время раскопок поищи слой `Grounds.Mushroom`. Затем вызови `measure()` на земле, чтобы узнать номер типа гриба от `0` до `5`.

Следующий код находит несколько грибов и выводит их тип:
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
    "items": [],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "digging_speed": 6,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron"]
}
#SETUP
jump(Unlocks.Mushrooms)
#CODE
# Обработать ряд грибов
for i in range(get_world_size()):
    # Прокопать до верхнего грибного блока
    while get_ground_type() != Grounds.Mushroom:
        dig()

    # Вывести номер типа гриба
    print(measure())

    move(East)
}}

## Как собирать грибы
Грибы одного типа селятся рядом, но стесняются расти друг на друге. Толкай грибной блок под дроном с помощью `push(direction)`.

Поставь друг на друга два грибных блока одного типа, и они автоматически соберутся, принеся тебе грибы.

Код ниже освобождает место, а затем толкает гриб, пока он не совпадет с грибом под ним:
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
    "items": [],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "digging_speed": 6,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 3,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron", "special_soils"]
}
#SETUP
jump(Unlocks.Mushrooms)
#CODE
while get_ground_type() != Grounds.Mushroom:
    dig()

depth = get_pos_z()
for i in range(2):
    # Освободить место, чтобы толкнуть грибной блок на восток
    move(East)
    while get_pos_z() > depth - 1:
        dig()
    # Вернуться, толкнуть и последовать за блоком
    move(West)
    push(East) # Толкнуть гриб!
    move(East)
}}

# Как толкать блоки
С помощью `can_push(direction)` можно проверить, удастся ли толкнуть блок под дроном и не мешает ли что-нибудь в заданном направлении.

`push(direction)` толкает блок и сообщает, удалось ли это сделать.

Толкать можно только грибные блоки. Блоки нельзя толкать вверх, а другой блок на пути помешает толчку. Вытолкнутые с опоры блоки падают на ближайший блок под ними.

# Стратегия
<spoiler=подсказка>
Не забывай, что команда `place(Grounds.Dirt)` устанавливает блоки под дроном. Так можно заполнить ямы, чтобы проталкивать над ними блоки.
</spoiler>

---

[Статистика](docs/stats.md)      [Подземные датчики](docs/unlocks/underground_senses.md)      [Словари](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
