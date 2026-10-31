[<- Fer](docs/unlocks/iron.md) <right>[Champignon ->](docs/unlocks/mushroom.md)
---
# Quartz
En continuant après les filons de fer dans `Grounds.Rock`, tu trouves du quartz dans la partie basse de la couche rocheuse et dans la `Grounds.Dirt` dure située dessous (vérifie la dureté avec `get_hardness()` du déblocage [Sens souterrains](docs/unlocks/underground_senses.md)).

L’extrait de code suivant traverse la terre et s’enfonce dans la couche rocheuse. Là, il prospecte le quartz en continu tout en creusant, jusqu’à ce que la distance soit inférieure à 2. Pour finir, il affiche la distance de prospection obtenue.
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
# Creuser jusqu’à la couche rocheuse
while get_ground_type() != Grounds.Rock:
    dig()

# Continuer à creuser jusqu’à ce qu’un filon de quartz soit proche
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# Afficher la distance finale jusqu’au filon
print(prospect_quartz())
}}

## Structure des filons
Le quartz pousse en filons en forme d’aiguilles qui forment des colonnes verticales, ce qui les rend assez difficiles à trouver au hasard.

## Prospection du quartz
Heureusement, nous pouvons utiliser notre fer et le tordre pour fabriquer une sorte de baguette de sourcier qui facilite la localisation de ces filons de quartz. La commande correspondante est `prospect_quartz()`.

`prospect_quartz()` fonctionne différemment de `prospect_iron()`. Au lieu de renvoyer la direction dans laquelle le drone doit se déplacer pour s’approcher du minerai de fer le plus proche, elle renvoie la distance 3D exacte entre le bloc de quartz le plus proche et le drone (distance euclidienne).

Exécuter `prospect_quartz()` coûte 1 fer : mieux vaut donc utiliser cette commande avec parcimonie.

Si `prospect_quartz()` ne trouve aucun quartz à proximité, ou si tu n’as pas assez de fer pour effectuer la recherche, elle renvoie `None`.

## Stratégie
<spoiler=afficher l’indice>Tu peux prospecter et te déplacer à plusieurs reprises pour observer comment la distance change. Sur une surface plane, chercher à réduire la distance au minimum peut te placer au-dessus d’un filon de quartz. Tu peux utiliser une stratégie proche de la recherche dichotomique pour réduire au minimum le nombre d’appels à `prospect_quartz()` et la quantité de fer qu’ils consomment.

Des stratégies plus poussées peuvent utiliser la géométrie 2D pour trouver l’intersection de deux cercles ou plus. Tu peux aussi choisir la voie difficile et faire une trilatération complète, pour intersecter trois sphères et trouver la position 3D exacte du filon.

Note que pour calculer une racine carrée, tu peux utiliser l’opérateur d’exposant : par exemple, pour obtenir la racine carrée de 16, utilise `16**0.5`. Il n’existe aucune fonction mathématique intégrée pour la trigonométrie ou les vecteurs : tu devras les écrire toi-même.

Note aussi qu’il peut y avoir plusieurs filons à proximité : si tu prends plusieurs mesures proches, elles ne pointent peut-être pas vers le même filon.</spoiler>

---

[Statistiques](docs/stats.md)      [Exploitation minière](docs/unlocks/mining.md)      [Sens souterrains](docs/unlocks/underground_senses.md)      [Variables](docs/scripting/variables.md)      [Opérateurs](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
