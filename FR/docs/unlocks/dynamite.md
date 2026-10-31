[<- Champignon](docs/unlocks/mushroom.md) <right>[Foreuse explosive ->](docs/unlocks/explosive_drill.md)
---
# Dynamite
L’explosif révolutionnaire, abandonné par de précédentes expéditions minières. Malheureusement, ta foreuse est parfaite pour faire exploser la dynamite et pulvériser tous les blocs alentour. La dynamite récupérée peut être utilisée avec `use_item(Items.Dynamite)` et explose immédiatement sous le drone.

Pour extraire la dynamite sans danger, trouve une couche de `Grounds.Dynamite` directement suivie d’une couche de `Grounds.Soot` en dessous. La couche de dynamite du dessus a un peu vieilli : certains de ses blocs peuvent être forés sans danger. Mais certains blocs de dynamite sont encore actifs et exploseront si tu les fores.

Cet exemple fore dans la dynamite et tout autour du point de forage initial, ce qui révèle la couche de suie et ses nombres, et affiche la mesure :
{{codeexample 
{
    "camera_position": {"x": -3, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 800, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 7, "y": 7},
    "execution_speed": 2,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 6,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(3):
    move(East)
    move(North)
#CODE
# Creuser jusqu’à la couche de suie, à travers la couche de dynamite du dessus
while get_ground_type() != Grounds.Soot:
    dig()

# Liste de directions qui font tourner le drone en cercle
circle_directions = [
    East, South, West, West, 
    North, North, East, East
]
for dir in circle_directions:
    move(dir)
    dig()
    print(measure()) # Le nombre sur le bloc de suie
}}

## Démineur de dynamite
Peux-tu trouver et forer tous les blocs de dynamite inertes en ne laissant que les blocs actifs ? Chaque bloc actif entouré uniquement d’autres blocs actifs ou de blocs de suie te rapportera de la dynamite supplémentaire lorsque la strate de dynamite disparaîtra.

Heureusement, les blocs de suie situés dessous vont t’aider : ils détectent le nombre de blocs de dynamite voisins contenant de la dynamite active. Ils ne t’indiquent pas lesquels sont actifs, seulement leur nombre total. Tu dois donc combiner les relevés de plusieurs blocs de suie et résoudre le problème toi-même.

Appeler `measure()` sur un bloc de suie renvoie le nombre de mines présentes dans les huit cases voisines de la strate de dynamite supérieure. Ce nombre peut aller de `0` (aucune mine active) à `8` (chaque case voisine contient une mine active).

Le premier bloc foré dans la strate de dynamite est toujours inerte. Chaque bloc de dynamite extrait rapporte un peu de dynamite. Lorsque la strate est détruite, soit après avoir extrait tous les blocs inertes, soit après avoir foré par mégarde de la dynamite active, tu reçois aussi une quantité de dynamite égale au carré du nombre de blocs actifs entièrement dégagés.

## Structure des strates
Le nombre de mines actives dans la strate de dynamite, et donc la difficulté pour les trouver, augmente avec la profondeur. Le nombre total de mines augmente avec la taille de la ferme, et donc aussi le rendement maximal possible quand tu nettoies une strate de dynamite.

Améliore la dynamite pour augmenter le rendement obtenu en forant les blocs de dynamite et en dégageant entièrement les blocs actifs. L’amélioration augmente également l’énergie des explosions de dynamite de 30 %.

## Détecter la réussite et l’échec
Si tu fores de la dynamite active, les deux strates explosent. Tu peux le vérifier avec `get_ground_type()` après avoir foré dans `Grounds.Dynamite`. Si le sol n’est pas `Grounds.Soot`, tu n’as pas résolu l’énigme. En revanche, si le dernier bloc de dynamite inerte est extrait, tous les blocs de dynamite disparaissent et tu obtiens le rendement maximal de l’énigme. La strate de suie reste en place, mais `measure()` renvoie `None`, ce qui indique que l’énigme a été résolue.

`# Forer un bloc de dynamite et vérifier l’état de l’énigme
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # Dynamite active forée, énigme échouée
        return False
    elif measure() == None:
        # Dernier bloc inerte extrait, énigme résolue
        return True
    else:
        # Un nombre a été mesuré, énigme toujours en cours
        return None
`

## Stratégie
<spoiler=indice>
Le code ci-dessous fore dans la strate de dynamite et cherche les blocs de suie dont la mesure vaut `0`. Pour chacun de ces blocs, il fore tous les blocs de dynamite qui l’entourent :
{{codeexample 
{
    "camera_position": {"x": -5, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 800, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 7, "y": 7},
    "execution_speed": 4,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 6,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(3):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [
    East, South, West, West, North,
    North, East, East, South, West
]
# Faire le tour du bloc foré au départ
for dir in circle_directions:
    # Si la suie mesure 0,
    # tous les blocs de dynamite voisins sont inertes
    if get_ground_type() == Grounds.Soot and measure() == 0:
        # Refaire un tour par les blocs voisins
        for dir2 in circle_directions:
            move(dir2)
            # Extraire le bloc de dynamite inerte
            while get_ground_type() != Grounds.Soot:
                dig()
    move(dir)
}}
</spoiler>

---

[Statistiques](docs/stats.md)      [Sens souterrains](docs/unlocks/underground_senses.md)      [Dictionnaires](docs/scripting/dicts.md)      [Sets](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
