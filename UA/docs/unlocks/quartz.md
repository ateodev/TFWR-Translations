[<- Залізо](docs/unlocks/iron.md) <right>[Гриби ->](docs/unlocks/mushroom.md)
---
# Кварц

Глибше за залізні жили в `Grounds.Rock` ви знайдете кварц у нижній частині кам'яного шару та у твердому `Grounds.Dirt` під ним (перевіряйте твердість за допомогою `get_hardness()` з розблокування [Підземні сенсори](docs/unlocks/underground_senses.md)).

Цей фрагмент коду змушує дрона прокопати землю і заглибитися в кам'яний шар. Далі, якщо пощастить, поблизу буде кварцова жила, і дрон виведе відстань до неї.
{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite"]
}
#SETUP
move(East)
move(North)
#CODE
while get_ground_type() != Grounds.Rock:
    dig()
for i in range(30):
    dig()

print(prospect_quartz())
move(South)
print(prospect_quartz())
}}

## Будова жил
Кварц росте голчастими жилами, що утворюють вертикальні стовпи, тож методом проб і помилок їх знайти досить важко.

## Пошук кварцу
На щастя, ми можемо взяти залізо і зігнути його в щось на кшталт лози, яка допомагає легше знаходити кварцові жили. Для цього є команда `prospect_quartz()`.

`prospect_quartz()` працює інакше, ніж `prospect_iron()`. Замість напрямку, у якому дрону слід рухатися до найближчої залізної руди, вона повертає точну відстань у 3D між найближчим блоком кварцу і дроном (евклідову відстань).

Виконання `prospect_quartz()` коштує 1 залізо, тому команду варто використовувати ощадливо.

Якщо `prospect_quartz()` не знаходить кварцу поблизу або у вас недостатньо заліза для пошуку, вона повертає `None`.

## Стратегія
<spoiler=показати підказку>
Можна раз у раз виконувати пошук і переміщатися, стежачи, як змінюється відстань, щоб зрозуміти, наближаєтеся ви до жили чи віддаляєтеся від неї. За допомогою 2D-геометрії можна знайти перетин двох або більше кіл, визначити горизонтальне положення жили й копати вниз. Або можна застосувати повну трилатерацію, щоб перетнути три сфери й знайти точне положення в 3D.

Зверніть увагу, що базових математичних функцій для квадратного кореня, тригонометрії чи векторів немає, тож їх доведеться написати самостійно. Також зверніть увагу, що поблизу може бути кілька жил, тож кілька сусідніх вимірювань можуть вказувати на різні жили й збити вас з пантелику.
</spoiler>

---

[Статистика](docs/stats.md)      [Видобуток](docs/unlocks/mining.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)      [Змінні](docs/scripting/variables.md)      [Оператори](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
