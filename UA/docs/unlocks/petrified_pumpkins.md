[<- Рис](docs/unlocks/rice.md)
---
# Скам'янілі гарбузи

Виявляється, гарбузи можна знайти й під землею. Вони затверділи й скам'яніли, але для наших цілей цілком годяться.

Скам'янілі гарбузи трапляються під землею кубами 3x3x3 або 5x5x5. Надійного способу їх знайти немає, лишається сподіватися, що дрон натрапить на них, але залягають вони у твердій землі під шаром каменю й заліза, приблизно на тій самій глибині, що й кварц (якщо він розблокований).

Це ще один спосіб отримати гарбузи, не вирощуючи їх на поверхні. Якщо вам більше до вподоби фермерство, скам'янілі гарбузи можна спокійно ігнорувати.

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
    "items": [{"item": "hay", "n": 100}],
    "exclude_unlocks": ["mushrooms", "watering", "fertilizer", "pyramid", "dynamite"],
    "world_size": {"x": 6, "y": 6},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 3
}
#SETUP
jump(Unlocks.Petrified_Pumpkins)
move(East)
move(North)
move(North)
move(North)
#CODE
while get_ground_type() != Grounds.Petrified_Pumpkin:
    dig()
z = get_pos_z()
for i in range(get_world_size()):
    for j in range(get_world_size()):
        while get_pos_z() > z:
            dig()
        move(North)
    move(East)
}}

---

[Статистика](docs/stats.md)      [Видобуток](docs/unlocks/mining.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
