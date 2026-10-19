[<- Uhlí](docs/unlocks/coal.md) <right>[Křemen ->](docs/unlocks/quartz.md)
<right>[Hledání železa ->](docs/unlocks/prospecting.md)
<right>[Mapa pokladu ->](docs/unlocks/treasure_map.md)
---
# Železo

Až najdeš uhlí v `Grounds.Dirt`, můžeš kopat hlouběji, skrz vrstvu `Grounds.Clay` až do `Grounds.Rock`, a najít železo.

Na rozdíl od uhelných žil se železné žíly táhnou i svisle. Všechny bloky železa v žíle ale vždy leží přímo vedle sebe, bloky nikdy nejsou spojené jen úhlopříčně.

Železné žíly jsou ale zpočátku malé a k jejich nalezení budeš potřebovat trochu štěstí. Další odemykání železa zvětšuje maximální velikost žil a trochu usnadňuje jejich náhodné nalezení. Abys je ale nacházel spolehlivě, měl bys odemknout [hledání železa](docs/unlocks/prospecting.md).

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

[Statistiky](docs/stats.md)      [Těžba](docs/unlocks/mining.md)      [Hledání železa](docs/unlocks/prospecting.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
