# Підземна таблиця лідерів
Під землею на вас чекають ще більші виклики. Чи готові ви оптимізувати свої програми для видобутку та фермерства?
Це розблокування дозволяє змагатися за найефективніші методи в глибинах.

Ви можете почати забіг у підземній таблиці лідерів, викликавши `leaderboard_run(leaderboard, filename, speedup)`.
Це запускає [симуляцію](docs/unlocks/simulation.md) з фіксованими початковими умовами. Кожна категорія має власні цілі.

Забіг вважається успішним, якщо умова для успіху дорівнює `True` на момент завершення симуляції. Якщо забіг успішний, ваш час буде додано до таблиці лідерів.
Не забудьте завершити програму, коли ціль досягнуто.

Щоб зменшити випадковість результатів, кожен забіг має тривати щонайменше 2 години (в еквіваленті реального часу). Якщо забіг завершується раніше, його буде повторено, а завантажено буде середній час.

Підземні таблиці лідерів мають дві особливі умови. По-перше, у таблиці лідерів бамбуку копати заборонено, бо вона проходить на поверхні. По-друге, у таблицях лідерів, де садіння не потрібне, його вимкнено.

## Швидке підземне скидання
Повністю автоматизуйте гру від однієї фермерської ділянки до повторного розблокування підземних таблиць лідерів.

Спробуйте розблокувати `Unlocks.Underground_Leaderboard` якомога швидше.

Виклик функції:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Умова для успіху:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Таблиці лідерів для ресурсів
Ці таблиці лідерів зосереджені на якомога швидшому видобутку певних підземних ресурсів. Ви стартуєте з усіма відкритими можливостями та необхідними для початку ресурсами.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Умова для успіху: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Умова для успіху: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Умова для успіху: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Умова для успіху: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Умова для успіху: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Умова для успіху: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Умова для успіху: `num_items(Items.Gold) >= 100`

## Підземні таблиці лідерів для одного дрона
Виклики під землею, обмежені одним дроном.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Gold) >= 100`
