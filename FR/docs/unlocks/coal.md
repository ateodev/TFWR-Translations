[<- Exploitation minière](docs/unlocks/mining.md) <right>[Fer ->](docs/unlocks/iron.md)
<right>[Saut ->](docs/unlocks/jump.md)
---
# Charbon

Différents minerais sont cachés sous terre et n’attendent que toi pour être trouvés et extraits. Si tu creuses à travers la surface jusque dans `Grounds.Dirt`, le premier minerai que tu trouves est le charbon.

Ses filons forment des couches horizontales de 1 bloc d’épaisseur que tu dois trouver par hasard en creusant dans la terre. Les blocs de charbon d’une couche sont le plus souvent directement voisins, mais certains peuvent aussi n’être reliés qu’en diagonale.

Tu n’as rien de spécial à faire pour extraire du charbon : exécute simplement `dig()` pendant que le drone se trouve juste au-dessus d’un bloc `Grounds.Coal`. Utilise `get_ground_type()` pour vérifier ce qu’il y a sous le drone et `get_ground_type(direction)` pour vérifier les quatre blocs adjacents.

Note que tu n’obtiens du charbon que pour les blocs de charbon dans lesquels tu creuses directement, pas pour les blocs qui s’effondrent autour du drone. Garde-le en tête quand tu réfléchis à la façon d’extraire le charbon, afin de maximiser les blocs de charbon que tu extrais par rapport à ceux perdus dans les effondrements.

Les mines de charbon grandissent proportionnellement à la taille de la ferme : pense donc à continuer de débloquer [Agrandir](unlocks/expand) pour augmenter la quantité de charbon que tu peux extraire.

Le programme suivant est un bon point de départ pour chercher du charbon. Il creuse vers le bas à la recherche d’une couche, puis creuse à l’est et à l’ouest dans l’espoir d’en trouver davantage.

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

Une stratégie simple, surtout pour les petites fermes, consiste à creuser tous les blocs à la profondeur où tu as trouvé un bloc de charbon. Pour gagner en efficacité, tu peux noter où tu as vu des blocs de charbon grâce à `get_ground_type(direction)` et éviter de perdre du temps à passer sur des blocs de terre. Fais bien attention à ne pas manquer les liaisons en diagonale, que tu rates si tu ne te déplaces que sur des blocs de charbon.

---

[Statistiques](docs/stats.md)      [Exploitation minière](docs/unlocks/mining.md)      [Sens souterrains](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
