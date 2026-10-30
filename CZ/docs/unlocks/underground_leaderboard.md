# Podzemní žebříček
Podzemí skrývá ještě větší výzvy. Jsi připraven optimalizovat své programy na těžbu a farmaření?
S tímto odemčením můžeš soutěžit o nejefektivnější metody v hlubinách.

Běh pro podzemní žebříček spustíš voláním `leaderboard_run(leaderboard, filename, speedup)`.
To spustí [simulaci](docs/unlocks/simulation.md) s pevně danými počátečními podmínkami. Každá kategorie má jiné cíle.

Běh je úspěšný, pokud je podmínka úspěchu na konci simulace `True`. Při úspěchu se tvůj čas přidá do žebříčku.
Nezapomeň ukončit program, jakmile dosáhneš cíle.

Aby se snížila náhodnost, musí každý běh trvat alespoň 2 hodiny (v přepočtu na reálný čas). Pokud je běh dokončen dřív, opakuje se a nahraje se průměrný čas.

Podzemní žebříčky mají dvě zvláštní podmínky: Zaprvé, v žebříčku bambusu nelze kopat, protože se odehrává na povrchu. Zadruhé, v žebříčcích, které sázení nepotřebují, je sázení vypnuté.

## Nejrychlejší podzemní reset
Úplně zautomatizuj hru od jediné dlaždice farmy až po opětovné odemknutí podzemních žebříčků.

Pokus se odemknout `Unlocks.Underground_Leaderboard` co nejrychleji.

Volání funkce:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Podmínka úspěchu:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Žebříčky surovin
Tyto žebříčky se zaměřují na co nejrychlejší získání konkrétních podzemních surovin. Začínáš se vším odemčeným a se surovinami, které potřebuješ na začátek.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Gold) >= 100`

## Podzemní žebříčky s jedním dronem
Výzvy v podzemí omezené na jediný dron.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Gold) >= 100`
