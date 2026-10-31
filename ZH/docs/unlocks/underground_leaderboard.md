# 地下排行榜
地下藏着更大的挑战。你准备好优化你的采矿和耕作程序了吗？
解锁此项后，你可以在地底深处一较高下，看看谁的方法效率最高。

调用 `leaderboard_run(leaderboard, filename, speedup)` 即可开始一次地下排行榜挑战。
这会启动一次类似于 `simulate()` 的[模拟](docs/unlocks/simulation.md)，只不过起始条件是固定的。每个排行榜类别都有不同的开始和成功条件。

如果模拟结束时成功条件为 `True`，则排行榜挑战成功。

当目标达成时，模拟不会自动结束。你必须确保程序终止。
如果挑战成功，你的时间纪录将被添加到排行榜。

为了减少方差，所有挑战都必须覆盖至少 2 小时的模拟时间。你可以加速模拟，所以实际不会花那么长时间。如果挑战提前完成，则会重复运行，直到总模拟时间达到 2 小时。随后，将所有运行过程的平均时间作为你的分数上传。

以下是示例设置，可以让你登上 `Leaderboards.Rice_Single` 排行榜。

![|x400](UndergroundLeaderboardSetup)

## 最快地下重置
地下重置是最有声望的类别。在这个类别中，你要从一块农田开始，将采矿解锁树完全自动化，直到再次解锁 `Unlocks.Underground_Leaderboard`。

不必解锁全部内容，只需尽快解锁 `Unlocks.Underground_Leaderboard`。

请记住，你可以使用 `num_unlocked(unlock) > 0` 来检查某项是否已解锁，也可以对解锁项使用 `get_cost()` 来查看其成本，以便自动耕种正确的物品。

`unlock()` 不受科技树中的前置解锁条件限制。例如，可以先解锁 `Unlocks.Fertilizer`，再解锁 `Unlocks.Water`。

函数调用：
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

等效模拟：
`unlocks = {}
items = {}
globals = {}
#负数种子值表示随机种子
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功条件：
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## 矿石
这个排行榜考验你开采矿石的技巧，尤其是石英。它会调整地块生成方式，让各地层依次为你提供煤炭、铁矿和石英。

从解锁全部内容开始，尽快收获 `20000` 份石英。

函数调用：
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

等效模拟：
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功条件：
`num_items(Items.Quartz) >= 20000`

## 藏宝图
这个排行榜开局解锁全部内容，并提供大量能量。它会调整地块生成方式，让地下出现大量藏宝图。

挑战在 8x8 的世界中进行，只有一架无人机。目标是尽快收获 `115000` 份金币。

函数调用：
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

等效模拟：
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功条件：
`num_items(Items.Gold) >= 115000`

## 资源排行榜
这些排行榜的标准是尽快收获特定资源。开局获得所有解锁项以及大量能量。唯一的例外是金字塔排行榜，你需要通过修复金字塔自行产出能量。

目标是收获特定数量的资源。

与之前一样，你需要确保程序在达到目标时终止。即使目标已达成，只要程序没有结束，挑战就不会完成。

这些排行榜会调整地块生成方式，让所需资源可以反复找到。这意味着不需要使用 `clear()`。例如，水稻排行榜只由黏土层构成。

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
成功条件：`num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
注意，竹子排行榜禁止挖掘。

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
成功条件：`num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
成功条件：`num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
成功条件：`num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
成功条件：`num_items(Items.Power) >= 150000`

## 单无人机地下排行榜
也有单无人机耕作的排行榜。你只有一架无人机和一个 8x8 的农场，并且必须尽快收获特定数量的资源。

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
成功条件：`num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
成功条件：`num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
成功条件：`num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
成功条件：`num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
成功条件：`num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
成功条件：`num_items(Items.Power) >= 30000`

