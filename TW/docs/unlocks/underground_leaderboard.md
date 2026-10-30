# 地下排行榜
地下還藏著更大的挑戰。你準備好最佳化你的採礦和耕作程式了嗎？
有了這個解鎖項，你就能在地底深處比拚誰的方法效率最高。

呼叫 `leaderboard_run(leaderboard, filename, speedup)` 即可開始一次地下排行榜挑戰。
這會以固定的起始條件啟動一次[模擬](docs/unlocks/simulation.md)。每個類別都有不同的目標。

如果模擬結束時成功條件為 `True`，則挑戰成功。挑戰成功後，你的時間紀錄將被新增到排行榜。
請記得在達成目標時終止你的程式。

為了減少變異數，所有挑戰都要求執行至少 2 小時（換算成真實時間）。如果挑戰提前完成，則會重複執行，並上傳平均時間。

地下排行榜有兩項特殊條件：第一，竹子排行榜在地面上進行，因此不允許挖掘。第二，不需要種植的排行榜會停用種植。

## 最快地下重設
從一塊農田開始，實現遊戲完全自動化，直到再次解鎖地下排行榜。

試著盡快解鎖 `Unlocks.Underground_Leaderboard`。

函式呼叫：
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

成功條件：
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## 資源排行榜
這些排行榜的重點是盡快收穫特定的地下資源。開局時所有內容皆已解鎖，並備有起步所需的資源。

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
成功條件：`num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
成功條件：`num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
成功條件：`num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
成功條件：`num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
成功條件：`num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
成功條件：`num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
成功條件：`num_items(Items.Gold) >= 100`

## 單無人機地下排行榜
僅限一架無人機的地下挑戰。

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
成功條件：`num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
成功條件：`num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
成功條件：`num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
成功條件：`num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
成功條件：`num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
成功條件：`num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
成功條件：`num_items(Items.Gold) >= 100`
