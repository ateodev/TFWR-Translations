[<- Kohle](docs/unlocks/coal.md) <right>[Quarz ->](docs/unlocks/quartz.md)
<right>[Eisensuche ->](docs/unlocks/prospecting.md)
<right>[Schatzkarte ->](docs/unlocks/treasure_map.md)
---
# Eisen

Nachdem du Kohle in `Grounds.Dirt` gefunden hast, kannst du tiefer graben, an der Schicht aus `Grounds.Clay` vorbei bis in `Grounds.Rock`, um Eisen zu finden.

Anders als Kohleadern erstrecken sich Eisenadern auch senkrecht. Alle Eisenblöcke einer Ader liegen aber immer direkt nebeneinander, die Blöcke sind nie nur diagonal verbunden.

Eisenadern sind anfangs jedoch klein, und du brauchst etwas Glück, um sie zu finden. Wenn du Eisen weiter freischaltest, steigt die maximale Größe der Adern und sie lassen sich etwas leichter zufällig finden. Um sie aber zuverlässig zu finden, solltest du die [Eisensuche](docs/unlocks/prospecting.md) freischalten.

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

[Statistiken](docs/stats.md)      [Bergbau](docs/unlocks/mining.md)      [Eisensuche](docs/unlocks/prospecting.md)      [Unterirdische Sinne](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
