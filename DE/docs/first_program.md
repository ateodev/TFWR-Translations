[<- Erste Schritte](docs/getting_started.md) <right>[While-Schleife ->](docs/scripting/while.md)
---
# Erstes Programm
## Texteditor
Die gesamte Programmierung erfolgt in Codefenstern. Jedes Codefenster entspricht einer Textdatei, die Code enthält.
<desktop>Du kannst die Datei umbenennen, indem du auf ihren Namen oben im Fenster klickst.</desktop>
<mobile>Du kannst die Datei umbenennen, indem du auf ihren Namen neben den Buttons des Fensters tippst.</mobile>

Der Code kann wie in jedem Texteditor bearbeitet werden, solange er nicht ausgeführt wird.
Du kannst das Programm direkt ausführen, indem du auf den grünen Play-Button im Codefenster drückst.
![|x50](PlayButton)

<desktop>Du kannst weitere Codedateien erstellen, indem du den "+"-Button in der oberen rechten Ecke des Bildschirms verwendest.</desktop>
<mobile>Du kannst weitere Codedateien erstellen, indem du den "+"-Button am unteren Bildschirmrand verwendest, oder in der oberen rechten Ecke, wenn du dein Gerät quer hältst.</mobile>
Du kannst ein Fenster an ein anderes Fenster andocken, indem du es darauf ziehst.

Du wirst feststellen, dass, sobald du mit dem Tippen beginnst, ein einfaches Code-Vervollständigungsfenster erscheint.
<desktop>Drücke die Tab-Taste, um die Code-Vervollständigung einzufügen.
Verwende die Pfeiltasten, um durch die Vervollständigungsoptionen zu navigieren.</desktop>
<mobile>Wische auf der Tastatur nach oben oder unten, um durch die Vervollständigungsoptionen zu gehen, und drücke Tab, um die ausgewählte einzufügen.
Auf der Seite [Spieltastatur](docs/keyboard.md) erfährst du, wie du durch Wischen den Cursor bewegst, Text auswählst und Vervollständigungen auswählst.</mobile>

Keine Sorge, wenn dies dein erstes Mal beim Programmieren ist. Die Sprache wird schrittweise freigeschaltet, sodass du nicht von all den Dingen, die du tun kannst, überfordert wirst.
Die Syntax ähnelt auch der von Python, einer der weltweit am weitesten verbreiteten Programmiersprachen, daher ist das Erlernen nicht völlig verschwendet.

Wenn du bereits Python kennst, ist das auch kein Problem, du wirst einfach in der Lage sein, das frühe Spiel schnell zu überspringen, um zu den interessanteren Dingen zu gelangen.

Derzeit sind zwei Drohnenbefehle verfügbar.

`harvest()`

und 

`do_a_flip()`

Dies sind Funktionsaufrufe. Du kannst dir eine Funktion als einen Befehl vorstellen, der ausgeführt werden kann. Du führst ihn mit den `()`-Klammern aus.

Versuche, diese Anweisungen in das Codefenster einzugeben und den Ausführen-Button zu drücken.

Du kannst dir deinen Code als eine Abfolge von Anweisungen vorstellen. Du kannst mehrere Anweisungen hintereinander ausführen, so wie hier:
Drücke auf den Ausführen-Button im eingebetteten Codefenster, um zu sehen, wie der Code ausgeführt wird:

{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
#CODE
do_a_flip()
harvest()
harvest()
}}

## Freischaltungen
Beim Ernten von Gras erhältst du Heu. Mit Heu kannst du Schleifen im Forschungsbaum freischalten. Öffne den Forschungsbaum über den Button <desktop>oben rechts auf dem Bildschirm</desktop><mobile>am unteren Bildschirmrand (oben rechts, wenn du dein Gerät quer hältst)</mobile>.

---

<desktop>[Externer Editor](docs/external_editor.md)      </desktop><mobile>[Spieltastatur](docs/keyboard.md)      </mobile>[Kommentare](docs/scripting/comments.md)      [While-Schleife](docs/scripting/while.md)

[harvest()](functions/harvest)      [do_a_flip()](functions/do_a_flip)
