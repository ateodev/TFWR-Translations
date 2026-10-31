[<- Kohle](docs/unlocks/coal.md)
---
# Springen
Deine Drohne hat den Befehl `jump()` freigeschaltet. Du verwendest ihn, indem du ihm eine Freischaltung als Argument übergibst, beispielsweise `Unlocks.Iron`.

Mit diesem Befehl kannst du bestimmte Ressourcen anvisieren, die im Boden verborgen sind, und sofort zu ihnen hinunterspringen. Das ist besonders beim Debuggen praktisch oder wenn du zu einer Erzader springen möchtest, die du kurz zuvor verpasst hast.

Nach dem Sprung sollte sich die anvisierte Ressource höchstens 3 Blöcke unter der obersten Blockoberfläche befinden. `jump()` kann pro Programmausführung nur einmal verwendet werden, weitere Sprungversuche führen zu einem Fehler.

Das folgende Beispiel springt hinunter zum [Reis](docs/unlocks/rice.md), findet die Tonschicht und pflanzt eine Reihe Reisterrassen:
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
    "items": [{"item": "hay", "n": 10}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms"],
    "starting_chunk": 0
}
#CODE
# Nahe an die Reis-Ressource springen
jump(Unlocks.Rice)

# Eine Reihe Reisterrassen pflanzen
for i in range(get_world_size()):
    # Der Sprung ist nicht exakt, die letzten Blöcke weggraben
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## Kompatible Freischaltungen
`jump()` funktioniert nur mit den folgenden Bergbau-Freischaltungen:
- Coal
- Iron
- Quartz
- Rice
- Petrified_Pumpkins
- Special_Soils
- Pyramid
- Treasure_Map
- Mushrooms
- Dynamite

---

[jump()](functions/jump)
