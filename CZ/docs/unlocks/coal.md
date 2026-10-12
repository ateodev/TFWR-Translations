[<- Těžba](docs/unlocks/mining.md) <right>[Železo ->](docs/unlocks/iron.md)
<right>[Skok ->](docs/unlocks/jump.md)
---
# Uhlí

Ukazuje se, že půda těsně pod povrchem je dobré místo pro hledání ložisek uhlí.

Uhlí se objevuje náhodně ve vodorovných vrstvách o tloušťce 1 bloku. Velikost vrstvy roste úměrně velikosti tvého světa, takže ho možná budeš chtít zvětšit, abys našel více uhlí!

Následující program je dobrý začátek pro hledání uhlí. Kope dolů, dokud nenajde vrstvu uhlí, a pak kope na východ a na západ v naději, že najde další uhlí.

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
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2
}
#SETUP
move(North)
move(East)
move(East)
#CODE
while get_ground_type() != Grounds.Coal:
    dig()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

---

[Statistiky](docs/stats.md)      [Těžba](docs/unlocks/mining.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
