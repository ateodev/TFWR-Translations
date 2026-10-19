[<- Minería](docs/unlocks/mining.md) <right>[Bambú ->](docs/unlocks/bamboo.md)
<right>[Calabazas petrificadas ->](docs/unlocks/petrified_pumpkins.md)
<right>[Perlita y suelo franco ->](docs/unlocks/special_soils.md)
---
# Arroz

Debajo de la superficie y de la capa de `Grounds.Dirt` puede que hayas visto una fina capa de `Grounds.Clay`. Resulta que este terreno fértil y empapado es perfecto para plantar brotes de arroz.

Igual que con la hierba o los arbustos, mientras tu dron esté encima de un bloque de `Grounds.Clay`, puedes usar `plant(Entities.Rice)` para plantar brotes de arroz en la arcilla, luego `can_harvest()` para comprobar si el arroz ha crecido del todo y, por último, `harvest()` para obtener arroz.

En cuanto plantas arroz, el terreno se convierte en `Grounds.Rice_Terrace` para ofrecer el entorno perfecto para que el arroz madure. Cuando el arroz ha crecido del todo, el terreno se seca, se convierte en `Grounds.Dry_Rice_Terrace` y ya no sirve para plantar más arroz. Por suerte, la capa tiene varios bloques de grosor, así que puedes quitar el bloque con `dig()` y plantar arroz nuevo en la `Grounds.Clay` de debajo. Y, si la capa se agota, siempre puedes usar `clear()` en el mundo y excavar hasta una capa nueva.

El siguiente código puede resultarte útil para excavar hacia abajo hasta encontrar arcilla.

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 8,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(East)
#CODE
while get_ground_type() != Grounds.Clay:
    dig()
plant(Entities.Rice)
move(North)
do_a_flip()
}}

---

[Estadísticas](docs/stats.md)      [Minería](docs/unlocks/mining.md)      [Sentidos subterráneos](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [Bucle for](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
