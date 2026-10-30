# 地下リーダーボード
地下には、さらに大きな課題が待ち受けています。採掘と農業のプログラムを最適化する準備はできていますか？
このアンロックで、地中深くで最も効率的な方法を競えるようになります。

`leaderboard_run(leaderboard, filename, speedup)` を呼び出すことで、地下リーダーボードランを開始できます。
これは、開始条件が固定された[シミュレーション](docs/unlocks/simulation.md)を開始します。カテゴリごとに目標が異なります。

シミュレーション終了時に成功条件が `True` であれば、ランは成功します。成功すると、あなたのタイムがリーダーボードに追加されます。
目標に到達したら、プログラムを終了させるのを忘れないでください。

ばらつきを減らすため、すべてのランは2時間以上（現実の時間に換算して）実行する必要があります。それより早く完了したランは繰り返され、平均時間がアップロードされます。

地下リーダーボードには2つの特別な条件があります。1つ目に、竹のリーダーボードは地上で行われるため、掘ることができません。2つ目に、植え付けが不要なリーダーボードでは植え付けが無効になっています。

## 最速地下リセット
単一の農地から地下リーダーボードを再びアンロックするまで、ゲームを完全に自動化します。

できるだけ早く `Unlocks.Underground_Leaderboard` をアンロックするようにしてください。

関数呼び出し:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

成功条件:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## リソースリーダーボード
これらのリーダーボードでは、特定の地下リソースをできるだけ早く集めることに挑みます。すべてがアンロックされた状態で、始めるのに必要なリソースを持ってスタートします。

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
成功条件: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
成功条件: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
成功条件: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
成功条件: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
成功条件: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
成功条件: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
成功条件: `num_items(Items.Gold) >= 100`

## シングルドローン地下リーダーボード
地下でドローン1台だけを使うチャレンジです。

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
成功条件: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
成功条件: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
成功条件: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
成功条件: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
成功条件: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
成功条件: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
成功条件: `num_items(Items.Gold) >= 100`
