[<- Riz](docs/unlocks/rice.md) <right>[Blocs colorés ->](docs/unlocks/debug_place.md)
<right>[Pyramides ->](docs/unlocks/pyramid.md)
---
# Bambou
Le bambou est une plante qui pousse vers le haut. Ton drone devra cueillir régulièrement ses fruits bruns pour qu’il puisse continuer à pousser. C’est possible grâce à la nouvelle commande `hover`.

Le bambou doit être planté sur un sol labouré (`Grounds.Soil`) et planter du bambou coûte du riz.

Le code suivant plante du bambou et attend qu’il pousse jusqu’à son premier fruit.
{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
move(East) # s’éloigner pour que le bambou puisse pousser
}}

## Fruits
Le bambou pousse d’exactement 1 bloc par seconde.

Tous les quelques blocs, le bambou produit des fruits. Il arrête alors de pousser et tu dois voler dedans avec ton drone pour détruire le fruit.

Pour cueillir un fruit, utilise d’abord `hover` pour atteindre la bonne hauteur. Ensuite, utilise `move` pour entrer dans le fruit et le cueillir, puis `move` à nouveau pour t’éloigner afin que le bambou puisse continuer à pousser.

Tu peux utiliser `measure()` sur le bambou pour savoir à quelle hauteur apparaîtra le prochain fruit. `measure()` commence à compter à `0`, donc `hover(measure())` amène ton drone à la hauteur où se trouvera le fruit.

{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
hover(measure()) # voler à la hauteur du futur fruit

move(East) # s’éloigner et attendre qu’il pousse
for i in range(3):
    do_a_flip()

move(West) # cueillir le fruit
move(East) # s’éloigner à nouveau
}}

## Vol stationnaire
La commande `hover` prend un argument, la hauteur de vol, qui est un nombre de `0` à `18`. La hauteur de vol par défaut du drone est `1`. `hover` ne peut pas descendre dans des entités solides : si ton drone se trouve déjà au-dessus d’un bambou, tu ne peux pas y entrer en exécutant `hover(0)`.

`hover` renvoie `True` si le drone a bien atteint la hauteur indiquée, sinon `False`.

Il existe aussi la commande `get_hover`, qui renvoie la hauteur de vol actuelle du drone.

Si tu utilises `dig`, `harvest` ou `plant` en vol, le drone revient à sa hauteur de vol par défaut (`1`).

Enfin, `get_pos_z()` n’est pas affecté par le vol. Il renvoie toujours la position z du bloc sous le drone.

## Récolter le bambou
Tu pourrais utiliser `harvest()`, mais la méthode recommandée pour récolter un champ de bambou est d’entrer dans un bambou avec ton drone à la hauteur de vol `0` (`hover(0)`). Cela récolte toute la plante d’un coup.

Si tu veux récolter le bambou sans le détruire, tu peux y entrer avec `move` à n’importe quelle hauteur, par exemple `hover(3)`. Cela récolte tous les morceaux de bambou à partir de cette hauteur, mais garde le bambou en vie. Un bambou partiellement récolté de cette façon produira de nouveaux fruits, que tu devras donc cueillir à nouveau.

Dans les deux cas, ton rendement est égal au carré du nombre de morceaux de bambou détruits : plus le bambou est haut, meilleur est ton rendement.

---

[Statistiques](docs/stats.md)      [Boucle for](docs/scripting/for.md)      [Variables](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Fonctions](docs/scripting/functions.md)      [Riz](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
