# 地下排行榜
地下藏着更大的挑战。你准备好优化你的采矿和耕作程序了吗？
解锁此项后，你可以在地底深处一较高下，看看谁的方法效率最高。

调用 `leaderboard_run(leaderboard, filename, speedup)` 即可开始一次地下排行榜挑战。
这会启动一次起始条件固定的[模拟](docs/unlocks/simulation.md)。每个类别都有不同的目标。

如果模拟结束时成功条件为 `True`，则挑战成功。如果挑战成功，你的时间纪录将被添加到排行榜。
记得在达成目标时终止程序。

为了减少方差，所有挑战都要求运行至少 2 小时（按实际时间等效计算）。如果挑战提前完成，则会重复运行，并上传平均时间。

地下排行榜有两项特殊条件：第一，竹子排行榜禁止挖掘，因为它在地面上进行。第二，不需要种植的排行榜会禁用种植。

## 最快地下重置
从一块农田开始，实现游戏完全自动化，直到再次解锁地下排行榜。

尽快解锁 `Unlocks.Underground_Leaderboard`。

函数调用：
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

成功条件：
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## 资源排行榜
这些排行榜的标准是尽快收获特定的地下资源。开局获得所有解锁项，以及起步所需的资源。

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
成功条件：`num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
成功条件：`num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
成功条件：`num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
成功条件：`num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
成功条件：`num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
成功条件：`num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
成功条件：`num_items(Items.Gold) >= 100`

## 单无人机地下排行榜
只能使用一架无人机的地下挑战。

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
成功条件：`num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
成功条件：`num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
成功条件：`num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
成功条件：`num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
成功条件：`num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
成功条件：`num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
成功条件：`num_items(Items.Gold) >= 100`
