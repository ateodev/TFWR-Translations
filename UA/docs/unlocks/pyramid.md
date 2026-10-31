[<- Бамбук](docs/unlocks/bamboo.md)
---
# Піраміди
Тепер під землею є стародавні пірамідальні споруди, з яких можна отримувати енергію, щоб пришвидшити дрон!

Піраміди складаються з блоків піску (`Grounds.Sand`). Під самою пірамідою лежить шар фундаменту з вапняку (`Grounds.Limestone`). Оскільки вони старі й зруйновані ерозією, ви знайдете їх лише частково зруйнованими. Шар фундаменту є завжди, але в піску будуть дірки.

Ось як виглядає піраміда, коли її відкопати:
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
    "items": [{"item": "hay", "n": 100}, {"item": "block", "n": 100}],
    "world_size": {"x": 6, "y": 6},
    "execution_speed": 32,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 7,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite", "quartz"]
}
#SETUP
jump(Unlocks.Pyramid)
move(North)
#CODE
# Копаємо вниз, щоб знайти фундамент піраміди
while get_ground_type() != Grounds.Limestone:
    dig()

z = get_pos_z() # Запам'ятовуємо глибину фундаменту

# Викопуємо все, що не є частиною піраміди
for i in range(6):
    for j in range(6):
        while (get_ground_type() != Grounds.Limestone
                and get_ground_type() != Grounds.Sand
                and get_pos_z() > z):
            dig()
        move(North)
    move(East)
}}

## Відновлення піраміди
Як бачите, у піску є кілька дірок, які потрібно заповнити. Коли ви заповните ці дірки й відновите піраміду до початкового стану, вона самознищиться, а посередині вапнякової основи з'явиться великий соняшник. Зберіть його, щоб отримати `Items.Power`. Що більшу піраміду ви завершили, то більше енергії отримаєте.

Відновити піраміду можна, розміщуючи блоки командою `place(Grounds.Sand)`. Пісок — особливий блок, який одразу обвалюється без належної опори. Блок піску можна ставити лише безпосередньо на вапняк або на квадрат 3x3 з блоків піску. Ось маленька піраміда, побудована вручну для прикладу. Звісно, побудована власноруч піраміда енергії не дасть:

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
    "items": [{"item": "hay", "n": 100}, {"item": "block", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 4,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#CODE
# Потрібен вапняковий фундамент, щоб класти на нього пісок
for i in range(3):
    for j in range(3):
        place(Grounds.Limestone)
        move(North)
    move(East)

# Кладемо шар піску 3x3 на вапняк
for i in range(3):
    for j in range(3):
        place(Grounds.Sand)
        move(North)
    move(East)

# Пробуємо покласти ще один шар 3x3
# Зверніть увагу, що опору має й залишається лише середній блок
for i in range(3):
    for j in range(3):
        place(Grounds.Sand)
        move(North)
    move(East)
}}

Правильно відновлена піраміда складається з квадратного вапнякового фундаменту з непарною довжиною сторони, наприклад 5x5. Над ним лежить шар блоків піску того самого розміру (5x5), а далі дедалі менші шари: 3x3, потім 1x1.

Блоки над пірамідою — завжди земля. Якщо ви хочете відкопувати піраміди ефективно, скористайтеся цим.

## Енергія
Поки у вас є енергія, дрон використовує її, щоб рухатися вдвічі швидше.
Він витрачає 1 одиницю енергії кожні 30 дій (наприклад, переміщення, збирання, саджання тощо).
Виконання інших інструкцій коду також може споживати енергію, але значно менше, ніж дії дрона.

Загалом, усе, що пришвидшується завдяки покращенням швидкості, також пришвидшується завдяки енергії.
Усе, що пришвидшується енергією, також споживає її пропорційно до часу виконання, без урахування покращень швидкості.

Енергія не впливає на `dig()`.

---

[Статистика](docs/stats.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [use_item()](functions/use_item)      [place()](functions/place)
