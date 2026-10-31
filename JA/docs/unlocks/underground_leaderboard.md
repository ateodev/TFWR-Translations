# 地下リーダーボード
地下には、さらに大きな課題が待ち受けています。採掘と農業のプログラムを最適化する準備はできていますか？
このアンロックで、地中深くで最も効率的な方法を競えるようになります。

`leaderboard_run(leaderboard, filename, speedup)` を呼び出すことで、地下リーダーボードランを開始できます。
これは、`simulate()` に似た[シミュレーション](docs/unlocks/simulation.md)を開始しますが、開始条件は固定されています。各リーダーボードカテゴリには、異なる開始条件と成功条件があります。

シミュレーション終了時に成功条件が `True` であれば、リーダーボードランは成功します。

目標に到達してもシミュレーションは自動的に終了しません。プログラムが終了するようにする必要があります。
ランが成功した場合、あなたのタイムがリーダーボードに追加されます。

ばらつきを減らすため、すべてのランはシミュレーション内で合計2時間以上実行する必要があります。シミュレーションは加速できるので、現実の時間で2時間はかかりません。早く終了したランは、シミュレーション時間が合計2時間に達するまで繰り返されます。全ランの平均時間がスコアとしてアップロードされます。

これは、`Leaderboards.Rice_Single` のリーダーボードに載るためのセットアップ例です。

![|x400](UndergroundLeaderboardSetup)

## 最速地下リセット
地下リセットは最も名誉あるカテゴリです。このカテゴリでは、単一の農地から始めて `Unlocks.Underground_Leaderboard` を再びアンロックするまで、採掘のアンロックツリーを完全に自動化します。

すべてをアンロックする必要はなく、できるだけ早く `Unlocks.Underground_Leaderboard` をアンロックするようにしてください。

`num_unlocked(unlock) > 0` を使って何かがアンロックされているかを確認でき、`get_cost()` をアンロックに使用してコストを確認できるので、適切なアイテムを自動的に栽培できます。

`unlock()` はアンロックツリーの依存関係を考慮しません。たとえば、`Unlocks.Water` より先に `Unlocks.Fertilizer` をアンロックできます。

関数呼び出し:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

同等のシミュレーション:
`unlocks = {}
items = {}
globals = {}
#負のシード値はランダムシードを意味します
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功条件:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## 鉱石
このリーダーボードでは、鉱石、特に石英を集める腕前が試されます。地面の生成が変更されていて、地層から石炭、鉄、石英の順に手に入ります。

すべてがアンロックされた状態から始め、できるだけ早く `20000` 個の石英を獲得します。

関数呼び出し:
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

同等のシミュレーション:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功条件:
`num_items(Items.Quartz) >= 20000`

## 宝物の地図
このリーダーボードは、すべてがアンロックされ、大量のパワーを持った状態から始まります。地面の生成が変更されていて、宝物の地図がたくさんあります。

ワールドサイズは8x8で、ドローンは1台だけです。目標は、できるだけ早く `115000` ゴールドを獲得することです。

関数呼び出し:
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

同等のシミュレーション:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

成功条件:
`num_items(Items.Gold) >= 115000`

## リソースリーダーボード
これらのリーダーボードでは、特定のリソースをできるだけ早く集めることに挑みます。すべてがアンロックされ、大量のパワーを持った状態でスタートします。唯一の例外はピラミッドのリーダーボードで、ピラミッドを修復して自分でパワーを生み出す必要があります。

目標は、決められた量のリソースを獲得することです。

いつもどおり、目標に到達したらプログラムが終了するようにする必要があります。目標に到達していても、プログラムが終了するまでランは終わりません。

これらのリーダーボードでは、目的のリソースが何度でも見つかるように地面の生成が変更されています。つまり、`clear()` を使う必要はありません。たとえば、稲のリーダーボードは粘土の層だけでできています。

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
成功条件: `num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
竹のリーダーボードでは掘ることができないので注意してください。

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
成功条件: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
成功条件: `num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
成功条件: `num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
成功条件: `num_items(Items.Power) >= 150000`

## シングルドローン地下リーダーボード
シングルドローンで農業を行うリーダーボードもあります。ドローンは1台、農場は8x8で、一定量のリソースをできるだけ早く獲得する必要があります。

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
成功条件: `num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
成功条件: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
成功条件: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
成功条件: `num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
成功条件: `num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
成功条件: `num_items(Items.Power) >= 30000`

