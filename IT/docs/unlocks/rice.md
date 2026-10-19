[<- Estrazione](docs/unlocks/mining.md) <right>[Bambù ->](docs/unlocks/bamboo.md)
<right>[Zucche Pietrificate ->](docs/unlocks/petrified_pumpkins.md)
<right>[Perlite e Terriccio ->](docs/unlocks/special_soils.md)
---
# Riso

Sotto la superficie e lo strato di `Grounds.Dirt` potresti aver notato un sottile strato di `Grounds.Clay`. A quanto pare, questo terreno fertile e impregnato d'acqua è perfetto per piantare le piantine di riso.

Come per l'erba o i cespugli, finché il drone si trova sopra un blocco `Grounds.Clay`, puoi usare `plant(Entities.Rice)` per piantare piantine di riso nell'argilla, poi `can_harvest()` per controllare se il riso è completamente cresciuto e infine `harvest()` per ottenere riso.

Quando pianti il riso, il terreno diventa `Grounds.Rice_Terrace` per offrire al riso l'ambiente perfetto per maturare. Quando il riso è completamente cresciuto, il terreno si secca, diventa `Grounds.Dry_Rice_Terrace` e non può più essere usato per piantare altro riso. Per fortuna lo strato è spesso alcuni blocchi, quindi puoi rimuovere il blocco con `dig()` e piantare nuovo riso sulla `Grounds.Clay` sottostante. E se lo strato finisce, puoi sempre usare `clear()` sul mondo e scavare fino a uno strato nuovo.

Il codice seguente potrebbe esserti utile per scavare verso il basso finché non trovi l'argilla.

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

[Statistiche](docs/stats.md)      [Estrazione](docs/unlocks/mining.md)      [Sensi Sotterranei](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [Ciclo For](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
