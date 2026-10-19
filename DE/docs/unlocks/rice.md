[<- Bergbau](docs/unlocks/mining.md) <right>[Bambus ->](docs/unlocks/bamboo.md)
<right>[Versteinerte Kürbisse ->](docs/unlocks/petrified_pumpkins.md)
<right>[Perlit und Lehmboden ->](docs/unlocks/special_soils.md)
---
# Reis

Unter der Oberfläche und der Schicht aus `Grounds.Dirt` ist dir vielleicht eine dünne Schicht aus `Grounds.Clay` aufgefallen. Wie sich herausstellt, eignet sich dieser fruchtbare und durchnässte Boden perfekt zum Pflanzen von Reissetzlingen.

Wie bei Gras oder Büschen kannst du, solange deine Drohne über einem `Grounds.Clay`-Block ist, mit `plant(Entities.Rice)` Reissetzlinge in den Ton pflanzen, dann mit `can_harvest()` prüfen, ob der Reis ausgewachsen ist, und schließlich mit `harvest()` Reis ernten.

Sobald du Reis pflanzt, wird der Boden zu `Grounds.Rice_Terrace`, damit der Reis perfekt reifen kann. Ist der Reis ausgewachsen, trocknet der Boden aus, wird zu `Grounds.Dry_Rice_Terrace` und kann nicht mehr für neuen Reis verwendet werden. Zum Glück ist die Schicht mehrere Blöcke dick, sodass du den Block mit `dig()` abtragen und neuen Reis auf dem `Grounds.Clay` darunter pflanzen kannst. Und wenn die Schicht aufgebraucht ist, kannst du jederzeit mit `clear()` die Welt zurücksetzen und zu einer frischen Schicht hinuntergraben.

Der folgende Code könnte dir helfen, nach unten zu graben, bis du Ton findest.

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 8,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(East)
#CODE
while get_ground_type() != Grounds.Clay:
    dig()
plant(Entities.Rice)
move(North)
do_a_flip()
}}

---

[Statistiken](docs/stats.md)      [Bergbau](docs/unlocks/mining.md)      [Unterirdische Sinne](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [For-Schleife](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
