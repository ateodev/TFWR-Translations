[<- Eisen](docs/unlocks/iron.md) <right>[Pilze ->](docs/unlocks/mushroom.md)
---
# Quarz
Weiter unten als die Eisenadern in `Grounds.Rock` findest du Quarz im unteren Teil der Gesteinsschicht und in der harten `Grounds.Dirt` darunter (prüfe die Härte mit `get_hardness()` aus der Freischaltung [Unterirdische Sinne](docs/unlocks/underground_senses.md)).

Der folgende Code gräbt sich durch die Erde bis in die Steinschicht. Dort sucht er beim Graben fortlaufend nach Quarz, bis die Entfernung kleiner als 2 ist. Zum Schluss gibt er die erreichte Entfernung aus.
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
# Bis zur Steinschicht hinuntergraben
while get_ground_type() != Grounds.Rock:
    dig()

# Weitergraben, bis eine Quarzader nah ist
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# Die endgültige Entfernung zur Ader ausgeben
print(prospect_quartz())
}}

## Aderstruktur
Quarz wächst in nadelförmigen Adern, die senkrechte Säulen bilden, wodurch sie durch bloßes Ausprobieren nur schwer zu finden sind.

## Quarzsuche
Zum Glück können wir unser Eisen zu etwas verbiegen, das einer Wünschelrute ähnelt und mit dem wir diese Quarzadern leichter aufspüren können. Der entsprechende Befehl lautet `prospect_quartz()`.

`prospect_quartz()` funktioniert anders als `prospect_iron()`. Statt die Richtung zurückzugeben, in die sich die Drohne bewegen müsste, um zum nächstgelegenen Eisenerz zu gelangen, liefert der Befehl die genaue 3D-Entfernung zwischen dem nächstgelegenen Quarzblock und der Drohne (euklidische Entfernung).

Die Ausführung von `prospect_quartz()` kostet 1 Eisen, daher solltest du den Befehl sparsam einsetzen.

Wenn `prospect_quartz()` keinen Quarz in der Nähe findet oder du nicht genug Eisen für die Suche hast, gibt der Befehl `None` zurück.

## Strategie
<spoiler=zeige Hinweis>Du kannst wiederholt suchen und dich bewegen und dabei beobachten, wie sich die Entfernung ändert. Auf einer ebenen Fläche kann dich der Versuch, die Entfernung zu minimieren, über eine Quarzader bringen. Mit einer Strategie ähnlich der binären Suche kannst du die Anzahl der `prospect_quartz()`-Aufrufe und das dafür verbrauchte Eisen gering halten.

Aufwendigere Strategien bestimmen mit 2D-Geometrie den Schnittpunkt von zwei oder mehr Kreisen. Oder du gehst den schweren Weg und nutzt vollständige Trilateration, um drei Kugeln zu schneiden und die genaue 3D-Position der Ader zu finden.

Für eine Quadratwurzel kannst du den Potenzoperator verwenden. Die Quadratwurzel von 16 erhältst du zum Beispiel mit `16**0.5`. Es gibt keine eingebauten Mathefunktionen für Trigonometrie oder Vektoren, die musst du selbst schreiben. 

Beachte auch, dass in der Nähe mehrere Adern liegen können. Wenn du also mehrere Messungen in der Nähe machst, zeigen sie vielleicht nicht auf dieselbe Ader.</spoiler>

---

[Statistiken](docs/stats.md)      [Bergbau](docs/unlocks/mining.md)      [Unterirdische Sinne](docs/unlocks/underground_senses.md)      [Variablen](docs/scripting/variables.md)      [Operatoren](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
