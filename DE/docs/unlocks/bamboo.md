[<- Reis](docs/unlocks/rice.md) <right>[Farbige Blöcke ->](docs/unlocks/debug_place.md)
<right>[Pyramiden ->](docs/unlocks/pyramid.md)
---
# Bambus
Bambus ist eine Pflanze, die nach oben wächst. Deine Drohne muss regelmäßig seine braunen Früchte pflücken, damit er weiterwachsen kann. Das gelingt mit dem neu freigeschalteten Befehl `hover`.

Bambus muss auf gepflügtem Boden (`Grounds.Soil`) gepflanzt werden, und das Pflanzen kostet Reis.

Der folgende Code pflanzt Bambus und wartet, bis er bis zu seiner ersten Frucht gewachsen ist.
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
move(East) # wegbewegen, damit der Bambus wachsen kann
}}

## Früchte
Bambus wächst genau 1 Block pro Sekunde.

Alle paar Blöcke bildet der Bambus Früchte. Dann hört er auf zu wachsen, und du musst mit deiner Drohne in ihn hineinfliegen, um die Frucht zu zerstören.

Um Früchte zu pflücken, musst du zuerst mit `hover` auf die richtige Höhe schweben. Dann bewegst du dich mit `move` in die Frucht hinein, um sie zu pflücken, und mit `move` wieder weg, damit der Bambus weiterwachsen kann.

Mit `measure()` kannst du am Bambus prüfen, in welcher Höhe die nächste Frucht erscheint. `measure()` beginnt bei `0` zu zählen, daher bringt `hover(measure())` deine Drohne genau auf die Höhe, in der die Frucht sein wird.

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
hover(measure()) # so schweben, dass die Drohne neben der Frucht ist

move(East) # wegbewegen und warten, bis er wächst
for i in range(3):
    do_a_flip()

move(West) # Frucht pflücken
move(East) # wieder wegbewegen
}}

## Schweben
Der Befehl `hover` nimmt ein Argument entgegen: die Schwebehöhe, eine Zahl von `0` bis `18`. Die Standard-Schwebehöhe der Drohne ist `1`. `hover` kann sich nicht nach unten in feste Objekte bewegen. Befindet sich deine Drohne also bereits über einem Bambus, kannst du nicht mit `hover(0)` in ihn hineinfliegen.

`hover` gibt `True` zurück, wenn die Drohne erfolgreich auf die angegebene Höhe geschwebt ist, andernfalls `False`.

Außerdem gibt es den Befehl `get_hover`, der die aktuelle Schwebehöhe der Drohne zurückgibt.

Wenn du beim Schweben `dig`, `harvest` oder `plant` verwendest, kehrt die Drohne auf ihre Standard-Schwebehöhe (`1`) zurück.

Und schließlich wird `get_pos_z()` vom Schweben nicht beeinflusst. Es gibt immer die z-Position des Blocks unter der Drohne zurück.

## Bambus ernten
Du könntest zwar `harvest()` verwenden, empfohlen wird aber, Bambusfelder zu ernten, indem du dich mit deiner Drohne auf Schwebehöhe `0` (`hover(0)`) in einen Bambus hineinbewegst. So wird die gesamte Pflanze auf einmal geerntet.

Wenn du den Bambus ernten möchtest, ohne ihn zu zerstören, kannst du dich in jeder beliebigen Höhe mit `move` in ihn hineinbewegen, zum Beispiel nach `hover(3)`. Dadurch werden alle Bambusstücke ab dieser Höhe aufwärts geerntet, der Bambus bleibt aber am Leben. Ein auf diese Weise teilweise geernteter Bambus bildet seine Früchte neu, du musst sie also erneut pflücken.

In beiden Fällen entspricht dein Ertrag dem Quadrat der Anzahl zerstörter Bambusstücke. Je höher die Bambuspflanze, desto besser also dein Ertrag.

---

[Statistiken](docs/stats.md)      [For-Schleife](docs/scripting/for.md)      [Variablen](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Funktionen](docs/scripting/functions.md)      [Reis](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
