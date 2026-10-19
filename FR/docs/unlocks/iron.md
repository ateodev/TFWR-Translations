[<- Charbon](docs/unlocks/coal.md) <right>[Quartz ->](docs/unlocks/quartz.md)
<right>[Prospection du fer ->](docs/unlocks/prospecting.md)
<right>[Carte au trésor ->](docs/unlocks/treasure_map.md)
---
# Fer

Après avoir trouvé du charbon dans `Grounds.Dirt`, tu peux creuser plus profond, au-delà de la couche de `Grounds.Clay` et jusque dans `Grounds.Rock`, pour trouver du fer.

Contrairement aux filons de charbon, les filons de fer s’étendent aussi verticalement. Mais tous les blocs de fer d’un filon sont toujours directement voisins, les blocs ne sont jamais reliés uniquement en diagonale.

Les filons de fer sont toutefois petits au début et il te faudra un peu de chance pour les trouver. Continuer à débloquer le fer augmente la taille maximale des filons et les rend un peu plus faciles à trouver par hasard. Mais pour les trouver de façon fiable, tu devrais débloquer la [prospection du fer](docs/unlocks/prospecting.md).

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
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#SETUP
jump(Unlocks.Iron)
#CODE
for i in range(4):
    dig()
do_a_flip()
}}

---

[Statistiques](docs/stats.md)      [Exploitation minière](docs/unlocks/mining.md)      [Prospection du fer](docs/unlocks/prospecting.md)      [Sens souterrains](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
