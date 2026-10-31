[<- Těžba](docs/unlocks/mining.md)
---
# Podzemní senzory
Přidáme pár senzorů, aby se tvůj dron v podzemí vyznal.

## Pozice z
Nyní můžeš pomocí `get_pos_z()` zjistit výšku dronu (začíná na 0 a při sestupu dronu je záporná).

{{codeexample 
{
    "camera_position": {"x": -1.5, "y": 0, "z": 10},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "exclude_unlocks": ["watering", "fertilizer"],
    "items": [],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(North)
move(North)
move(East)
move(East)
#CODE
print(get_pos_z())
dig()
dig()
dig()
print(get_pos_z())
}}

## Typ půdy
`get_ground_type()` vrací typ půdy pod dronem. Můžeš mu předat argument směru, například `get_ground_type(North)`, a získat typ půdy sousedního políčka.

Takhle zkontroluješ, zda je blok pod dronem hlína:

{{codeexample 
{
    "camera_position": {"x": -1.5, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "exclude_unlocks": ["watering", "fertilizer"],
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

## Tvrdost a stabilita
`get_hardness()` vrací tvrdost políčka půdy pod dronem. Čím vyšší tvrdost políčka, tím déle trvá ho vykopat. Můžeš mu předat argument směru, například `get_hardness(North)`.

`get_stability()` vrací stabilitu políčka půdy pod dronem. Stabilita 1 znamená, že blok vydrží výškový rozdíl 1, než se sesune. Můžeš mu předat argument směru, například `get_stability(North)`.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 10},
    "show_image": true,
    "image_size": {"x": 800, "y": 250},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 0
}
#SETUP
jump(Unlocks.Rice)
#CODE
print(get_hardness(), "|", get_stability())
while get_hardness() == 1:
    dig()

print(get_hardness(), "|", get_stability())
while get_hardness() == 2 and get_stability() == 3:
    dig()
}}

Všimni si, že čtyři bloky přímo vedle dronu se při kopání dolů odstraní bez ohledu na jejich stabilitu, pokud blok nemá zvláštní funkci. Například jíl, železo a křemen se podle tohoto pravidla neodstraňují. Stále se však mohou sesunout kvůli nedostatečné stabilitě bloku.
---

[Těžba](docs/unlocks/mining.md)      [Smysly](docs/unlocks/senses.md)

[get_pos_z()](functions/get_pos_z)      [get_ground_type()](functions/get_ground_type)      [get_hardness()](functions/get_hardness)      [get_stability()](functions/get_stability)
