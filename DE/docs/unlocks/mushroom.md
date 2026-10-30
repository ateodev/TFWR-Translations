[<- Quarz](docs/unlocks/quartz.md) <right>[Dynamit ->](docs/unlocks/dynamite.md)
---
# Pilze

Viele Pilzarten wachsen unterirdisch in Kolonien. Suche beim Graben nach einer Schicht aus `Grounds.Mushroom`. Mit `measure()` kannst du dann den Pilztyp als Zahl von `0` bis `5` ermitteln.

Der folgende Code findet einige Pilze und gibt ihren Typ aus:
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

Pilze desselben Typs sind gern zusammen, aber etwas zu schüchtern, um übereinander zu wachsen. Schiebe den Pilzblock unter der Drohne mit `push(direction)`.

Staple zwei Pilzblöcke desselben Typs übereinander, dann werden die Blöcke automatisch geerntet und du erhältst ihre Pilze.

Der folgende Code schafft Platz und schiebt dann einen Pilz, bis er zum Pilz darunter passt:
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

# Blöcke schieben
Mit `can_push(direction)` kannst du prüfen, ob sich der Block unter der Drohne schieben lässt und ob in der angegebenen Richtung etwas im Weg ist.

`push(direction)` schiebt den Block und gibt zurück, ob das Schieben erfolgreich war.

Nur Pilzblöcke können geschoben werden. Blöcke können nicht nach oben geschoben werden, und befindet sich ein anderer Block im Weg, schlägt das Schieben fehl. Werden Blöcke in die Luft geschoben, fallen sie herunter und landen auf dem nächsten Block unter ihnen.

# Strategie
<spoiler=Hinweis>
Denke daran, dass du mit `place(Grounds.Dirt)` Blöcke unter der Drohne platzieren kannst. So kannst du Löcher auffüllen, um Blöcke darüberzuschieben.
</spoiler>

---

[Statistiken](docs/stats.md)      [Unterirdische Sinne](docs/unlocks/underground_senses.md)      [Dictionaries](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
