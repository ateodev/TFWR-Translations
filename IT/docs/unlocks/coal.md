[<- Estrazione](docs/unlocks/mining.md) <right>[Ferro ->](docs/unlocks/iron.md)
<right>[Salto ->](docs/unlocks/jump.md)
---
# Carbone

Sottoterra sono nascosti diversi minerali che aspettano solo di essere trovati e scavati. Se scavi attraverso la superficie fino a `Grounds.Dirt`, il primo minerale che trovi è il carbone.

Le sue vene formano strati orizzontali spessi 1 blocco che devi trovare per caso mentre scavi nella terra. I blocchi di carbone di uno strato sono per lo più direttamente adiacenti, ma alcuni possono anche essere collegati solo in diagonale.

Per estrarre il carbone non devi fare nulla di speciale: basta eseguire `dig()` mentre il drone si trova direttamente sopra un blocco `Grounds.Coal`. Usa `get_ground_type()` per controllare cosa c'è sotto il drone e `get_ground_type(direction)` per controllare i quattro blocchi adiacenti.

Nota che ottieni carbone solo per i blocchi di carbone in cui scavi direttamente, non per i blocchi che crollano intorno al drone. Tienilo a mente quando pensi a come estrarre il carbone, così da massimizzare i blocchi di carbone che estrai rispetto a quelli persi nei crolli.

Le miniere di carbone crescono in proporzione alle dimensioni della fattoria, quindi valuta di continuare a sbloccare [Espandi](unlocks/expand) per aumentare la quantità di carbone che puoi estrarre.

Il programma seguente è un buon punto di partenza per trovare il carbone. Scava verso il basso alla ricerca di uno strato di carbone, poi scava a est e a ovest nella speranza di trovarne altro.

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
do_a_flip()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

Una strategia semplice, soprattutto per le fattorie più piccole, è scavare tutti i blocchi alla profondità in cui hai trovato un blocco di carbone. Per essere più efficiente, puoi tenere traccia di dove hai visto blocchi di carbone usando `get_ground_type(direction)` ed evitare di perdere tempo spostandoti sopra blocchi di terra. Dovrai fare molta attenzione a non perdere i collegamenti in diagonale, che ti sfuggono se ti muovi solo sopra blocchi di carbone.

---

[Statistiche](docs/stats.md)      [Estrazione](docs/unlocks/mining.md)      [Sensi Sotterranei](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
