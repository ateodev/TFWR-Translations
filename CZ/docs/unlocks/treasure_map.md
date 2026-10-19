[<- Železo](docs/unlocks/iron.md)
---
# Mapa pokladu

Legendy vyprávějí o nepolapitelném pokladu, který ukryl dávno mrtvý, zapomnětlivý pirát, nebo tak nějak. Co když cestu k pokladu zapsal na mapu a tu pak ztratil? Možná mapu upustil, když ho zahnala do kouta řeka lávy, a ta se zachovala pod vrstvou čediče. Změření čediče by mohlo něco prozradit.

<spoiler=řekni mi víc>
Hledej vrstvu `Grounds.Basalt`. Zkus čedič změřit a uvidíš, co ti řekne. Nápověda tě může dovést k mapě pokladu a změření mapy ti jistě vrátí cestu k samotnému pokladu – ale dokážeš rozluštit pokyny, které ti mapa dává?
</spoiler>

<spoiler=prostě mi řekni jak>
Dobře, takže takhle: najdi vrstvu `Grounds.Basalt` a blok `Grounds.Treasure_Map` přímo pod ní. Změř čedič pomocí `measure()` a získáš pozici `(x, y)` bloku mapy pod ním.

Zavolej `measure()` na bloku mapy a získáš cestu k pokladu jako řetězec písmen směrů. N, E, S a W znamenají `North`, `East`, `South` a `West`, zatímco D znamená „dolů“ nebo „kopat“. Tato písmena popisují cestu z bloků `Grounds.Treasure_Path`, která vede k pokladu.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 6},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "hay", "n": 100}, {"item": "iron", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "digging_speed": 10,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 3,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron"]
}

#SETUP
jump(Unlocks.Treasure_Map)
#CODE
while get_ground_type() != Grounds.Basalt:
    dig()

do_a_flip()
map_pos = measure()

while get_pos_x() < map_pos[0]:
    move(East)
while get_pos_y() < map_pos[1]:
    move(North)

while get_ground_type() != Grounds.Treasure_Map:
    dig()

do_a_flip()
instructions = measure()
dig()
}}

Pomocí cyklu `for` můžeš řetězec zpracovat písmeno po písmenu:
```
path = measure()
for letter in path:
    do_something(letter)
```

Dron, který kopne do bloku mapy pokladu, je ten, který musí poklad najít. Musí celou dobu zůstat nad bloky `Grounds.Treasure_Path`. Pokud přejde na jinou půdu, cesta se přeruší a poklad bude ztracen.

Na konci cesty je blok `Grounds.Treasure_Goal`. Pokud dron z cesty nesešel, objeví se na něm `Entities.Underground_Treasure`. Dron může truhlu sklidit pomocí `harvest()` a sebrat její zlato.

Množství zlata je úměrné délce cesty k pokladu. Vylepšení odemčení Mapa pokladu zvětšuje hloubku cesty, zatímco vylepšení Rozšíření jí dává více prostoru do stran. Obě vylepšení prodlužují cestu k pokladu a zvyšují množství zlata, které najdeš.
</spoiler>

---

[Statistiky](docs/stats.md)      [For Loop](docs/scripting/for.md)      [Tuples](docs/scripting/tuples.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[harvest()](functions/harvest)      [move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)
