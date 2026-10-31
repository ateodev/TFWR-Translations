[<- Рис](docs/unlocks/rice.md) <right>[Кольорові блоки ->](docs/unlocks/debug_place.md)
<right>[Піраміди ->](docs/unlocks/pyramid.md)
---
# Бамбук
Бамбук росте вгору. Вашому дрону доведеться регулярно зривати його коричневі плоди, щоб він міг рости далі. Для цього знадобиться щойно розблокована команда `hover`.

Бамбук потрібно садити на зораний ґрунт (`Grounds.Soil`), а садіння коштує рису.

Наведений нижче код садить бамбук і чекає, поки він виросте до першого плоду.
{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
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
move(East) # відлетіти, щоб бамбук міг рости
}}

## Плоди
Бамбук росте рівно на 1 блок за секунду.

Через кожні кілька блоків бамбук утворює плоди. Коли це стається, бамбук перестає рости, і вам доведеться залетіти в нього дроном, щоб знищити плід.

Щоб зірвати плоди, спершу потрібно за допомогою `hover` піднятися на потрібну висоту. Потім виконайте `move` у бік плоду, щоб зірвати його, і знову `move` геть, щоб бамбук міг рости далі.

Використайте `measure()` на бамбуку, щоб дізнатися, на якій висоті з'явиться наступний плід. `measure()` рахує з `0`, тож `hover(measure())` підніме дрон саме на ту висоту, де буде плід.

{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
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
hover(measure()) # піднятися так, щоб дрон опинився поруч із плодом

move(East) # відлетіти й почекати, поки він виросте
for i in range(3):
    do_a_flip()

move(West) # зірвати плід
move(East) # знову відлетіти
}}

## Ширяння
Команда `hover` приймає один аргумент: висоту ширяння, тобто число від `0` до `18`. За замовчуванням дрон ширяє на висоті `1`. `hover` не може опустити дрон у тверді сутності, тож якщо дрон уже над бамбуком, ви не зможете залетіти в нього, виконавши `hover(0)`.

`hover` повертає `True`, якщо дрону вдалося піднятися на вказану висоту, і `False` в іншому разі.

Крім того, є команда `get_hover`, яка повертає поточну висоту ширяння дрона.

Якщо під час ширяння використати `dig`, `harvest` або `plant`, дрон повернеться на висоту ширяння за замовчуванням (`1`).

Нарешті, ширяння не впливає на `get_pos_z()`. Ця функція завжди повертає z-координату блоку під дроном.

## Збір бамбука
Можна використати `harvest()`, але для збору бамбукових полів радимо залітати в бамбук дроном на висоті ширяння `0` (`hover(0)`). Так уся рослина збирається одразу.

Якщо ви хочете зібрати бамбук, не знищуючи його, можна виконати `move` у нього на будь-якій висоті, наприклад після `hover(3)`. Так ви зберете всі частини бамбука від цієї висоти й вище, але сама рослина залишиться живою. Частково зібраний таким чином бамбук знову утворить плоди, тож їх доведеться зривати знову.

В обох випадках урожай дорівнює квадрату кількості знищених частин бамбука, тож що вищий бамбук, то більший урожай.

---

[Статистика](docs/stats.md)      [Цикл for](docs/scripting/for.md)      [Змінні](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Функції](docs/scripting/functions.md)      [Рис](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
