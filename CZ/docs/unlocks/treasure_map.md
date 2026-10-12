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
