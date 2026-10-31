[<- Перша програма](docs/first_program.md) <right>[Покращення швидкості ->](docs/unlocks/speed.md)
---
# Цикл while
Ви розблокували цикл `while` та значення `True` і `False`. Цикл `while` виконує тіло циклу доти, доки умова дорівнює `True`:

`while condition:
	#тіло циклу`

Не хвилюйтесь щодо створення нескінченних циклів. Дрон може застрягнути, але вся гра не зависне: ви можете просто зупинити запущену програму і спробувати знову.

## Для новачків
Можливо, ви вже пробували написати кілька викликів `harvest()` підряд:

{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
do_a_flip()
#CODE
harvest()
harvest()
harvest()
}}
Це дозволяє зібрати врожай кілька разів за один запуск програми. 
Однак було б добре збирати врожай більше ніж три рази, а якщо писати той самий код багато разів, програма швидко перетворюється на безлад. 
Рішенням є цикл. 
Цикл дозволяє виконувати один і той самий код багато разів.

Цикл `while` приймає умову — логічне значення, яке може бути лише в одному з двох станів: `True` або `False`. 
Таке значення називається булевим.

Цикл виконує код всередині циклу, поки умова не прийме значення `False`.
Цикл `while` виглядає так:

`while condition:
	#тіло циклу
	#тіло циклу
	#...`

Потрібно замінити `condition` на булеве значення або вираз, а `#тіло циклу` на код, який ви хочете виконувати.

У вас є два постійні булеві значення (константи). Константи — це значення, які не змінюються під час виконання програми.

Щоб створити константу, яка завжди дорівнює `True`, можна просто написати `True`. Напишіть `False` для створення константи, яка завжди дорівнює `False`.
Тож ви можете написати або

{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
#CODE
while False:
	do_a_flip()
}}
або

{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
#CODE
while True:
	do_a_flip()
}}
Перший код ніколи не виконає переворот, а другий виконуватиме перевороти безкінечно (нескінченний цикл). 

Зазвичай нескінченний цикл — це погана ідея, так як через них програма може зависнути, але в цій грі між ітераціями є затримки, тому дрон буде продовжувати виконувати перевороти, доки ви вручну не зупините виконання (натиснувши кнопку Виконати повторно).

Зверніть увагу, що рядки після двокрапки мають відступ. Подібні відступи використовуються для позначення блоку коду.
Натисніть `Tab`, щоб додати відступ, і `Shift + Tab` (або <desktop>`Backspace`</desktop><mobile>«Видалити»</mobile>), щоб його видалити. Якщо виділено кілька рядків, `Tab` і `Shift + Tab` застосуються до всіх них.

<desktop>Примітка: якщо ви граєте через Steam, натискання `Shift + Tab` натомість відкриє оверлей Steam. Ви можете перепризначити комбінацію для видалення відступу в налаштуваннях гри або комбінацію оверлею Steam в його налаштуваннях.
</desktop>
Тут `do_a_flip()` і `pet_the_piggy()` викликаються повторно, бо вони знаходяться всередині блоку `while` з відступом. Проте `harvest()` ніколи не виконається, бо цей виклик іде після блоку.
{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
#CODE
while True:
	do_a_flip()
	pet_the_piggy()
harvest()
}}

---

[Цикл for](docs/scripting/for.md)      [If](docs/scripting/if.md)      [Break](docs/scripting/break.md)      [Continue](docs/scripting/continue.md)<desktop>      [Зовнішній редактор](docs/external_editor.md)</desktop>
