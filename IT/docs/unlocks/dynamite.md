[<- Funghi](docs/unlocks/mushroom.md) <right>[Trivella Esplosiva ->](docs/unlocks/explosive_drill.md)
---
# Dinamite

Il rivoluzionario esplosivo lasciato dalle precedenti spedizioni minerarie. Per (s)fortuna, la tua trivella è perfetta per far esplodere la dinamite e spazzare via tutti i blocchi intorno a te.

Per estrarre la dinamite in sicurezza, trova uno strato di `Grounds.Dynamite` seguito direttamente da un altro strato di `Grounds.Soot` sotto di esso. Lo strato di dinamite superiore è ormai vecchio e alcuni dei suoi blocchi possono essere scavati senza pericolo. Alcuni blocchi di dinamite, però, sono ancora attivi ed esploderanno quando li scavi.

{{codeexample 
{
    "camera_position": {"x": -5, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 900, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}],
    "world_size": {"x": 11, "y": 11},
    "execution_speed": 8,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 5,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(5):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [East, South, West, West, North, North, East, East, South, West]
def dig_dynamite_neighbors():
    for dir in circle_directions:
        move(dir)
        while get_ground_type() != Grounds.Soot:
            dig()

while get_ground_type() == Grounds.Soot and measure() == 0:
    dig_dynamite_neighbors()
    move(circle_directions[random() * len(circle_directions)])
}}

Riesci a trovare e scavare tutti i blocchi di dinamite inerti, lasciando solo quelli attivi? Quando lo strato di dinamite scompare, ogni blocco attivo circondato soltanto da altri blocchi attivi o da blocchi di fuliggine ti darà dinamite extra.

Per fortuna i blocchi di fuliggine sottostanti ti aiuteranno: possono rilevare quanti blocchi di dinamite vicini contengono dinamite attiva. Non indicano quali blocchi sono attivi, ma solo il totale, quindi dovrai combinare le misurazioni di più blocchi di fuliggine e dedurlo da solo.

Chiamare `measure()` su un blocco di fuliggine restituisce il numero di mine nelle otto caselle vicine dello strato di dinamite soprastante. Il numero varia da `0` (nessuna mina attiva) a `8` (ogni vicino contiene una mina attiva).

Il primo blocco scavato nello strato di dinamite è sempre inerte. Ogni blocco di dinamite scavato produce un po' di dinamite. Quando lo strato viene distrutto, dopo aver scavato tutti i blocchi inerti oppure colpendo per errore della dinamite attiva, ricevi anche una quantità di dinamite pari al quadrato del numero di blocchi attivi completamente scoperti.

Se scavi nella dinamite attiva, entrambi gli strati esplodono. Puoi verificarlo usando `get_ground_type()` dopo aver scavato in `Grounds.Dynamite`. Se il terreno non è `Grounds.Soot`, non hai risolto l'enigma. Se invece viene scavato l'ultimo blocco di dinamite inerte, tutti i blocchi di dinamite scompaiono e ottieni la resa massima dell'enigma. Lo strato di fuliggine rimane, ma `measure()` restituisce `None`, indicando che l'enigma è stato risolto correttamente.

`# Scava un blocco di dinamite e controlla lo stato dell'enigma
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # Scavata dinamite attiva, enigma fallito
        return False
    elif measure() == None:
        # Scavato l'ultimo blocco inerte, enigma risolto
        return True
    else:
        # Ottenuto un numero dalla misurazione, enigma ancora in corso
        return None
`

Il numero di mine attive nello strato di dinamite, e quindi la difficoltà nel trovarle, aumenta con la profondità. Il numero totale di mine aumenta con le dimensioni della fattoria, e con esso anche la resa massima possibile per aver ripulito uno strato di dinamite.

La dinamite raccolta può essere usata con `use_item(Items.Dynamite)` ed esplode immediatamente sotto il drone.

Potenzia la dinamite per aumentare la resa ottenuta scavando i blocchi di dinamite e scoprendo completamente quelli attivi. Il potenziamento aumenta anche del 30% l'energia delle esplosioni.

---

[Statistiche](docs/stats.md)      [Sensi Sotterranei](docs/unlocks/underground_senses.md)      [Dizionari](docs/scripting/dicts.md)      [Set](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
