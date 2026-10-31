[<- Рис](docs/unlocks/rice.md) <right>[Цветные блоки ->](docs/unlocks/debug_place.md)
<right>[Пирамиды ->](docs/unlocks/pyramid.md)
---
# Бамбук
Бамбук растет вверх. Чтобы он мог расти дальше, дрону придется регулярно срывать его коричневые плоды. В этом поможет недавно разблокированная команда `hover`.

Бамбук нужно сажать на вспаханную грядку (`Grounds.Soil`), а для его посадки требуется рис.

Следующий код сажает бамбук и ждет, пока тот вырастет до первого плода.
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
move(East) # отойти, чтобы бамбук мог расти
}}

## Плоды
Бамбук растет со скоростью ровно 1 блок в секунду.

Каждые несколько блоков на бамбуке появляется плод. Когда это происходит, бамбук перестает расти, и тебе нужно залететь в него дроном, чтобы уничтожить плод.

Чтобы сорвать плод, сначала поднимись на нужную высоту с помощью `hover`. Затем влети в плод с помощью `move`, чтобы сорвать его, и снова отлети с помощью `move`, чтобы бамбук мог расти дальше.

Вызови `measure()` у бамбука, чтобы узнать, на какой высоте появится следующий плод. Функция `measure()` начинает отсчет с `0`, поэтому `hover(measure())` поднимет дрон на ту высоту, где будет плод.

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
hover(measure()) # подняться так, чтобы дрон оказался рядом с плодом

move(East) # отойти и подождать, пока бамбук вырастет
for i in range(3):
    do_a_flip()

move(West) # сорвать плод
move(East) # снова отойти
}}

## Парение
Команда `hover` принимает один аргумент: высоту парения, число от `0` до `18`. По умолчанию дрон парит на высоте `1`. `hover` не может опустить дрон внутрь твердых объектов, поэтому если дрон уже находится над бамбуком, ты не сможешь влететь в него, выполнив `hover(0)`.

`hover` возвращает `True`, если дрону удалось перейти на указанную высоту, и `False` в противном случае.

Кроме того, есть команда `get_hover`, которая возвращает текущую высоту парения дрона.

Если во время парения использовать `dig`, `harvest` или `plant`, дрон вернется на высоту парения по умолчанию (`1`).

Наконец, высота парения не влияет на `get_pos_z()`. Эта функция всегда возвращает z-координату блока под дроном.

## Сбор бамбука
Можно использовать и `harvest()`, но поля бамбука лучше собирать, влетая в бамбук дроном на высоте парения `0` (`hover(0)`). Так растение собирается целиком за один раз.

Если хочешь собрать бамбук, не уничтожая его, влети в него с помощью `move` на любой высоте, например `hover(3)`. Так соберутся все части бамбука от этой высоты и выше, но сам бамбук останется жив. Частично собранный таким образом бамбук снова отрастит плоды, так что их придется срывать заново.

В любом случае урожай равен квадрату количества уничтоженных частей бамбука, так что чем выше бамбук, тем больше урожай.

---

[Статистика](docs/stats.md)      [Цикл For](docs/scripting/for.md)      [Переменные](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Функции](docs/scripting/functions.md)      [Рис](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
