[<- Ferro](docs/unlocks/iron.md) <right>[Funghi ->](docs/unlocks/mushroom.md)
---
# Quarzo
Proseguendo dalle vene di ferro in `Grounds.Rock`, trovi il quarzo nella parte inferiore dello strato di roccia e nella `Grounds.Dirt` dura sottostante (controlla la durezza con `get_hardness()` dello sblocco [Sensi Sotterranei](docs/unlocks/underground_senses.md)).

Il codice seguente scava oltre la terra e nello strato di roccia. Lì continua a fare prospezioni per il quarzo mentre scava, finché la distanza non è inferiore a 2. Infine stampa la distanza di prospezione raggiunta.
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
    "items": [{"item": "block", "n": 1}, {"item": "iron", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite"]
}
#SETUP
move(East)
move(North)
#CODE
# Scava fino allo strato di roccia
while get_ground_type() != Grounds.Rock:
    dig()

# Continua a scavare finché una vena di quarzo non è vicina
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# Stampa la distanza finale dalla vena
print(prospect_quartz())
}}

## Struttura delle Vene
Il quarzo cresce in vene a forma di ago che formano colonne verticali, perciò sono piuttosto difficili da trovare procedendo per tentativi.

## Prospezione del Quarzo
Per fortuna possiamo prendere il ferro e deformarlo fino a ottenere qualcosa di simile a una bacchetta da rabdomante, così da individuare più facilmente le vene di quarzo. Il comando apposito è `prospect_quartz()`.

`prospect_quartz()` funziona diversamente da `prospect_iron()`. Invece di restituire la direzione in cui il drone deve muoversi per avvicinarsi al minerale di ferro più vicino, restituisce la distanza 3D esatta tra il blocco di quarzo più vicino e il drone (distanza euclidea).

Eseguire `prospect_quartz()` costa 1 ferro, quindi conviene usare il comando con parsimonia.

Se `prospect_quartz()` non trova quarzo nelle vicinanze oppure non hai abbastanza ferro per eseguire la ricerca, restituisce `None`.

## Strategia
<spoiler=mostra suggerimento>Puoi fare prospezioni e spostarti più volte per osservare come cambia la distanza. Su una superficie piana, cercare di ridurre al minimo la distanza può portarti sopra una vena di quarzo. Puoi usare una strategia simile alla ricerca binaria per ridurre al minimo il numero di chiamate a `prospect_quartz()` e la quantità di ferro che consumano.

Strategie più elaborate possono usare la geometria 2D per trovare l'intersezione tra due o più cerchi, oppure puoi scegliere la via difficile e usare la trilaterazione completa per intersecare tre sfere e trovare la posizione 3D esatta della vena.

Nota che per calcolare una radice quadrata puoi usare l'operatore di potenza: per esempio, per ottenere la radice quadrata di 16, usa `16**0.5`. Non esistono funzioni matematiche integrate per la trigonometria o i vettori: dovrai implementarle da solo.

Nota anche che nelle vicinanze possono esserci più vene, quindi se fai più misurazioni vicine, potrebbero non puntare alla stessa vena.</spoiler>

---

[Statistiche](docs/stats.md)      [Estrazione](docs/unlocks/mining.md)      [Sensi Sotterranei](docs/unlocks/underground_senses.md)      [Variabili](docs/scripting/variables.md)      [Operatori](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
