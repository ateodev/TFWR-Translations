[<- Кварц](docs/unlocks/quartz.md) <right>[Динаміт ->](docs/unlocks/dynamite.md)
---
# Гриби

Під землею колоніями ростуть різні види грибів. Копаючи, шукайте шар `Grounds.Mushroom`. Потім ви можете виміряти ґрунт через `measure()`, щоб отримати тип гриба як число, починаючи з `0`.

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
    "digging_speed": 6,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron"]
}

#SETUP
jump(Unlocks.Mushrooms)
#CODE
while get_ground_type() != Grounds.Mushroom:
    dig()
do_a_flip()
print(measure())
}}

Гриби одного типу люблять бути разом, але надто сором'язливі, щоб рости один на одному. Зсуньте грибний блок на інший грибний блок того самого типу — вони зникнуть, а ви отримаєте гриби як винагороду.

За допомогою `can_push(direction)` можна перевірити, чи можна зсунути блок під дроном і чи ніщо не заважає йому в заданому напрямку. `push(direction)` зсуває блок і повертає, чи вдався зсув.

Блоки не можна штовхати вгору, і зсув не вдасться, якщо на шляху інший блок. Зсунуті в повітря блоки падають і приземляються на найближчий блок під ними.

Пам'ятайте, що можна викликати `place(Grounds.Dirt)`, щоб розмістити блоки під дроном. Це корисно для заповнення ям, щоб можна було зсувати блоки через них.

---

[Статистика](docs/stats.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)      [Словники](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
