[<- Видобуток](docs/unlocks/mining.md) <right>[Залізо ->](docs/unlocks/iron.md)
<right>[Стрибок ->](docs/unlocks/jump.md)
---
# Вугілля

Виявляється, ґрунт одразу під поверхнею — гарне місце для пошуку покладів вугілля.

Вугілля з'являється випадково горизонтальними пластами завтовшки 1 блок. Розмір пласта зростає пропорційно до розміру вашого світу, тож варто його збільшити, щоб знайти більше вугілля!

Ця програма — гарна відправна точка для пошуку вугілля. Вона копає вниз у пошуках вугільного пласта, а потім копає на схід і захід, сподіваючись знайти більше вугілля.

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
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2
}
#SETUP
move(North)
move(East)
move(East)
#CODE
while get_ground_type() != Grounds.Coal:
    dig()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

---

[Статистика](docs/stats.md)      [Видобуток](docs/unlocks/mining.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
