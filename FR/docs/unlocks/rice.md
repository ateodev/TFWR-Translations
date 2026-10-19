[<- Exploitation minière](docs/unlocks/mining.md) <right>[Bambou ->](docs/unlocks/bamboo.md)
<right>[Citrouilles pétrifiées ->](docs/unlocks/petrified_pumpkins.md)
<right>[Perlite et terreau ->](docs/unlocks/special_soils.md)
---
# Riz

Sous la surface et la couche de `Grounds.Dirt`, tu as peut-être remarqué une fine couche de `Grounds.Clay`. Il s’avère que ce sol fertile et gorgé d’eau est idéal pour planter des pousses de riz.

Comme pour l’herbe ou les buissons, tant que ton drone se trouve au-dessus d’un bloc `Grounds.Clay`, tu peux utiliser `plant(Entities.Rice)` pour planter des pousses de riz dans l’argile, puis `can_harvest()` pour vérifier si le riz a fini de pousser, et enfin `harvest()` pour récolter du riz.

Dès que tu plantes du riz, le sol devient `Grounds.Rice_Terrace` pour offrir au riz l’environnement idéal pour mûrir. Une fois le riz arrivé à maturité, le sol s’assèche, devient `Grounds.Dry_Rice_Terrace` et ne peut plus servir à planter du riz. Heureusement, la couche fait plusieurs blocs d’épaisseur : tu peux donc retirer le bloc avec `dig()` et planter du nouveau riz sur la `Grounds.Clay` en dessous. Et si la couche est épuisée, tu peux toujours utiliser `clear()` sur le monde et creuser jusqu’à une couche neuve.

Le code suivant peut t’aider à creuser jusqu’à trouver de l’argile.

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 8,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(East)
#CODE
while get_ground_type() != Grounds.Clay:
    dig()
plant(Entities.Rice)
move(North)
do_a_flip()
}}

---

[Statistiques](docs/stats.md)      [Exploitation minière](docs/unlocks/mining.md)      [Sens souterrains](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [Boucle for](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
