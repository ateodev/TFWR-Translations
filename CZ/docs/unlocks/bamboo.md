[<- Rýže](docs/unlocks/rice.md) <right>[Barevné bloky ->](docs/unlocks/debug_place.md)
<right>[Pyramidy ->](docs/unlocks/pyramid.md)
---
# Bambus

Bambus je rostlina, která může vyrůst až do výšky 6 bloků. Neroste, dokud je nad ním dron, takže po `plant(Entities.Bamboo)` dron nezapomeň pomocí `move` přesunout. Sázení bambusu stojí rýži.

Bambus vykvete, když dosáhne určité, náhodně zvolené výšky. Pomocí `measure()` zjistíš, v jaké výšce vykvete. `measure()` počítá od 0, takže pokud bambus kvete na druhém bloku, `measure()` vrátí 1:

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 1000, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "rice", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
print(measure())
move(East)
}}

Maximální výnos z bambusu získáš, když zavoláš `harvest()`, zatímco je dron přímo nad květem. Za každý blok rozdílu se výnos vydělí osmi.
Například pokud je květ ve výšce 3, ale sklidíš ho o dva bloky výš, výnos se vydělí 64.

Chceš-li sklidit květy výše, vleť do bambusu, když je dron v požadované výšce. Pomůže ti s tím nově odemčený příkaz `place()`.

Pomocí `place(Grounds.Dirt)` naskládej bloky vedle bambusu a vyšplhej nahoru. Pak pomocí `move()` vleť do bambusu z boku. Při volání `harvest()` by měl být dron přímo nad květem.

`place(Grounds.Dirt)` tě stojí 1 blok! Můžeš pokládat i jiné půdy, například `Grounds.Rock`, ale ne speciální bloky jako `Grounds.Clay`.

Bambus roste přesně o 1 blok za sekundu.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 1000, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "block", "n": 100}, {"item": "rice", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
print(measure())
move(East)
place(Grounds.Dirt)
do_a_flip() # chvíli počkej
do_a_flip()
move(West)
harvest()
}}

---

[Statistiky](docs/stats.md)      [For Loop](docs/scripting/for.md)      [Proměnné](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Funkce](docs/scripting/functions.md)      [Rýže](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [place()](functions/place)      [measure()](functions/measure)
