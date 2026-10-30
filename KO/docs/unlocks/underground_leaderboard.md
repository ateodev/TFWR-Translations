# 지하 리더보드
지하에는 훨씬 더 큰 도전이 기다리고 있어요. 채광과 농사 프로그램을 최적화할 준비가 되셨나요?
이 해금 항목으로 깊은 지하에서 가장 효율적인 방법을 두고 경쟁할 수 있어요.

`leaderboard_run(leaderboard, filename, speedup)`을 호출하여 지하 리더보드 런을 시작할 수 있어요.
이것은 시작 조건이 고정된 [시뮬레이션](docs/unlocks/simulation.md)을 시작해요. 카테고리마다 목표가 달라요.

런은 시뮬레이션이 끝날 때 성공 조건이 `True`이면 성공해요. 성공하면 여러분의 시간이 리더보드에 추가될 거예요.
목표에 도달하면 프로그램을 종료하는 것을 잊지 마세요.

편차를 줄이기 위해 모든 런은 최소 2시간(실제 시간 기준) 동안 실행되어야 해요. 런이 더 일찍 끝나면 반복되고, 평균 시간이 업로드돼요.

지하 리더보드에는 두 가지 특별한 조건이 있어요. 첫째, 대나무 리더보드는 지상에서 진행되므로 굴착이 허용되지 않아요. 둘째, 심기가 필요 없는 리더보드에서는 심기를 사용할 수 없어요.

## 가장 빠른 지하 리셋
단 하나의 농지에서 시작하여 지하 리더보드를 다시 해금할 때까지 게임을 완전히 자동화하세요.

가능한 한 빨리 `Unlocks.Underground_Leaderboard`를 해금하려고 노력하세요.

함수 호출:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

성공 조건:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## 자원 리더보드
이 리더보드들은 특정 지하 자원을 가능한 한 빨리 모으는 데 집중해요. 모든 것이 해금되어 있고 시작에 필요한 자원을 가진 상태로 시작해요.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
성공 조건: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
성공 조건: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
성공 조건: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
성공 조건: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
성공 조건: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
성공 조건: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
성공 조건: `num_items(Items.Gold) >= 100`

## 싱글 드론 지하 리더보드
지하에서 드론 하나만 사용할 수 있는 도전이에요.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
성공 조건: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
성공 조건: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
성공 조건: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
성공 조건: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
성공 조건: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
성공 조건: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
성공 조건: `num_items(Items.Gold) >= 100`
