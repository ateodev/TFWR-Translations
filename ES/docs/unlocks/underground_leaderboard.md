# Tabla de clasificación subterránea
El subsuelo alberga desafíos aún mayores. ¿Estás preparado para optimizar tus programas de minería y cultivo?
Con este desbloqueo, puedes competir por los métodos más eficientes en las profundidades.

Puedes iniciar una carrera en la tabla de clasificación subterránea llamando a `leaderboard_run(leaderboard, filename, speedup)`.
Esto inicia una [simulación](docs/unlocks/simulation.md) parecida a `simulate()`, salvo que las condiciones iniciales son fijas. Cada categoría de la tabla de clasificación tiene condiciones iniciales y de éxito distintas.

La carrera tiene éxito si la condición de éxito es `True` cuando la simulación termina. 

La simulación NO terminará automáticamente cuando se alcance el objetivo. Debes asegurarte de que el programa termine.
Si la carrera tiene éxito, tu tiempo se añadirá a la tabla de clasificación.

Para reducir la variación, todas las carreras deben abarcar al menos 2 horas de tiempo simulado. Puedes acelerar la simulación, así que no tardará tanto tiempo real. Si una carrera termina antes, se repetirá hasta que el tiempo simulado total alcance las 2 horas. Después se subirá como puntuación el tiempo medio de todas las carreras.

Aquí hay un ejemplo de configuración que te pondrá en la tabla de clasificación `Leaderboards.Rice_Single`.

![|x400](UndergroundLeaderboardSetup)

## Reinicio subterráneo más rápido
El reinicio subterráneo es la categoría más prestigiosa. En ella automatizas por completo el árbol de desbloqueos de minería: empiezas con una sola parcela y terminas cuando vuelves a desbloquear `Unlocks.Underground_Leaderboard`.

No tienes que desbloquear todo, solo intenta desbloquear `Unlocks.Underground_Leaderboard` lo más rápido posible.

Recuerda que puedes usar `num_unlocked(unlock) > 0` para comprobar si algo está desbloqueado. También puedes usar `get_cost()` con los desbloqueos para ver cuánto cuestan y conseguir automáticamente los ítems adecuados.

`unlock()` no tiene en cuenta las dependencias del árbol tecnológico. Por ejemplo, es posible desbloquear `Unlocks.Fertilizer` antes que `Unlocks.Water`.

Llamada de función:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Simulación equivalente:
`unlocks = {}
items = {}
globals = {}
#un valor de semilla negativo significa una semilla aleatoria
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Condición de éxito:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Minerales
Esta tabla de clasificación pone a prueba tu habilidad para extraer minerales, sobre todo cuarzo. Modifica la generación del terreno para que las capas de terreno te proporcionen carbón, luego hierro y luego cuarzo, en este orden.

Comienza con todo desbloqueado y consigue `20000` de cuarzo lo más rápido que puedas.

Llamada de función:
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

Simulación equivalente:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Condición de éxito:
`num_items(Items.Quartz) >= 20000`

## Mapa del tesoro
Esta tabla de clasificación comienza con todo desbloqueado y mucha energía. Modifica la generación del terreno para que haya muchos mapas del tesoro.

Se desarrolla en un mundo de 8x8 con un solo dron. El objetivo es conseguir `115000` de oro lo más rápido posible.

Llamada de función:
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

Simulación equivalente:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Condición de éxito:
`num_items(Items.Gold) >= 115000`

## Tablas de clasificación de recursos
Estas tablas de clasificación se centran en conseguir determinados recursos lo más rápido posible. Comienzas con todo desbloqueado y mucha energía. La única excepción es la tabla de clasificación de las pirámides, en la que tendrás que producir energía tú mismo restaurando pirámides.

El objetivo es conseguir una cantidad determinada de recursos.

Como siempre, necesitas asegurarte de que tu programa termine cuando alcances el objetivo. Una carrera no se considera finalizada hasta que el programa termina, incluso si se ha alcanzado el objetivo.

Estas tablas de clasificación modifican la generación del terreno para que el recurso deseado se pueda encontrar una y otra vez. Esto significa que no hace falta usar `clear()`. Por ejemplo, la tabla de clasificación del arroz consta solo de capas de arcilla.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Condición de éxito: `num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
Ten en cuenta que la tabla de clasificación del bambú no permite excavar.

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Condición de éxito: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Condición de éxito: `num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Condición de éxito: `num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Condición de éxito: `num_items(Items.Power) >= 150000`

## Tablas de clasificación subterráneas de un solo dron
También hay tablas de clasificación para cultivar con un solo dron. Solo dispones de un dron y una granja de 8x8, y debes obtener una cantidad determinada de recursos lo más rápido posible.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Condición de éxito: `num_items(Items.Power) >= 30000`

