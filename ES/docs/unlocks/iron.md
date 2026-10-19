[<- Carbón](docs/unlocks/coal.md) <right>[Cuarzo ->](docs/unlocks/quartz.md)
<right>[Prospección de hierro ->](docs/unlocks/prospecting.md)
<right>[Mapa del tesoro ->](docs/unlocks/treasure_map.md)
---
# Hierro

Después de encontrar carbón en `Grounds.Dirt`, puedes excavar más hondo, más allá de la capa de `Grounds.Clay` y hasta `Grounds.Rock`, para encontrar hierro.

A diferencia de las vetas de carbón, las vetas de hierro también se extienden en vertical. Pero todos los bloques de hierro de una veta están siempre justo unos al lado de otros; nunca se conectan solo en diagonal.

Pero las vetas de hierro empiezan siendo pequeñas y necesitarás algo de suerte para encontrarlas. Seguir desbloqueando el hierro aumenta el tamaño máximo de las vetas y hace que sea un poco más fácil encontrarlas por casualidad. Pero para encontrarlas de forma fiable, deberías desbloquear la [prospección de hierro](docs/unlocks/prospecting.md).

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
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#SETUP
jump(Unlocks.Iron)
#CODE
for i in range(4):
    dig()
do_a_flip()
}}

---

[Estadísticas](docs/stats.md)      [Minería](docs/unlocks/mining.md)      [Prospección de hierro](docs/unlocks/prospecting.md)      [Sentidos subterráneos](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
