[<- Křemen](docs/unlocks/quartz.md) <right>[Dynamit ->](docs/unlocks/dynamite.md)
---
# Houby

V podzemí rostou v koloniích mnohé druhy hub. Při kopání hledej vrstvu `Grounds.Mushroom`. Pak můžeš půdu změřit pomocí `measure()` a získat typ houby jako číslo počínaje `0`.

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
    "items": [{"item": "hay", "n": 100}, {"item": "iron", "n": 100}],
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
while get_ground_type() != Grounds.Mushroom:
    dig()
do_a_flip()
print(measure())
}}

Houby stejného typu jsou rády pohromadě, ale jsou příliš plaché na to, aby rostly na sobě. Posuň houbový blok na jiný houbový blok stejného typu a oba zmizí, přičemž jako odměnu dostaneš houby.

Pomocí `can_push(direction)` zjistíš, zda lze blok pod dronem posunout a zda mu v daném směru něco nebrání. `push(direction)` blok posune a vrátí, zda se posun zdařil.

Bloky nelze posouvat nahoru a posun se nezdaří, pokud je v cestě jiný blok. Bloky posunuté do vzduchu spadnou a dopadnou na nejbližší blok pod sebou.

Pamatuj, že voláním `place(Grounds.Dirt)` můžeš pokládat bloky pod dron. To se hodí k zaplnění děr, abys přes ně mohl bloky posouvat.

---

[Statistiky](docs/stats.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)      [Slovníky](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
