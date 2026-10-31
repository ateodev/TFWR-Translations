[<- Uhlí](docs/unlocks/coal.md)
---
# Skok
Tvůj dron odemkl příkaz `jump()`. Používá se tak, že mu jako argument předáš odemčení, například `Unlocks.Iron`.

Tento příkaz ti umožňuje zacílit na určité suroviny skryté v zemi a okamžitě k nim skočit dolů. Hodí se zejména při ladění nebo pro skok k rudné žíle, kterou jsi nedávno minul.

Po skoku by cílová surovina měla být do 3 bloků od povrchu nejvyššího bloku. `jump()` lze použít jen jednou za běh programu, další pokusy o skok skončí chybou.

Následující příklad skočí dolů k [rýži](docs/unlocks/rice.md), najde vrstvu jílu a zasadí řadu rýžových teras:
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
    "items": [{"item": "hay", "n": 10}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms"],
    "starting_chunk": 0
}
#CODE
# Skoč blízko k rýži
jump(Unlocks.Rice)

# Zasaď řadu rýžových teras
for i in range(get_world_size()):
    # Skok není přesný, vykopej poslední bloky
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## Kompatibilní odemčení
`jump()` funguje jen s následujícími odemčeními pro těžbu:
- Coal
- Iron
- Quartz
- Rice
- Petrified_Pumpkins
- Special_Soils
- Pyramid
- Treasure_Map
- Mushrooms
- Dynamite

---

[jump()](functions/jump)
