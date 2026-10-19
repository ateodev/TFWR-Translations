[<- Eisen](docs/unlocks/iron.md)
---
# Schatzkarte

Legenden erzählen von einem schwer auffindbaren Schatz, den ein längst verstorbener, vergesslicher Pirat versteckt haben soll – oder so ähnlich. Was, wenn er den Weg zum Schatz auf einer Karte eingezeichnet und diese dann verloren hat? Vielleicht ließ er die Karte fallen, als ihn ein Lavafluss in die Enge trieb, und sie blieb unter einer Basaltschicht erhalten. Wenn man den Basalt misst, könnte man etwas herausfinden.

<spoiler=Erzähl mir mehr>
Halte nach einer Schicht aus `Grounds.Basalt` Ausschau. Versuche, den Basalt zu messen, und sieh nach, was er dir verrät. Der Hinweis könnte dich zur Schatzkarte führen. Wenn du die Karte misst, erhältst du bestimmt den Weg zum Schatz – doch kannst du ihre Anweisungen auch entschlüsseln?
</spoiler>

<spoiler=Sag mir einfach, wie es geht>
Also gut: Finde die Schicht aus `Grounds.Basalt` und den Block `Grounds.Treasure_Map` direkt darunter. Du kannst den Basalt mit `measure()` messen, um die `(x, y)`-Position des darunterliegenden Kartenblocks zu erhalten.

Rufe `measure()` auf dem Kartenblock auf, um den Weg zum Schatz als Zeichenfolge aus Richtungsbuchstaben zu erhalten. N, E, S und W stehen jeweils für `North`, `East`, `South` und `West`, während D für „Down“ oder „Dig“ steht. Diese Buchstaben beschreiben einen Weg aus `Grounds.Treasure_Path`-Blöcken, der zum Schatz führt.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 6},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "hay", "n": 100}, {"item": "iron", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "digging_speed": 10,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 3,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron"]
}

#SETUP
jump(Unlocks.Treasure_Map)
#CODE
while get_ground_type() != Grounds.Basalt:
    dig()

do_a_flip()
map_pos = measure()

while get_pos_x() < map_pos[0]:
    move(East)
while get_pos_y() < map_pos[1]:
    move(North)

while get_ground_type() != Grounds.Treasure_Map:
    dig()

do_a_flip()
instructions = measure()
dig()
}}

Mit einer `for`-Schleife kannst du die Zeichenfolge Buchstabe für Buchstabe verarbeiten:
```
path = measure()
for letter in path:
    do_something(letter)
```

Die Drohne, die sich bis zum Schatzkartenblock durchgräbt, muss auch den Schatz finden. Sie muss sich die ganze Zeit auf `Grounds.Treasure_Path`-Blöcken befinden. Wenn sie sich auf einen anderen Untergrund bewegt, bricht der Pfad zusammen und der Schatz ist verloren.

Am Ende des Pfades befindet sich ein `Grounds.Treasure_Goal`-Block. Wenn die Drohne den Pfad nicht verlassen hat, erscheint darauf eine `Entities.Underground_Treasure`. Die Drohne kann die Truhe mit `harvest()` ernten und ihr Gold einsammeln.

Die Goldmenge ist proportional zur Länge des Schatzpfades. Wenn du die Schatzkarten-Freischaltung verbesserst, wird der Pfad tiefer. Verbesserst du Erweitern, erhält er mehr Platz, um sich seitwärts auszubreiten. Beide Verbesserungen verlängern den Schatzpfad und erhöhen die Goldmenge, die du findest.
</spoiler>

---

[Statistiken](docs/stats.md)      [For-Schleife](docs/scripting/for.md)      [Tupel](docs/scripting/tuples.md)      [Unterirdische Sinne](docs/unlocks/underground_senses.md)

[harvest()](functions/harvest)      [move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)
