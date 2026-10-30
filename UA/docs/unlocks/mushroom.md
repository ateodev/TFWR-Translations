[<- Кварц](docs/unlocks/quartz.md) <right>[Динаміт ->](docs/unlocks/dynamite.md)
---
# Гриби

Під землею колоніями ростуть різні види грибів. Копаючи, шукайте шар `Grounds.Mushroom`. Потім ви можете виміряти ґрунт через `measure()`, щоб отримати тип гриба як число від `0` до `5`.

Наведений нижче код знаходить кілька грибів і виводить їхній тип:
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
for i in range(get_world_size()):
    while get_ground_type() != Grounds.Mushroom:
        dig()

    print(measure())

    move(East)
}}

Гриби одного типу люблять бути разом, але надто сором'язливі, щоб рости один на одному. Зсуньте грибний блок під дроном за допомогою `push(direction)`.

Складіть два грибні блоки одного типу один на одного, і ці блоки буде автоматично зібрано, а ви отримаєте гриби.

Наведений нижче код звільняє місце, а потім зсуває гриб, доки він не збігатиметься з грибом під ним:
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
    move(East)
    while get_pos_z() > depth - 1:
        dig()
    move(West)
    push(East)
    move(East)
}}

# Зсування блоків
За допомогою `can_push(direction)` можна перевірити, чи можна зсунути блок під дроном і чи ніщо не заважає йому в заданому напрямку.

`push(direction)` зсуває блок і повертає, чи вдався зсув.

Зсувати можна лише грибні блоки, блоки не можна штовхати вгору, і зсув не вдасться, якщо на шляху інший блок. Зсунуті в повітря блоки падають і приземляються на найближчий блок під ними.

# Стратегія
<spoiler=підказка>
Пам'ятайте, що можна викликати `place(Grounds.Dirt)`, щоб розмістити блоки під дроном. Це корисно для заповнення ям, щоб можна було зсувати блоки через них.
</spoiler>

---

[Статистика](docs/stats.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)      [Словники](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
