[<- Grzyby](docs/unlocks/mushroom.md) <right>[Wiertło wybuchowe ->](docs/unlocks/explosive_drill.md)
---
# Dynamit

Rewolucyjny materiał wybuchowy pozostawiony przez poprzednie wyprawy górnicze. Na (nie)szczęście twoje wiertło idealnie nadaje się do detonowania dynamitu i wysadzania wszystkich bloków wokół.

Aby bezpiecznie wydobywać dynamit, znajdź warstwę `Grounds.Dynamite`, pod którą bezpośrednio leży warstwa `Grounds.Soot`. Górna warstwa dynamitu nieco się zestarzała i do części jej bloków można bezpiecznie się dokopać. Niektóre bloki dynamitu są jednak nadal aktywne i eksplodują, gdy się do nich dokopiesz.

Zebranego dynamitu można użyć za pomocą `use_item(Items.Dynamite)`; eksploduje bezpośrednio pod dronem.

Ten przykład dokopuje się do dynamitu i kopie dookoła początkowego miejsca kopania, wypisując pomiary bloków sadzy poniżej:
{{codeexample 
{
    "camera_position": {"x": -3, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 800, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 7, "y": 7},
    "execution_speed": 2,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 6,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(3):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [
    East, South, West, West, 
    North, North, East, East
]
for dir in circle_directions:
    move(dir)
    dig()
    print(measure())
}}

## Dynamitowy saper
Czy potrafisz znaleźć i wykopać wszystkie niewypały dynamitu, pozostawiając tylko aktywne bloki? Każdy aktywny blok otoczony wyłącznie innymi aktywnymi blokami lub blokami sadzy da ci dodatkowy dynamit, gdy warstwa dynamitu zniknie.

Na szczęście pomogą ci bloki sadzy poniżej: potrafią wykryć liczbę sąsiednich bloków dynamitu zawierających aktywne ładunki. Nie wskażą dokładnie, które bloki są aktywne, a tylko ich łączną liczbę, więc musisz połączyć odczyty z kilku bloków sadzy i samodzielnie znaleźć rozwiązanie.

Wywołanie `measure()` na bloku sadzy zwraca liczbę min na ośmiu sąsiednich polach w warstwie dynamitu powyżej. Wynik może wynosić od `0` (brak aktywnych min) do `8` (każdy sąsiad zawiera aktywną minę).

Pierwszy wykopany blok w warstwie dynamitu jest zawsze niewypałem. Każdy wydobyty blok daje trochę dynamitu. Gdy warstwa zostanie zniszczona — przez wykopanie wszystkich niewypałów lub przypadkowe dokopanie się do aktywnego dynamitu — otrzymasz także ilość dynamitu równą kwadratowi liczby całkowicie odsłoniętych aktywnych bloków.

## Struktura warstw
Liczba aktywnych min w warstwie dynamitu, a tym samym trudność ich odnalezienia, rośnie wraz z głębokością. Łączna liczba min rośnie wraz z rozmiarem farmy, a z nią maksymalny możliwy plon za oczyszczenie warstwy dynamitu.

Ulepszaj dynamit, aby zwiększyć plon z wykopywania bloków dynamitu i całkowitego odsłaniania aktywnych bloków. Ulepszenie zwiększa też energię eksplozji o 30%.

## Wykrywanie sukcesu i porażki
Jeśli dokopiesz się do aktywnego dynamitu, oba pokłady eksplodują. Możesz to sprawdzić za pomocą `get_ground_type()` po dokopaniu się do `Grounds.Dynamite`. Jeśli podłoże nie jest typu `Grounds.Soot`, zagadka zakończyła się niepowodzeniem. Jeśli natomiast wykopiesz ostatni nieaktywny blok dynamitu, wszystkie bloki dynamitu znikną, a ty otrzymasz maksymalny plon za tę zagadkę. Warstwa sadzy pozostanie, ale `measure()` zwróci `None`, co oznacza, że zagadka została pomyślnie rozwiązana.

`# Dokop się do bloku dynamitu i sprawdź stan zagadki
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # Dokopano się do aktywnego dynamitu, zagadka nieudana
        return False
    elif measure() == None:
        # Wykopano ostatni niewypał, zagadka rozwiązana
        return True
    else:
        # Pomiar zwrócił liczbę, zagadka nadal trwa
        return None
`

## Strategia
<spoiler=podpowiedź>
Poniższy kod dokopuje się do warstwy dynamitu i szuka bloków sadzy, których pomiar wynosi `0`. Dla każdego takiego bloku wykopuje wszystkie otaczające go bloki dynamitu:
{{codeexample 
{
    "camera_position": {"x": -5, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 800, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 7, "y": 7},
    "execution_speed": 4,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 6,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(3):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [
    East, South, West, West, North,
    North, East, East, South, West
]
for dir in circle_directions:
    if get_ground_type() == Grounds.Soot and measure() == 0:
        for dir2 in circle_directions:
            move(dir2)
            while get_ground_type() != Grounds.Soot:
                dig()
    move(dir)
}}
</spoiler>

---

[Statystyki](docs/stats.md)      [Podziemne zmysły](docs/unlocks/underground_senses.md)      [Słowniki](docs/scripting/dicts.md)      [Zbiory](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
