[<- Węgiel](docs/unlocks/coal.md)
---
# Skok

Twój dron odblokował polecenie `jump()`. Używa się go, przekazując odblokowanie jako argument, na przykład `Unlocks.Iron`.

To polecenie pozwala wskazać określone odblokowania ukryte w ziemi i natychmiast przenieść się w dół prosto do nich. Jest szczególnie przydatne podczas debugowania lub do szybkiego dotarcia do niedawno pominiętej żyły rudy.

Po skoku docelowe odblokowanie powinno znajdować się w odległości do 3 bloków od najwyższej powierzchni bloków. `jump()` można użyć tylko raz podczas jednego wykonania programu, a kolejne próby skoku spowodują błąd.

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
jump(Unlocks.Rice)

for i in range(get_world_size()):
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## Zgodne odblokowania
`jump()` działa tylko z następującymi odblokowaniami górniczymi:
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
