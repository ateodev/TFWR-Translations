[<- Rýže](docs/unlocks/rice.md)
---
# Zkamenělé dýně

Dýně se zjevně dají najít i v podzemí. Ztvrdly a zkameněly, ale pro naše účely jsou pořád dost dobré.

Zkamenělé dýně se v podzemí vyskytují v blocích 3x3x3 nebo 5x5x5. Neexistuje spolehlivý způsob, jak je najít, takže musíš doufat, že do nějaké dron kopne, ale vyskytují se v tvrdé hlíně pod vrstvou kamene a železa, zhruba ve stejné hloubce jako křemen (pokud ho máš odemčený).

Je to další způsob, jak získat dýně, aniž bys je pěstoval na povrchu. Pokud dáváš přednost farmaření, můžeš zkamenělé dýně klidně úplně ignorovat.

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

[Statistiky](docs/stats.md)      [Těžba](docs/unlocks/mining.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
