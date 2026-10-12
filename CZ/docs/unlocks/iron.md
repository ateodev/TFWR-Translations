[<- Uhlí](docs/unlocks/coal.md) <right>[Křemen ->](docs/unlocks/quartz.md)
<right>[Hledání železa ->](docs/unlocks/prospecting.md)
<right>[Mapa pokladu ->](docs/unlocks/treasure_map.md)
---
# Železo

V kamenné vrstvě pod jílem jsi objevil železné žíly.

Železné žíly jsou zpočátku malé a k jejich nalezení budeš potřebovat trochu štěstí. S vyššími úrovněmi tohoto odemčení roste maximální velikost žíly. Pro spolehlivější způsob hledání železa se podívej i na odemčení hledání rudy.

Železná žíla je vždy souvislá, bez úhlopříčných skoků. Když najdeš kus železa, hledej další pod ním nebo vedle něj, abys posbíral celou žílu.

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
