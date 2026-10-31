[<- Залізо](docs/unlocks/iron.md)
---
# Карта скарбів
Легенди розповідають про невловимий скарб, захований давно померлим забудькуватим піратом, чи щось таке. А якщо він записав шлях до скарбу на карті, а потім її загубив? Може, він упустив карту, коли його притиснула річка лави, і вона збереглася під шаром базальту.

Вимірювання блоків базальту може щось відкрити!

<spoiler=розкажи більше>
Шукайте шар `Grounds.Basalt`. Спробуйте виміряти базальт і подивіться, що він вам скаже. Підказка може привести до карти скарбів, а вимірювання карти напевно поверне шлях до самого скарбу — але чи зможете ви розшифрувати вказівки карти?
</spoiler>

<spoiler=просто скажи як>
Гаразд, ось у чому річ: знайдіть шар `Grounds.Basalt` і блок `Grounds.Treasure_Map` прямо під ним. Виміряйте базальт через `measure()`, щоб отримати позицію `(x, y)` блоку карти внизу.

Викличте `measure()` на блоці карти, щоб отримати шлях до скарбу як рядок літер напрямків. N, E, S і W означають відповідно `North`, `East`, `South` і `West`, а D — «вниз» або «копати». Ці літери описують шлях із блоків `Grounds.Treasure_Path`, що веде до скарбу.

{{codeexample 
{
    "camera_position": {"x": -1.5, "y": 0, "z": 6},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": true,
    "collapsing": true,
    "autoplay": false,
    "items": [],
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
# Шукаємо шар базальту
while get_ground_type() != Grounds.Basalt:
    dig()

# Вимірювання базальту повертає позицію карти скарбів
map_pos = measure()

while get_pos_x() < map_pos[0]:
    move(East)
while get_pos_y() < map_pos[1]:
    move(North)

while get_ground_type() != Grounds.Treasure_Map:
    dig()

# Карту знайдено, вимірюємо її, щоб отримати шлях
do_a_flip()
instructions = measure()
print("вказівки: ", instructions)

# Копаємо в карту, щоб почати пошук скарбу
dig()
}}

За допомогою циклу `for` можна обробити рядок літера за літерою:
{{codeexample 
{
    "camera_position": {"x": -1.5, "y": 0, "z": 6},
    "show_image": false,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": true,
    "collapsing": true,
    "autoplay": false,
    "items": [],
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
while get_ground_type() != Grounds.Basalt:
    dig()

map_pos = measure()

while get_pos_x() < map_pos[0]:
    move(East)
while get_pos_y() < map_pos[1]:
    move(North)

while get_ground_type() != Grounds.Treasure_Map:
    dig()
#CODE
# Вказівки карти повертаються одним рядком
instructions = measure()
# Використовуємо for-in, щоб розбити рядок на літери
for letter in instructions:
    print(letter)
}}

Дрон весь час має залишатися над блоками `Grounds.Treasure_Path`. Якщо він перейде на інший ґрунт, шлях обірветься, а скарб буде втрачено.

## Ціль
Наприкінці шляху лежить блок `Grounds.Treasure_Goal`. Якщо дрон не збився зі шляху, на ньому з'явиться `Entities.Underground_Treasure`. Дрон може зібрати скриню через `harvest()`, щоб забрати її золото.

## Винагорода
Кількість золота пропорційна довжині шляху до скарбу. Покращення розблокування «Карта скарбів» збільшує глибину шляху, а покращення «Розширення» дає йому більше місця для бокових переміщень. Обидва покращення збільшують довжину шляху і кількість золота, яке ви знайдете.

## Кілька дронів
Дрон, який копає блок карти скарбів, і є тим дроном, що має знайти скарб, не сходячи з блоків шляху.
</spoiler>

---

[Статистика](docs/stats.md)      [Цикл for](docs/scripting/for.md)      [Кортежі](docs/scripting/tuples.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)

[harvest()](functions/harvest)      [move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)
