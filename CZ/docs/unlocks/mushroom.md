[<- Křemen](docs/unlocks/quartz.md) <right>[Dynamit ->](docs/unlocks/dynamite.md)
---
# Houby
V podzemí rostou v koloniích mnohé druhy hub. Při kopání hledej vrstvu `Grounds.Mushroom`. Pak můžeš půdu změřit pomocí `measure()` a získat typ houby jako číslo od `0` do `5`.

Následující kód najde několik hub a vypíše jejich typ:
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
# Zpracuj řadu hub
for i in range(get_world_size()):
    # Prokopej se dolů k hornímu houbovému bloku
    while get_ground_type() != Grounds.Mushroom:
        dig()

    # Vypiš číslo typu houby
    print(measure())

    move(East)
}}

## Jak sbírat houby
Houby stejného typu jsou rády pohromadě, ale jsou trochu příliš plaché na to, aby rostly na sobě. Houbový blok pod dronem posuneš pomocí `push(direction)`.

Polož na sebe dva houbové bloky stejného typu a bloky se automaticky sklidí a dostaneš z nich houby.

Následující kód udělá místo a pak posouvá houbu, dokud neodpovídá houbě pod ní:
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
    # Udělej místo pro posunutí houbového bloku na východ
    move(East)
    while get_pos_z() > depth - 1:
        dig()
    # Vrať se, posuň blok a následuj ho
    move(West)
    push(East) # Posuň houbu!
    move(East)
}}

# Posouvání bloků
Pomocí `can_push(direction)` zjistíš, zda lze blok pod dronem posunout a zda mu v daném směru něco nebrání.

`push(direction)` blok posune a vrátí, zda se posun zdařil.

Posouvat lze jen houbové bloky, bloky nelze posouvat nahoru a posun se nezdaří, pokud je v cestě jiný blok. Bloky posunuté do vzduchu spadnou a dopadnou na nejbližší blok pod sebou.

# Strategie
<spoiler=nápověda>
Pamatuj, že voláním `place(Grounds.Dirt)` můžeš pokládat bloky pod dron. To se hodí k zaplnění děr, abys přes ně mohl bloky posouvat.
</spoiler>

---

[Statistiky](docs/stats.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)      [Slovníky](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
