[<- Riso](docs/unlocks/rice.md) <right>[Blocchi Colorati ->](docs/unlocks/debug_place.md)
<right>[Piramidi ->](docs/unlocks/pyramid.md)
---
# Bambù
Il bambù è una pianta che cresce verso l'alto. Il drone dovrà raccoglierne regolarmente i frutti marroni perché possa continuare a crescere. Possiamo farlo con il comando appena sbloccato `hover`.

Il bambù va piantato su terreno arato (`Grounds.Soil`) e piantarlo costa riso.

Il codice seguente pianta un bambù e aspetta che cresca fino al suo primo frutto.
{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
move(East) # spostati così il bambù può crescere
}}

## Frutti
Il bambù cresce esattamente di 1 blocco al secondo.

Il bambù produce frutti ogni pochi blocchi. Quando succede, il bambù smette di crescere e dovrai volarci dentro con il drone per distruggere il frutto.

Per raccogliere i frutti, devi prima portarti con `hover` all'altezza giusta. Poi usa `move` per entrare nel frutto e raccoglierlo, e di nuovo `move` per allontanarti, così il bambù può continuare a crescere.

Puoi usare `measure()` sul bambù per sapere a quale altezza comparirà il prossimo frutto. `measure()` inizia a contare da `0`, quindi `hover(measure())` porterà il drone all'altezza in cui si troverà il frutto.

{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
hover(measure()) # librati in modo che il drone sia accanto al frutto

move(East) # spostati e aspetta che cresca
for i in range(3):
    do_a_flip()

move(West) # raccogli il frutto
move(East) # spostati di nuovo
}}

## Librarsi
Il comando `hover` accetta un argomento, l'altezza a cui librarsi, che è un numero da `0` a `18`. L'altezza predefinita a cui si libra il drone è `1`. `hover` non può scendere dentro entità solide, quindi se il drone si trova già sopra un bambù, non puoi entrarci eseguendo `hover(0)`.

`hover` restituisce `True` se il drone è riuscito a librarsi all'altezza indicata, e `False` altrimenti.

Inoltre c'è il comando `get_hover`, che restituisce l'altezza attuale a cui si libra il drone.

Se usi `dig`, `harvest` o `plant` mentre il drone si libra, tornerà alla sua altezza predefinita (`1`).

Infine, `get_pos_z()` non è influenzato dal librarsi. Restituisce sempre la posizione z del blocco sotto il drone.

## Raccogliere il Bambù
Anche se potresti usare `harvest()`, il modo consigliato per raccogliere i campi di bambù è entrare in un bambù con il drone ad altezza `0` (`hover(0)`). In questo modo raccogli l'intera pianta in una volta.

Se vuoi raccogliere il bambù senza distruggerlo, puoi entrarci con `move` a qualsiasi altezza, per esempio `hover(3)`. Così raccogli tutti i pezzi di bambù da quell'altezza in su, ma il bambù resta in vita. Un bambù raccolto parzialmente in questo modo farà ricrescere i suoi frutti, quindi dovrai raccoglierli di nuovo.

In entrambi i casi, la resa è uguale al quadrato del numero di pezzi di bambù distrutti, quindi più alta è la pianta di bambù, migliore sarà la resa.

---

[Statistiche](docs/stats.md)      [Ciclo For](docs/scripting/for.md)      [Variabili](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Funzioni](docs/scripting/functions.md)      [Riso](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
