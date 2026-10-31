# Podziemna tabela wyników
Podziemia kryją jeszcze większe wyzwania. Czy jesteś gotów zoptymalizować swoje programy do wydobycia i uprawy?
Dzięki temu odblokowaniu możesz rywalizować o najbardziej wydajne metody w głębinach.

Możesz rozpocząć próbę w podziemnej tabeli wyników, wywołując `leaderboard_run(leaderboard, filename, speedup)`.
Rozpoczyna to [symulację](docs/unlocks/simulation.md) podobną do `simulate()`, z tym wyjątkiem, że warunki początkowe są stałe. Każda kategoria tabeli wyników ma inne warunki początkowe i warunki powodzenia.

Próba w tabeli wyników kończy się sukcesem, jeśli warunek powodzenia jest `True`, gdy symulacja się kończy.

Symulacja NIE zakończy się automatycznie po osiągnięciu celu. Musisz upewnić się, że program zakończy działanie.
Jeśli próba się powiedzie, twój czas zostanie dodany do tabeli wyników.

Aby zmniejszyć wariancję, wszystkie próby muszą obejmować co najmniej 2 godziny symulowanego czasu. Symulację można przyspieszyć, więc w rzeczywistości nie potrwa to tak długo. Jeśli próba zakończy się wcześniej, będzie powtarzana, aż łączny symulowany czas osiągnie 2 godziny. Jako twój wynik zostanie przesłany średni czas ze wszystkich prób.

Oto przykładowa konfiguracja, która pozwoli ci znaleźć się w tabeli wyników `Leaderboards.Rice_Single`.

![|x400](UndergroundLeaderboardSetup)

## Najszybszy podziemny reset
Podziemny reset to najbardziej prestiżowa kategoria. W tej kategorii całkowicie automatyzujesz drzewko odblokowań górniczych, zaczynając od jednego pola farmy i kończąc po ponownym odblokowaniu `Unlocks.Underground_Leaderboard`.

Nie musisz wszystkiego odblokowywać. Po prostu spróbuj jak najszybciej odblokować `Unlocks.Underground_Leaderboard`.

Pamiętaj, że za pomocą `num_unlocked(unlock) > 0` możesz sprawdzić, czy coś jest odblokowane. Możesz też użyć `get_cost()` na odblokowaniach, aby poznać ich koszt i automatycznie zdobywać odpowiednie przedmioty.

`unlock()` nie uwzględnia zależności w drzewku technologii. Można na przykład odblokować `Unlocks.Fertilizer` przed `Unlocks.Water`.

Wywołanie funkcji:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Równoważna symulacja:
`unlocks = {}
items = {}
globals = {}
#ujemna wartość zmiennej seed oznacza losowe ziarno
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Warunek powodzenia:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Rudy
Ta tabela wyników sprawdza twoje umiejętności wydobywania rud, a zwłaszcza kwarcu. Zmienia ona generowanie podłoża tak, że kolejne warstwy dostarczą ci węgla, potem żelaza, a na końcu kwarcu.

Zacznij z wszystkim odblokowanym i zbierz `20000` kwarcu tak szybko, jak potrafisz.

Wywołanie funkcji:
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

Równoważna symulacja:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Warunek powodzenia:
`num_items(Items.Quartz) >= 20000`

## Mapa skarbu
Ta tabela wyników zaczyna się z wszystkim odblokowanym i dużym zapasem energii. Zmienia ona generowanie podłoża tak, że występuje w nim mnóstwo map skarbu.

Rozgrywa się na świecie o rozmiarze 8x8 z jednym dronem. Celem jest jak najszybsze zebranie `115000` złota.

Wywołanie funkcji:
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

Równoważna symulacja:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Warunek powodzenia:
`num_items(Items.Gold) >= 115000`

## Tabele wyników zasobów
Te tabele wyników polegają na jak najszybszym zdobywaniu określonych zasobów. Zaczynasz ze wszystkimi odblokowaniami i dużym zapasem energii. Jedynym wyjątkiem jest tabela wyników piramid, w której energię musisz wytwarzać sam, odnawiając piramidy.

Celem jest zebranie określonej ilości zasobów.

Jak zawsze musisz upewnić się, że program zakończy działanie po osiągnięciu celu. Próba nie kończy się, dopóki program nie przestanie działać, nawet jeśli cel został już osiągnięty.

Te tabele wyników zmieniają generowanie podłoża tak, aby potrzebny zasób można było znajdować raz za razem. Dzięki temu nie trzeba używać `clear()`. Na przykład tabela wyników ryżu składa się wyłącznie z warstw gliny.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Warunek powodzenia: `num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
Pamiętaj, że w tabeli wyników bambusa kopanie jest niedozwolone.

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Warunek powodzenia: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Warunek powodzenia: `num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Warunek powodzenia: `num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Warunek powodzenia: `num_items(Items.Power) >= 150000`

## Podziemne tabele wyników jednego drona
Istnieją również tabele wyników dla uprawy jednym dronem. Otrzymujesz tylko jednego drona i farmę 8x8, a twoim zadaniem jest jak najszybsze zebranie określonej ilości zasobów.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Power) >= 30000`

