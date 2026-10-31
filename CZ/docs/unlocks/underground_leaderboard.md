# Podzemní žebříček
Podzemí skrývá ještě větší výzvy. Jsi připraven optimalizovat své programy na těžbu a farmaření?
S tímto odemčením můžeš soutěžit o nejefektivnější metody v hlubinách.

Běh pro podzemní žebříček spustíš voláním `leaderboard_run(leaderboard, filename, speedup)`.
To spustí [simulaci](docs/unlocks/simulation.md) podobnou `simulate()`, ale s pevně danými počátečními podmínkami. Každá kategorie žebříčku má jiné počáteční podmínky a podmínky úspěchu.

Běh pro žebříček je úspěšný, pokud je podmínka úspěchu na konci simulace `True`. 

Simulace se NEUKONČÍ automaticky ve chvíli, kdy dosáhneš cíle. Musíš zajistit, aby se program ukončil.
Pokud je běh úspěšný, tvůj čas se přidá do žebříčku.

Aby se snížila náhodnost, musí všechny běhy dohromady pokrýt alespoň 2 hodiny simulovaného času. Simulaci můžeš zrychlit, takže v reálném čase to tak dlouho trvat nebude. Pokud běh skončí dřív, opakuje se, dokud celkový simulovaný čas nedosáhne 2 hodin. Jako tvé skóre se pak nahraje průměrný čas všech běhů.

Tady je ukázkové nastavení, se kterým se dostaneš do žebříčku `Leaderboards.Rice_Single`.

![|x400](UndergroundLeaderboardSetup)

## Nejrychlejší podzemní reset
Podzemní reset je nejprestižnější kategorie. V této kategorii úplně zautomatizuješ strom odemčení pro těžbu, od jediné dlaždice farmy až po opětovné odemknutí `Unlocks.Underground_Leaderboard`.

Nemusíš odemknout všechno, jen se pokus odemknout `Unlocks.Underground_Leaderboard` co nejrychleji.

Pamatuj, že pomocí `num_unlocked(unlock) > 0` můžeš zkontrolovat, jestli je něco odemčené. Pomocí `get_cost()` můžeš u odemčení zjistit i jejich cenu, takže můžeš automaticky pěstovat ty správné předměty.

`unlock()` nebere ohled na závislosti ve stromu technologií. Například je možné odemknout `Unlocks.Fertilizer` dřív než `Unlocks.Water`.

Volání funkce:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Ekvivalentní simulace:
`unlocks = {}
items = {}
globals = {}
#záporná hodnota seedu znamená náhodný seed
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Podmínka úspěchu:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Rudy
Tento žebříček prověří tvé dovednosti v získávání rud, zejména křemene. Upravuje generování půdy tak, aby ti vrstvy půdy poskytly uhlí, pak železo a pak křemen, v tomto pořadí.

Začínáš se vším odemčeným a máš co nejrychleji získat `20000` křemene.

Volání funkce:
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

Ekvivalentní simulace:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Podmínka úspěchu:
`num_items(Items.Quartz) >= 20000`

## Mapa pokladu
V tomto žebříčku začínáš se vším odemčeným a se spoustou energie. Upravuje generování půdy tak, aby v ní bylo hodně map pokladu.

Odehrává se ve světě o velikosti 8x8 s jediným dronem. Cílem je co nejrychleji získat `115000` zlata.

Volání funkce:
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

Ekvivalentní simulace:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Podmínka úspěchu:
`num_items(Items.Gold) >= 115000`

## Žebříčky surovin
Tyto žebříčky se zaměřují na co nejrychlejší získání konkrétních surovin. Začínáš se vším odemčeným a se spoustou energie. Jedinou výjimkou je žebříček pyramid, kde si energii musíš vyrobit sám obnovováním pyramid.

Cílem je získat stanovené množství surovin.

Jako vždy musíš zajistit, aby se program po dosažení cíle ukončil. Běh není dokončen, dokud program neskončí, i když už je cíle dosaženo.

Tyto žebříčky upravují generování půdy tak, aby šlo požadovanou surovinu nacházet znovu a znovu. Díky tomu není potřeba volat `clear()`. Například žebříček rýže se skládá jen z vrstev jílu.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
Pozor, v žebříčku bambusu nelze kopat.

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Power) >= 150000`

## Podzemní žebříčky s jedním dronem
Existují také žebříčky pro farmaření s jediným dronem. Dostaneš jen jeden dron a farmu 8x8 a musíš co nejrychleji získat určité množství surovin.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Podmínka úspěchu: `num_items(Items.Power) >= 30000`

