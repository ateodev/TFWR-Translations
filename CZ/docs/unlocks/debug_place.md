[<- Bambus](docs/unlocks/bamboo.md)
---
# Barevné bloky

Jak už víš, pomocí `place()` může dron položit blok. Toto odemčení přidává barevné bloky, které se vizuálně odlišují od svého okolí.

Jak položit nové bloky:

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
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"],
    "starting_chunk": 2
}
#SETUP
move(East)
move(North)
dig()
dig()
dig()
#CODE
place(Grounds.Red_Block)
place(Grounds.Green_Block)
place(Grounds.Blue_Block)
}}
---

[Debug](docs/scripting/debug.md)      [Debug 2](docs/unlocks/debug2.md)      [Bambus](docs/unlocks/bamboo.md)

[place()](functions/place)
