[<- Rýže](docs/unlocks/rice.md) <right>[Barevné bloky ->](docs/unlocks/debug_place.md)
<right>[Pyramidy ->](docs/unlocks/pyramid.md)
---
# Bambus
Bambus je rostlina, která roste vzhůru. Tvůj dron z něj bude muset pravidelně otrhávat hnědé plody, aby mohl dál růst. K tomu nám poslouží nově odemčený příkaz `hover`.

Bambus se musí sázet na zoranou půdu (`Grounds.Soil`) a jeho zasazení stojí rýži.

Následující kód zasadí bambus a počká, až doroste k prvnímu plodu.
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
move(East) # odleť pryč, aby bambus mohl růst
}}

## Plody
Bambus roste přesně o 1 blok za sekundu.

Každých pár bloků bambus vytvoří plod. Když se to stane, bambus přestane růst a budeš do něj muset s dronem vletět, abys plod zničil. Bambus může růst vzhůru až do svého třetího plodu, potom už výš neroste, ani když ho otrháš.

Abys plody otrhal, musíš se nejdřív pomocí `hover` dostat do správné výšky. Pak se pomocí `move` přesuň do plodu, čímž ho otrháš, a pomocí `move` zase odleť, aby bambus mohl dál růst.

Pomocí `measure()` na bambusu zjistíš, v jaké výšce se objeví další plod. `measure()` počítá od `0`, takže `hover(measure())` dostane tvůj dron do výšky, kde bude plod.

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
hover(measure()) # vznes se tak, aby byl dron vedle plodu

move(East) # odleť a počkej, až vyroste
for i in range(3):
    do_a_flip()

move(West) # otrhej plod
move(East) # zase odleť
}}

## Vznášení
Příkaz `hover` přijímá jeden argument, výšku, ve které se má dron vznášet. Je to číslo od `0` do `18`. Výchozí výška vznášení dronu je `1`. `hover` se nemůže posunout dolů do pevných entit, takže pokud je tvůj dron už nad bambusem, nedostaneš se do něj voláním `hover(0)`.

`hover` vrací `True`, pokud se dron úspěšně dostal do zadané výšky, jinak vrací `False`.

Navíc existuje příkaz `get_hover`, který vrací aktuální výšku vznášení dronu.

Pokud během vznášení použiješ `dig`, `harvest` nebo `plant`, dron se vrátí do výchozí výšky vznášení (`1`).

A nakonec, vznášení nemá vliv na `get_pos_z()`. Tato funkce vždy vrací pozici z bloku pod dronem.

## Sklizeň bambusu
Sice můžeš použít `harvest()`, ale doporučený způsob sklizně bambusových polí je vletět do bambusu s dronem ve výšce vznášení `0` (`hover(0)`). Tím sklidíš celou rostlinu najednou.

Pokud chceš bambus sklidit, aniž bys ho zničil, můžeš do něj pomocí `move` vletět v libovolné výšce, například `hover(3)`. Tím sklidíš všechny kusy bambusu od této výšky nahoru, ale bambus zůstane naživu. Bambusu, který byl takto částečně sklizen, znovu narostou plody, takže je budeš muset znovu otrhat.

V obou případech se tvůj výnos rovná druhé mocnině počtu zničených kusů bambusu, takže čím vyšší bambus, tím větší výnos.

---

[Statistiky](docs/stats.md)      [For Loop](docs/scripting/for.md)      [Proměnné](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Funkce](docs/scripting/functions.md)      [Rýže](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
