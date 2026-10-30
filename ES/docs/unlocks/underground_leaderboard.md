# Tabla de clasificación subterránea
El subsuelo alberga desafíos aún mayores. ¿Estás preparado para optimizar tus programas de minería y cultivo?
Con este desbloqueo, puedes competir por los métodos más eficientes en las profundidades.

Puedes iniciar una carrera en la tabla de clasificación subterránea llamando a `leaderboard_run(leaderboard, filename, speedup)`.
Esto inicia una [simulación](docs/unlocks/simulation.md) con condiciones iniciales fijas. Cada categoría tiene objetivos distintos.

La carrera tiene éxito si la condición de éxito es `True` cuando la simulación termina. Si tiene éxito, tu tiempo se añadirá a la tabla de clasificación.
Recuerda terminar tu programa cuando se alcance el objetivo.

Para reducir la variación, todas las carreras deben durar al menos 2 horas (equivalente en tiempo real). Si una carrera termina antes, se repetirá y se subirá el tiempo medio.

Las tablas de clasificación subterráneas tienen dos condiciones especiales: en primer lugar, la tabla de clasificación del bambú no permite excavar, porque se desarrolla en la superficie. En segundo lugar, plantar está desactivado en las tablas de clasificación que no lo necesitan.

## Reinicio subterráneo más rápido
Automatiza el juego por completo, desde una sola parcela hasta volver a desbloquear las tablas de clasificación subterráneas.

Intenta desbloquear `Unlocks.Underground_Leaderboard` lo más rápido posible.

Llamada de función:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Condición de éxito:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Tablas de clasificación de recursos
Estas tablas de clasificación se centran en conseguir determinados recursos subterráneos lo más rápido posible. Comienzas con todo desbloqueado y con los recursos necesarios para empezar.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Condición de éxito: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Condición de éxito: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Condición de éxito: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Condición de éxito: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Condición de éxito: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Condición de éxito: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Condición de éxito: `num_items(Items.Gold) >= 100`

## Tablas de clasificación subterráneas de un solo dron
Desafíos limitados a un solo dron en el subsuelo.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Gold) >= 100`
