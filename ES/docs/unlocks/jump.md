[<- Carbón](docs/unlocks/coal.md)
---
# Saltar

Tu dron ha desbloqueado el comando `jump()`. Para usarlo, debes pasarle un desbloqueo como argumento, por ejemplo, `Unlocks.Iron`.

Este comando te permite seleccionar ciertos desbloqueos que están ocultos bajo tierra y saltar al instante hasta ellos. Resulta especialmente útil para depurar o para ir directamente a una veta de mineral que acabas de pasar por alto.

Después del salto, el desbloqueo objetivo debería estar como máximo a 3 bloques de la superficie de bloques superior. `jump()` solo se puede usar una vez por ejecución del programa; los intentos de salto posteriores producirán un error.

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

## Desbloqueos compatibles
`jump()` solo funciona con los siguientes desbloqueos de minería:
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
