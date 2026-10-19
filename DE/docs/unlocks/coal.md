[<- Bergbau](docs/unlocks/mining.md) <right>[Eisen ->](docs/unlocks/iron.md)
<right>[Springen ->](docs/unlocks/jump.md)
---
# Kohle

Unter der Erde liegen verschiedene Erze verborgen und warten darauf, dass du sie findest und ausgräbst. Wenn du dich durch die Oberfläche in `Grounds.Dirt` gräbst, ist Kohle das erste Erz, das du findest.

Ihre Adern bilden waagerechte, 1 Block dicke Schichten, die du beim Graben durch die Erde zufällig finden musst. Die Kohleblöcke einer Schicht liegen meist direkt nebeneinander, manche sind aber auch nur diagonal miteinander verbunden.

Um Kohle abzubauen, musst du nichts Besonderes tun. Führe einfach `dig()` aus, während die Drohne direkt auf einem `Grounds.Coal`-Block steht. Mit `get_ground_type()` prüfst du, was unter der Drohne liegt, und mit `get_ground_type(direction)` die vier angrenzenden Blöcke.

Beachte, dass du nur für die Kohleblöcke Kohle bekommst, in die du direkt gräbst, nicht für Blöcke, die rund um die Drohne einstürzen. Denk daran, wenn du überlegst, wie du Kohle abbaust, damit du möglichst viele Kohleblöcke abbaust und möglichst wenige durch Einstürze verlierst.

Die Kohleminen wachsen proportional zur Größe der Farm. Es kann sich also lohnen, [Erweitern](unlocks/expand) weiter freizuschalten, um mehr Kohle abbauen zu können.

Das folgende Programm ist ein guter Ausgangspunkt für die Kohlesuche. Es gräbt nach unten, bis es eine Kohleschicht findet, und gräbt dann östlich und westlich davon weiter, um hoffentlich noch mehr Kohle zu entdecken.

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

Eine einfache Strategie, vor allem bei kleineren Farmen, ist es, einfach alle Blöcke in der Tiefe auszugraben, in der du einen Kohleblock gefunden hast. Effizienter wird es, wenn du dir mit `get_ground_type(direction)` merkst, wo du Kohleblöcke gesehen hast, und keine Zeit damit verlierst, über Erdblöcke zu fahren. Achte dabei besonders darauf, die diagonalen Verbindungen nicht zu übersehen, denn die verpasst du, wenn du dich nur über Kohleblöcke bewegst.

---

[Statistiken](docs/stats.md)      [Bergbau](docs/unlocks/mining.md)      [Unterirdische Sinne](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
