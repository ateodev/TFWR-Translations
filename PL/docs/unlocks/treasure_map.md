[<- Żelazo](docs/unlocks/iron.md)
---
# Mapa skarbu

Legendy mówią o nieuchwytnym skarbie ukrytym przez dawno zmarłego, zapominalskiego pirata — albo jakoś tak. A co, jeśli zapisał drogę do skarbu na mapie, a potem ją zgubił? Może upuścił mapę, gdy odcięła mu drogę rzeka lawy, i zachowała się ona pod warstwą bazaltu. Pomiar bazaltu może coś ujawnić.

<spoiler=powiedz mi więcej>
Wypatruj warstwy `Grounds.Basalt`. Spróbuj zmierzyć bazalt i sprawdź, co ci powie. Wskazówka może zaprowadzić cię do mapy skarbu, a zmierzenie mapy z pewnością zwróci drogę do samego skarbu — tylko czy uda ci się rozszyfrować jej instrukcje?
</spoiler>

<spoiler=po prostu powiedz jak>
Dobrze, sprawa wygląda tak: znajdź warstwę `Grounds.Basalt` i blok `Grounds.Treasure_Map` znajdujący się bezpośrednio pod nią. Możesz użyć `measure()` na bazalcie, aby uzyskać pozycję `(x, y)` leżącego niżej bloku mapy.

Wywołaj `measure()` na bloku mapy, aby otrzymać drogę do skarbu jako ciąg liter oznaczających kierunki. N, E, S i W oznaczają odpowiednio `North`, `East`, `South` i `West`, natomiast D oznacza „Down” lub „Dig”. Litery te opisują drogę złożoną z bloków `Grounds.Treasure_Path`, która prowadzi do skarbu.

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

Możesz użyć pętli `for` na ciągu znaków, aby przetwarzać go litera po literze:
```
path = measure()
for letter in path:
    do_something(letter)
```

Dron, który dokopie się do bloku mapy skarbu, musi również odnaleźć skarb. Przez cały czas musi pozostawać na blokach `Grounds.Treasure_Path`. Jeśli przemieści się na inne podłoże, droga zniknie, a skarb zostanie utracony.

Na końcu drogi znajduje się blok `Grounds.Treasure_Goal`. Jeśli dron nie zboczył z drogi, pojawi się na nim `Entities.Underground_Treasure`. Dron może użyć `harvest()` na skrzyni, aby zebrać złoto.

Ilość złota jest proporcjonalna do długości drogi do skarbu. Ulepszanie odblokowania Mapy skarbu zwiększa jej głębokość, a ulepszanie Rozszerzenia daje jej więcej miejsca na ruch w poziomie. Oba ulepszenia wydłużają drogę do skarbu i zwiększają ilość znalezionego złota.
</spoiler>

---

[Statystyki](docs/stats.md)      [Pętla for](docs/scripting/for.md)      [Krotki](docs/scripting/tuples.md)      [Podziemne zmysły](docs/unlocks/underground_senses.md)

[harvest()](functions/harvest)      [move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)
