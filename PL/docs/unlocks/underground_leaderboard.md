# Podziemna tabela wyników
Podziemia kryją jeszcze większe wyzwania. Czy jesteś gotów zoptymalizować swoje programy do wydobycia i uprawy?
Dzięki temu odblokowaniu możesz rywalizować o najbardziej wydajne metody w głębinach.

Możesz rozpocząć próbę w podziemnej tabeli wyników, wywołując `leaderboard_run(leaderboard, filename, speedup)`.
Rozpoczyna to [symulację](docs/unlocks/simulation.md) ze stałymi warunkami początkowymi. Każda kategoria ma inne cele.

Próba kończy się sukcesem, jeśli warunek powodzenia jest `True`, gdy symulacja się kończy. Jeśli próba się powiedzie, twój czas zostanie dodany do tabeli wyników.
Pamiętaj, aby zakończyć program po osiągnięciu celu.

Aby zmniejszyć wariancję, wszystkie próby muszą trwać co najmniej 2 godziny (w przeliczeniu na czas rzeczywisty). Jeśli próba zakończy się wcześniej, zostanie powtórzona, a jako wynik zostanie przesłany średni czas.

Podziemne tabele wyników mają dwa specjalne warunki. Po pierwsze, w tabeli wyników bambusa kopanie jest niedozwolone, ponieważ rozgrywa się ona na powierzchni. Po drugie, sadzenie jest wyłączone w tabelach wyników, które go nie wymagają.

## Najszybszy podziemny reset
Całkowicie zautomatyzuj grę, zaczynając od jednego pola farmy i kończąc po ponownym odblokowaniu podziemnych tabel wyników.

Spróbuj jak najszybciej odblokować `Unlocks.Underground_Leaderboard`.

Wywołanie funkcji:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Warunek powodzenia:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Tabele wyników zasobów
Te tabele wyników polegają na jak najszybszym zdobywaniu określonych podziemnych zasobów. Zaczynasz ze wszystkimi odblokowaniami i zasobami potrzebnymi na start.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Warunek powodzenia: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Warunek powodzenia: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Warunek powodzenia: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Warunek powodzenia: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Warunek powodzenia: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Warunek powodzenia: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Warunek powodzenia: `num_items(Items.Gold) >= 100`

## Podziemne tabele wyników jednego drona
Wyzwania pod ziemią, w których masz do dyspozycji tylko jednego drona.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Warunek powodzenia: `num_items(Items.Gold) >= 100`
