# Підземна таблиця лідерів
Під землею на вас чекають ще більші виклики. Чи готові ви оптимізувати свої програми для видобутку та фермерства?
Це розблокування дозволяє змагатися за найефективніші методи в глибинах.

Ви можете почати забіг у підземній таблиці лідерів, викликавши `leaderboard_run(leaderboard, filename, speedup)`.
Це запускає [симуляцію](docs/unlocks/simulation.md) подібно до `simulate()`, але з фіксованими початковими умовами. Кожна категорія таблиці лідерів має власні стартові умови та умови для успіху.

Забіг вважається успішним, якщо умова для успіху дорівнює `True` на момент завершення симуляції. 

Симуляція НЕ завершується автоматично, коли ціль досягнута. Ви повинні самі подбати про завершення програми.
Якщо забіг успішний, ваш час буде додано до таблиці лідерів.

Щоб зменшити випадковість результатів, усі забіги разом мають охоплювати щонайменше 2 години симульованого часу. Симуляцію можна прискорити, тож у реальному часі це не займе так багато. Якщо забіг завершується раніше, його буде повторено, доки загальний симульований час не досягне 2 годин. Потім як ваш результат завантажується середній час усіх забігів.

Ось приклад налаштування, який дозволить вам потрапити в таблицю лідерів `Leaderboards.Rice_Single`.

![|x400](UndergroundLeaderboardSetup)

## Швидке підземне скидання
Підземне скидання є найпрестижнішою категорією. У цій категорії ви повністю автоматизуєте дерево розблокувань видобутку, починаючи з однієї фермерської ділянки й закінчуючи повторним розблокуванням `Unlocks.Underground_Leaderboard`.

Вам не потрібно розблоковувати все, просто спробуйте розблокувати `Unlocks.Underground_Leaderboard` якомога швидше.

Пам'ятайте, що ви можете використовувати `num_unlocked(unlock) > 0`, щоб перевірити, чи щось розблоковано. Також можна застосувати `get_cost()` до розблокувань, щоб подивитися їхню вартість і автоматично збирати потрібні предмети.

`unlock()` не зважає на залежності в дереві технологій. Наприклад, можна розблокувати `Unlocks.Fertilizer` раніше за `Unlocks.Water`.

Виклик функції:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Еквівалентна симуляція:
`unlocks = {}
items = {}
globals = {}
#негативне значення сіда означає випадковий сід
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Умова для успіху:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Руди
Ця таблиця лідерів перевіряє ваші навички видобутку руд, зокрема кварцу. Генерація ґрунту в ній змінена так, що шари ґрунту даватимуть вам вугілля, потім залізо, а потім кварц, саме в такому порядку.

Почніть з усіма відкритими можливостями та видобудьте `20000` кварцу якнайшвидше.

Виклик функції:
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

Еквівалентна симуляція:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Умова для успіху:
`num_items(Items.Quartz) >= 20000`

## Карта скарбів
У цій таблиці лідерів ви починаєте з усіма відкритими можливостями та великим запасом енергії. Генерація ґрунту в ній змінена так, що карт скарбів дуже багато.

Забіг проходить на світі розміром 8x8 з одним дроном. Мета: назбирати `115000` золота якнайшвидше.

Виклик функції:
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

Еквівалентна симуляція:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Умова для успіху:
`num_items(Items.Gold) >= 115000`

## Таблиці лідерів для ресурсів
Ці таблиці лідерів зосереджені на якомога швидшому видобутку певних ресурсів. Ви стартуєте з усіма відкритими можливостями та великим запасом енергії. Єдиний виняток становить таблиця лідерів пірамід, де енергію вам доведеться виробляти самостійно, відновлюючи піраміди.

Мета: назбирати задану кількість ресурсів.

Як завжди, ви повинні подбати про те, щоб програма завершилася, коли ціль досягнута. Забіг не закінчується, доки не завершиться програма, навіть якщо ціль уже досягнута.

У цих таблицях лідерів генерація ґрунту змінена так, що потрібний ресурс можна знаходити знову і знову. Тож викликати `clear()` немає потреби. Наприклад, таблиця лідерів рису складається лише з шарів глини.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Умова для успіху: `num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
Зверніть увагу, що в таблиці лідерів бамбуку копати заборонено.

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Умова для успіху: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Умова для успіху: `num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Умова для успіху: `num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Умова для успіху: `num_items(Items.Power) >= 150000`

## Підземні таблиці лідерів для одного дрона
Є також таблиці лідерів для фермерства одним дроном. Ви отримуєте лише один дрон і ферму 8x8, і маєте якнайшвидше назбирати певну кількість ресурсів.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Умова для успіху: `num_items(Items.Power) >= 30000`

