[<- Charbon](docs/unlocks/coal.md)
---
# Saut

Ton drone a débloqué la commande `jump()`. Pour l’utiliser, passe-lui un déblocage en argument, par exemple `Unlocks.Iron`.

Cette commande te permet de cibler certains déblocages cachés dans le sol et de sauter instantanément jusqu’à eux. Elle est particulièrement utile pour le débogage ou pour revenir à un filon de minerai que tu viens de manquer.

Après le saut, le déblocage ciblé devrait se trouver à 3 blocs au plus sous la surface des blocs supérieurs. `jump()` ne peut être utilisée qu’une seule fois par exécution du programme : toute autre tentative de saut produira une erreur.

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
jump(Unlocks.Rice)

for i in range(get_world_size()):
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## Déblocages compatibles
`jump()` ne fonctionne qu’avec les déblocages miniers suivants :
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
