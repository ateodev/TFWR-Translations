[<- Těžba](docs/unlocks/mining.md) <right>[Bambus ->](docs/unlocks/bamboo.md)
<right>[Zkamenělé dýně ->](docs/unlocks/petrified_pumpkins.md)
<right>[Perlit a hlína ->](docs/unlocks/special_soils.md)
---
# Rýže

Pod povrchem a vrstvou `Grounds.Dirt` sis možná všiml tenké vrstvy `Grounds.Clay`. Ukazuje se, že tahle úrodná a nasáklá půda je ideální pro sázení sazenic rýže.

Stejně jako u trávy nebo keřů můžeš, dokud je dron nad blokem `Grounds.Clay`, pomocí `plant(Entities.Rice)` zasadit sazenice rýže do jílu, pak pomocí `can_harvest()` zkontrolovat, jestli rýže úplně vyrostla, a nakonec pomocí `harvest()` rýži sklidit.

Jakmile zasadíš rýži, půda se změní na `Grounds.Rice_Terrace`, aby rýže měla ideální prostředí k dozrání. Když rýže úplně vyroste, půda vyschne, změní se na `Grounds.Dry_Rice_Terrace` a už se na ni nedá sázet další rýže. Naštěstí je vrstva několik bloků tlustá, takže můžeš blok odstranit pomocí `dig()` a zasadit novou rýži na `Grounds.Clay` pod ním. A když vrstva dojde, můžeš svět vždy vyčistit pomocí `clear()` a prokopat se k nové vrstvě.

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
