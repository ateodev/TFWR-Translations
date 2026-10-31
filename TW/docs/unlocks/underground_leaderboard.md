# 地下排行榜
地下還藏著更大的挑戰。你準備好最佳化你的採礦和耕作程式了嗎？
有了這個解鎖項，你就能在地底深處比拚誰的方法效率最高。

呼叫 `leaderboard_run(leaderboard, filename, speedup)` 即可開始一次地下排行榜挑戰。
這會啟動一次類似於 `simulate()` 的[模擬](docs/unlocks/simulation.md)，只不過起始條件是固定的。每個排行榜類別都有不同的開始和成功條件。

如果模擬結束時成功條件為 `True`，則排行榜挑戰成功。

當目標達成時，模擬「不會」自動結束。你必須確保程式終止。
如果挑戰成功，你的時間紀錄將被新增到排行榜。

為了減少變異數，所有挑戰都必須涵蓋至少 2 小時的模擬時間。你可以加速模擬，所以實際上不會花那麼長時間。如果挑戰提前完成，則會重複執行，直到總模擬時間達到 2 小時。隨後，將所有執行過程的平均時間作為你的分數上傳。

以下是範例設定，可以讓你登上 `Leaderboards.Rice_Single` 排行榜。

![|x400](UndergroundLeaderboardSetup)

## 最快地下重設
地下重設是最有聲望的類別。在這個類別中，你要將採礦解鎖樹完全自動化：從一塊農田開始，直到再次解鎖 `Unlocks.Underground_Leaderboard` 為止。

不必解鎖全部內容，只需盡快解鎖 `Unlocks.Underground_Leaderboard`。

請記住，你可以使用 `num_unlocked(unlock) > 0` 來檢查某項是否已解鎖，也可以對解鎖項使用 `get_cost()` 來檢視其成本，以便自動耕種正確的物品。

`unlock()` 不受科技樹中的前置解鎖條件限制。例如，可以先解鎖 `Unlocks.Fertilizer`，再解鎖 `Unlocks.Water`。

函式呼叫：
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

等效模擬：
`unlocks = {}
items = {}
globals = {}
#負數種子值表示隨機種子
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功條件：
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## 礦石
這個排行榜考驗你開採礦石的技巧，特別是石英。它會調整地層的生成方式，讓地層依序提供煤炭、鐵礦，然後是石英。

從解鎖全部內容開始，盡快收穫 `20000` 份石英。

函式呼叫：
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

等效模擬：
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功條件：
`num_items(Items.Quartz) >= 20000`

## 藏寶圖
這個排行榜開局時所有內容皆已解鎖，並有大量的能量。它會調整地層的生成方式，讓地下出現大量藏寶圖。

挑戰在 8x8 的世界中進行，且只有一架無人機。目標是盡快收穫 `115000` 份金幣。

函式呼叫：
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

等效模擬：
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功條件：
`num_items(Items.Gold) >= 115000`

## 資源排行榜
這些排行榜的重點是盡快收穫特定的資源。開局時所有內容皆已解鎖，並有大量的能量。唯一的例外是金字塔排行榜，你需要修復金字塔來自行產生能量。

目標是收穫指定數量的資源。

與之前一樣，你需要確保程式在達到目標時終止。即使目標已達成，只要程式沒有結束，挑戰就不會完成。

這些排行榜會調整地層的生成方式，讓目標資源可以一再被找到。也就是說，不需要使用 `clear()`。例如，水稻排行榜就只有黏土層。

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
成功條件：`num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
注意，竹子排行榜不允許挖掘。

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
成功條件：`num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
成功條件：`num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
成功條件：`num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
成功條件：`num_items(Items.Power) >= 150000`

## 單無人機地下排行榜
也有單無人機耕作的排行榜。你只有一架無人機和一個 8x8 的農場，並且必須盡快收穫特定數量的資源。

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
成功條件：`num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
成功條件：`num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
成功條件：`num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
成功條件：`num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
成功條件：`num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
成功條件：`num_items(Items.Power) >= 30000`
