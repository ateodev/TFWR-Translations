[<- Рис](docs/unlocks/rice.md) <right>[Кольорові блоки ->](docs/unlocks/debug_place.md)
<right>[Піраміди ->](docs/unlocks/pyramid.md)
---
# Бамбук

Бамбук — рослина, що може вирости заввишки до 6 блоків. Він не росте, поки над ним є дрон, тому після `plant(Entities.Bamboo)` обов'язково виконайте `move`. Садіння бамбука коштує рису.

Бамбук цвіте, коли досягає певної висоти, вибраної випадково. Використайте `measure()`, щоб дізнатися, на якій висоті він зацвіте. `measure()` рахує з 0, тож якщо бамбук цвіте на другому блоці, `measure()` повертає 1:

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 1000, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "rice", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
print(measure())
move(East)
}}

Максимальний урожай бамбука ви отримаєте, якщо викликати `harvest()`, коли дрон перебуває прямо над квіткою. За кожен блок різниці врожай ділиться на вісім.
Наприклад, якщо квітка на висоті 3, а ви збираєте врожай на два блоки вище, урожай буде поділено на 64.

Щоб зібрати квітки, які ростуть вище, залетіть у бамбук, коли дрон на потрібній висоті. У цьому допоможе щойно розблокована команда `place()`.

Використайте `place(Grounds.Dirt)`, щоб скласти блоки поруч із бамбуком і піднятися. Потім за допомогою `move()` залетіть у бамбук збоку. Під час виклику `harvest()` дрон має бути прямо над квіткою.

`place(Grounds.Dirt)` коштує вам 1 блок! Можна також розміщувати інші ґрунти, наприклад `Grounds.Rock`, але не особливі блоки на кшталт `Grounds.Clay`.

Бамбук росте рівно на 1 блок за секунду.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 1000, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "block", "n": 100}, {"item": "rice", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
print(measure())
move(East)
place(Grounds.Dirt)
do_a_flip() # трохи почекаємо
do_a_flip()
move(West)
harvest()
}}

---

[Статистика](docs/stats.md)      [Цикл for](docs/scripting/for.md)      [Змінні](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Функції](docs/scripting/functions.md)      [Рис](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [place()](functions/place)      [measure()](functions/measure)
