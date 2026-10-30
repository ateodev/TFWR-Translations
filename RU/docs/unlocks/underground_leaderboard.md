# Подземный рейтинг
Под землей тебя ждут еще более серьезные испытания. Готов ли ты оптимизировать свои программы для добычи и фермерства?
С этой технологией ты можешь соревноваться в поиске самых эффективных методов работы в глубинах.

Чтобы запустить подземный рейтинг, вызови `leaderboard_run(leaderboard, filename, speedup)`.
Это начнет [симуляцию](docs/unlocks/simulation.md) с фиксированными начальными условиями. У каждой категории свои цели.

Запуск считается успешным, если условие успеха равно `True` в момент окончания симуляции. В случае успеха твое время будет добавлено в рейтинг.
Не забудь завершить программу, когда цель будет достигнута.

Чтобы уменьшить разброс, все запуски должны длиться не менее 2 часов (в пересчете на реальное время). Если запуск завершится раньше, он будет повторен, а в рейтинг загрузится среднее время.

У подземных рейтингов есть два особых условия. Во-первых, в рейтинге по бамбуку копать нельзя, потому что он проходит на поверхности. Во-вторых, в рейтингах, где посадка не нужна, она отключена.

## Самый быстрый подземный сброс
Полностью автоматизируй игру от одной клетки фермы до повторной разблокировки подземных рейтингов.

Постарайся как можно быстрее разблокировать `Unlocks.Underground_Leaderboard`.

Вызов функции:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Условие успеха:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Рейтинги по ресурсам
В этих рейтингах нужно как можно быстрее собрать определенные подземные ресурсы. Ты начинаешь со всеми разблокированными технологиями и ресурсами, необходимыми для старта.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Условие успеха: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Условие успеха: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Условие успеха: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Условие успеха: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Условие успеха: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Условие успеха: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Условие успеха: `num_items(Items.Gold) >= 100`

## Подземные рейтинги для одного дрона
Испытания под землей, в которых у тебя есть только один дрон.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Условие успеха: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Условие успеха: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Условие успеха: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Условие успеха: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Условие успеха: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Условие успеха: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Условие успеха: `num_items(Items.Gold) >= 100`
