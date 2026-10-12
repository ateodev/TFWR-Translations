[<- Těžba](docs/unlocks/mining.md)
---
# Podzemní senzory

Přidáme pár senzorů, aby se tvůj dron v podzemí vyznal.

Nyní můžeš pomocí `get_pos_z()` zjistit výšku dronu (začíná na 0 a při sestupu dronu je záporná).

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#CODE
move(North)
move(North)
move(East)
dig()
dig()
dig()
print(get_pos_z())
}}

`get_ground_type()` vrací typ půdy pod dronem. Můžeš mu předat argument směru, například `get_ground_type(North)`, a získat typ půdy sousedního políčka.

Takhle zkontroluješ, zda je blok pod dronem hlína:

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
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#CODE
dig()
if get_ground_type() == Grounds.Dirt:
    do_a_flip()
}}


`get_hardness()` vrací tvrdost políčka půdy pod dronem. Můžeš mu předat argument směru, například `get_hardness(North)`. Čím vyšší tvrdost políčka, tím déle trvá ho vykopat.

`get_stability()` vrací stabilitu políčka půdy pod dronem. Můžeš mu předat argument směru, například `get_stability(North)`. Stabilita 1 znamená, že blok vydrží výškový rozdíl 1, než se sesune.

Všimni si, že čtyři bloky přímo vedle dronu se při kopání dolů odstraní bez ohledu na jejich stabilitu, pokud blok nemá zvláštní funkci. Například jíl, železo a křemen se podle tohoto pravidla neodstraňují. Stále se však mohou sesunout kvůli nedostatečné stabilitě bloku.
---

[Těžba](docs/unlocks/mining.md)      [Senses](docs/unlocks/senses.md)

[get_pos_z()](functions/get_pos_z)      [get_ground_type()](functions/get_ground_type)      [get_hardness()](functions/get_hardness)      [get_stability()](functions/get_stability)
