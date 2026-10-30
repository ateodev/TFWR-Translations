# Classifica Sotterranea
Il sottosuolo nasconde sfide ancora più grandi. Sei pronto a ottimizzare i tuoi programmi di estrazione e coltivazione?
Con questo sblocco puoi competere per i metodi più efficienti nelle profondità.

Puoi avviare una partita per la classifica sotterranea chiamando `leaderboard_run(leaderboard, filename, speedup)`.
Questo avvia una [simulazione](docs/unlocks/simulation.md) con condizioni iniziali fisse. Ogni categoria ha obiettivi diversi.

La partita ha successo se la condizione di successo è `True` quando la simulazione termina. In caso di successo, il tuo tempo verrà aggiunto alla classifica.
Ricorda di terminare il programma quando raggiungi l'obiettivo.

Per ridurre la variabilità, tutte le run devono durare almeno 2 ore (equivalenti in tempo reale). Se una run termina prima, verrà ripetuta e verrà caricato il tempo medio.

Le classifiche sotterranee hanno due condizioni speciali: innanzitutto, nella classifica del bambù non si può scavare, perché si svolge in superficie. In secondo luogo, la semina è disattivata nelle classifiche che non ne hanno bisogno.

## Reset Sotterraneo più Veloce
Automatizza completamente il gioco, partendo da un'unica casella di fattoria fino a sbloccare di nuovo le classifiche sotterranee.

Cerca di sbloccare `Unlocks.Underground_Leaderboard` il più velocemente possibile.

Chiamata di Funzione:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Condizione di Successo:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Classifiche di Risorse
Queste classifiche si concentrano sulla raccolta di specifiche risorse sotterranee il più velocemente possibile. Inizi con tutto sbloccato e con le risorse necessarie per cominciare.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Condizione di Successo: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Condizione di Successo: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Condizione di Successo: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Condizione di Successo: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Condizione di Successo: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Condizione di Successo: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Condizione di Successo: `num_items(Items.Gold) >= 100`

## Classifiche Sotterranee a Drone Singolo
Sfide nel sottosuolo limitate a un solo drone.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Condizione di Successo: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Condizione di Successo: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Condizione di Successo: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Condizione di Successo: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Condizione di Successo: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Condizione di Successo: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Condizione di Successo: `num_items(Items.Gold) >= 100`
