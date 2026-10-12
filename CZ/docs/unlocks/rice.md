[<- Těžba](docs/unlocks/mining.md) <right>[Bambus ->](docs/unlocks/bamboo.md)
<right>[Zkamenělé dýně ->](docs/unlocks/petrified_pumpkins.md)
<right>[Perlit a hlína ->](docs/unlocks/special_soils.md)
---
# Rýže

Pod povrchem sis všiml tenké vrstvy jílu. Ukazuje se, že tahle úrodná půda je ideální pro sázení sazenic rýže.

Rýže vysuší jíl, na kterém byla zasazena. Každý blok jílu lze použít jen jednou. Naštěstí je vrstva několik bloků tlustá. A samozřejmě můžeš svět vždy prostě vyčistit pomocí `clear()` a vrstvu jílu tak získat zpět.

Následující kód se ti může hodit ke kopání dolů, dokud nenajdeš jíl.

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

[Statistiky](docs/stats.md)      [Těžba](docs/unlocks/mining.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [For Loop](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
