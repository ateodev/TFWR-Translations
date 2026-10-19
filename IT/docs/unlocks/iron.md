[<- Carbone](docs/unlocks/coal.md) <right>[Quarzo ->](docs/unlocks/quartz.md)
<right>[Prospezione del Ferro ->](docs/unlocks/prospecting.md)
<right>[Mappa del Tesoro ->](docs/unlocks/treasure_map.md)
---
# Ferro

Dopo aver trovato il carbone in `Grounds.Dirt`, puoi scavare più in profondità, oltre lo strato di `Grounds.Clay` e fino a `Grounds.Rock`, per trovare il ferro.

A differenza delle vene di carbone, le vene di ferro si estendono anche in verticale. Però tutti i blocchi di ferro di una vena sono sempre direttamente adiacenti tra loro: i blocchi non sono mai collegati solo in diagonale.

All'inizio però le vene di ferro sono piccole e avrai bisogno di un po' di fortuna per trovarle. Continuare a sbloccare il ferro aumenta la dimensione massima delle vene e le rende un po' più facili da trovare per caso. Ma per trovarle in modo affidabile, dovresti sbloccare la [prospezione del ferro](docs/unlocks/prospecting.md).

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

[Statistiche](docs/stats.md)      [Estrazione](docs/unlocks/mining.md)      [Prospezione del Ferro](docs/unlocks/prospecting.md)      [Sensi Sotterranei](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
