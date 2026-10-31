[<- Charbon](docs/unlocks/coal.md)
---
# Saut
Ton drone a débloqué la commande `jump()`. Pour l’utiliser, passe-lui un déblocage en argument, par exemple `Unlocks.Iron`.

Cette commande te permet de cibler certaines ressources cachées dans le sol et de sauter instantanément jusqu’à elles. Elle est particulièrement utile pour le débogage ou pour revenir à un filon de minerai que tu viens de manquer.

Après le saut, la ressource ciblée devrait se trouver à 3 blocs au plus sous la surface des blocs supérieurs. `jump()` ne peut être utilisée qu’une seule fois par exécution du programme : toute autre tentative de saut produira une erreur.

L’exemple suivant saute jusqu’au [riz](docs/unlocks/rice.md), trouve la couche d’argile et plante une rangée de rizières en terrasses :
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
# Sauter près de la ressource de riz
jump(Unlocks.Rice)

# Planter une rangée de rizières en terrasses
for i in range(get_world_size()):
    # Le saut n’est pas exact, creuser les derniers blocs
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
