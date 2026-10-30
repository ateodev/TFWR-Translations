[<- Грибы](docs/unlocks/mushroom.md) <right>[Взрывной бур ->](docs/unlocks/explosive_drill.md)
---
# Динамит

Революционная взрывчатка, оставленная предыдущими шахтерскими экспедициями. К счастью (или к сожалению), твой бур идеально подходит для подрыва динамита, уничтожающего все блоки вокруг.

Чтобы безопасно добывать динамит, найди слой `Grounds.Dynamite`, под которым сразу идет слой `Grounds.Soot`. Верхний динамитный слой состарился, поэтому некоторые его блоки можно безопасно копать. Но некоторые динамитные блоки все еще активны и взорвутся, если в них копать.

Собранный динамит можно применить командой `use_item(Items.Dynamite)`: он взорвется прямо под дроном.

Этот пример раскапывает динамит в начальной точке и вокруг нее, выводя показания блоков сажи под ними:
{{codeexample 
{
    "camera_position": {"x": -3, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 800, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 7, "y": 7},
    "execution_speed": 2,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 6,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(3):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [
    East, South, West, West, 
    North, North, East, East
]
for dir in circle_directions:
    move(dir)
    dig()
    print(measure())
}}

## Динамитный сапер
Сможешь ли ты найти и раскопать все динамитные блоки-пустышки, оставив только активные заряды? Когда динамитный слой исчезнет, каждый активный блок, окруженный только другими активными блоками или сажей, даст дополнительный динамит.

К счастью, помогут расположенные ниже блоки сажи: они способны опознавать соседние динамитные блоки с активными зарядами. Какие именно блоки активны, они не сообщат — только общее число, поэтому придется сопоставить показания нескольких блоков сажи.

Вызов `measure()` на блоке сажи возвращает количество зарядов в восьми соседних клетках динамитного слоя выше. Значение может быть от `0` (активных зарядов нет) до `8` (активный заряд есть у каждого соседа).

Первый раскопанный блок динамитного слоя всегда оказывается пустышкой. Каждый добытый блок дает немного динамита. Когда слой уничтожается — после успешной добычи всех пустышек или случайного попадания в активный заряд, — ты также получишь количество динамита, равное квадрату числа полностью открытых активных блоков.

## Строение слоев
Чем больше глубина, тем больше активных зарядов окажется в динамитном слое, а также выше сложность их поиска. Общее число зарядов растет вместе с размером фермы, а с ним и максимально возможная награда за расчистку динамитного слоя.

Улучшай динамит, чтобы получать большее его количество при раскопках динамитных блоков и полном открытии активных зарядов. Каждое улучшение также повышает энергию взрыва динамита на 30%.

## Как распознать успех и провал
Если прокопать активный динамит, оба слоя взорвутся. Проверить это можно, использовав `get_ground_type()` после раскопок `Grounds.Dynamite`. Если земля не `Grounds.Soot`, решить головоломку не удалось. Если же раскопать последний неактивный динамитный блок, все динамитные блоки исчезнут, а ты получишь максимальный урожай за головоломку. Слой сажи останется, но `measure()` вернет `None`, показывая, что головоломка успешно решена.

`# Раскопать динамитный блок и проверить состояние головоломки
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # Раскопан активный динамит, головоломка провалена
        return False
    elif measure() == None:
        # Раскопан последний блок-пустышка, головоломка решена
        return True
    else:
        # При измерении получено число, головоломка не завершена
        return None
`

## Стратегия
<spoiler=подсказка>
Код ниже раскапывает динамитный слой и ищет блоки сажи, измерение которых дает `0`. Для каждого найденного такого блока он раскапывает все окружающие его динамитные блоки:
{{codeexample 
{
    "camera_position": {"x": -5, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 800, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 7, "y": 7},
    "execution_speed": 4,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 6,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(3):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [
    East, South, West, West, North,
    North, East, East, South, West
]
for dir in circle_directions:
    if get_ground_type() == Grounds.Soot and measure() == 0:
        for dir2 in circle_directions:
            move(dir2)
            while get_ground_type() != Grounds.Soot:
                dig()
    move(dir)
}}
</spoiler>

---

[Статистика](docs/stats.md)      [Подземные датчики](docs/unlocks/underground_senses.md)      [Словари](docs/scripting/dicts.md)      [Множества](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
