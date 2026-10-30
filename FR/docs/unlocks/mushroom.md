[<- Quartz](docs/unlocks/quartz.md) <right>[Dynamite ->](docs/unlocks/dynamite.md)
---
# Champignon

De nombreux types de champignons poussent en colonies sous terre. En creusant, cherche une strate de `Grounds.Mushroom`. Tu peux ensuite appeler `measure()` sur le sol pour obtenir le type de champignon sous forme d’un nombre allant de `0` à `5`.

Le code suivant trouve quelques champignons et affiche leur type :
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

Les champignons du même type aiment se retrouver, mais ils sont un peu trop timides pour pousser les uns sur les autres. Pousse le bloc de champignon situé sous le drone avec `push(direction)`.

Empile deux blocs de champignon du même type l’un sur l’autre : les blocs seront automatiquement récoltés et te rapporteront leurs champignons.

Le code ci-dessous libère de la place, puis pousse un champignon jusqu’à ce qu’il corresponde au champignon situé dessous :
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

# Pousser des blocs
Tu peux utiliser `can_push(direction)` pour vérifier si le bloc sous le drone peut être poussé et si quelque chose lui barre la route dans la direction indiquée.

`push(direction)` pousse le bloc et indique si l’opération a réussi.

Seuls les blocs de champignon peuvent être poussés. Les blocs ne peuvent pas être poussés vers le haut, et la poussée échoue si un autre bloc fait obstacle. Lorsqu’un bloc est poussé dans le vide, il tombe et atterrit sur le prochain bloc situé dessous.

# Stratégie
<spoiler=indice>
N’oublie pas que tu peux appeler `place(Grounds.Dirt)` pour placer des blocs sous le drone. Cela peut être utile pour combler les trous et pousser des blocs par-dessus.
</spoiler>

---

[Statistiques](docs/stats.md)      [Sens souterrains](docs/unlocks/underground_senses.md)      [Dictionnaires](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
