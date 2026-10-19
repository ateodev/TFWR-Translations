[<- Вугілля](docs/unlocks/coal.md) <right>[Кварц ->](docs/unlocks/quartz.md)
<right>[Пошук заліза ->](docs/unlocks/prospecting.md)
<right>[Карта скарбів ->](docs/unlocks/treasure_map.md)
---
# Залізо

Знайшовши вугілля в `Grounds.Dirt`, можна копати глибше, повз шар `Grounds.Clay` і далі в `Grounds.Rock`, щоб знайти залізо.

На відміну від вугільних жил, залізні жили тягнуться й по вертикалі. Але всі блоки заліза в жилі завжди прилягають один до одного впритул, блоки ніколи не з'єднуються лише по діагоналі.

Проте спочатку залізні жили маленькі, і щоб їх знайти, потрібна удача. Подальше розблокування заліза збільшує максимальний розмір жил і трохи полегшує їх випадковий пошук. Але щоб знаходити їх надійно, варто розблокувати [пошук заліза](docs/unlocks/prospecting.md).

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#SETUP
jump(Unlocks.Iron)
#CODE
for i in range(4):
    dig()
do_a_flip()
}}

---

[Статистика](docs/stats.md)      [Видобуток](docs/unlocks/mining.md)      [Пошук заліза](docs/unlocks/prospecting.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
