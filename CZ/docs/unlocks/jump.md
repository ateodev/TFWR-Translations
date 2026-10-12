[<- Uhlí](docs/unlocks/coal.md)
---
# Skok

Tvůj dron odemkl příkaz `jump()`.

Tento příkaz ti umožňuje zacílit na určitá odemčení a skočit rovnou k nim. Hodí se zejména při ladění nebo pro skok k rudné žíle, kterou jsi nedávno minul. Používá se tak, že mu jako argument předáš odemčení, například `Unlocks.Iron`.

`jump()` funguje jen pro odemčení, která se vyskytují v podzemí, například `jump(Unlocks.Rice)` nebo `jump(Unlocks.Iron)`.

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
    "items": [],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 1,
    "digging_speed": 3,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms"],
    "starting_chunk": 0
}
#CODE
dig()
dig()
dig()
jump(Unlocks.Iron)
do_a_flip()
}}

Není zaručeno, že tě skok přenese přímo k cílovému odemčení, takže se možná budeš muset trochu porozhlédnout, ale je zaručeno, že cíl je poblíž.

`jump()` lze použít jen jednou za běh programu.

---

[jump()](functions/jump)
