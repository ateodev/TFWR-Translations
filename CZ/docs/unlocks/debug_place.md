[<- Bambus](docs/unlocks/bamboo.md)
---
# Barevné bloky
Jak už možná víš, pomocí `place()` může dron položit blok. Toto odemčení přidává tři barevné bloky, které se vizuálně odlišují od svého okolí: `Grounds.Block_Red`, `Grounds.Block_Green` a `Grounds.Block_Blue`.

Barevné bloky můžeš použít k označení věcí nebo k vytváření pěkných vzorů.

Jak položit nové bloky:
{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 10},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "block", "n": 100}],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 5,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"],
    "starting_chunk": 2
}
#SETUP
move(East)
move(North)
#CODE
place(Grounds.Block_Green)
move(East)

place(Grounds.Block_Blue)
move(East)

place(Grounds.Block_Green)
move(North)

place(Grounds.Block_Blue)
move(North)

place(Grounds.Block_Green)
move(West)

place(Grounds.Block_Blue)
move(West)

place(Grounds.Block_Green)
move(South)

place(Grounds.Block_Blue)
move(East)

place(Grounds.Block_Red)
place(Grounds.Block_Red)

do_a_flip()
}}

## Výškový limit pokládání
Výška, do které můžeš pokládat bloky, je omezená, a to přibližně tam, kde bloky při úplném oddálení začínají přecházet do černé. Závisí na průměrné hloubce odkrytých bloků, takže pokud farmu stavíš rovnoměrně, tomuto limitu se vyhneš.

---

[Debug](docs/scripting/debug.md)      [Debug 2](docs/unlocks/debug2.md)      [Bambus](docs/unlocks/bamboo.md)

[place()](functions/place)
