[<- Węgiel](docs/unlocks/coal.md) <right>[Kwarc ->](docs/unlocks/quartz.md)
<right>[Poszukiwanie żelaza ->](docs/unlocks/prospecting.md)
<right>[Mapa skarbu ->](docs/unlocks/treasure_map.md)
---
# Żelazo

Po znalezieniu węgla w `Grounds.Dirt` możesz kopać głębiej, przez warstwę `Grounds.Clay` aż do `Grounds.Rock`, aby znaleźć żelazo.

W przeciwieństwie do żył węgla żyły żelaza rozciągają się także pionowo. Ale wszystkie bloki żelaza w żyle zawsze przylegają bezpośrednio do siebie; bloki nigdy nie łączą się wyłącznie po przekątnej.

Żyły żelaza są jednak początkowo małe, a ich znalezienie wymaga odrobiny szczęścia. Dalsze odblokowywanie żelaza zwiększa maksymalny rozmiar żył i sprawia, że trochę łatwiej trafić na nie przypadkiem. Aby jednak znajdować je niezawodnie, odblokuj [poszukiwanie żelaza](docs/unlocks/prospecting.md).

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

[Statystyki](docs/stats.md)      [Górnictwo](docs/unlocks/mining.md)      [Poszukiwanie żelaza](docs/unlocks/prospecting.md)      [Podziemne zmysły](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
