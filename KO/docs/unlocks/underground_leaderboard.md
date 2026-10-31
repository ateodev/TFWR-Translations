# 지하 리더보드
지하에는 훨씬 더 큰 도전이 기다리고 있어요. 채광과 농사 프로그램을 최적화할 준비가 되셨나요?
이 해금 항목으로 깊은 지하에서 가장 효율적인 방법을 두고 경쟁할 수 있어요.

`leaderboard_run(leaderboard, filename, speedup)`을 호출하여 지하 리더보드 런을 시작할 수 있어요.
이것은 `simulate()`와 비슷한 [시뮬레이션](docs/unlocks/simulation.md)을 시작하지만, 시작 조건이 고정되어 있어요. 리더보드 카테고리마다 시작 조건과 성공 조건이 달라요.

리더보드 런은 시뮬레이션이 끝날 때 성공 조건이 `True`이면 성공해요. 

목표에 도달해도 시뮬레이션은 절대 자동으로 끝나지 않아요. 프로그램이 반드시 종료되도록 해야 해요.
런이 성공하면 여러분의 시간이 리더보드에 추가될 거예요.

편차를 줄이기 위해 모든 런은 시뮬레이션 시간으로 최소 2시간을 채워야 해요. 시뮬레이션 속도를 높일 수 있으니 실제로는 그렇게 오래 걸리지 않아요. 런이 더 일찍 끝나면 총 시뮬레이션 시간이 2시간에 도달할 때까지 반복돼요. 그런 다음 모든 런의 평균 시간이 점수로 업로드돼요.

다음은 `Leaderboards.Rice_Single` 리더보드에 기록을 올릴 수 있는 설정 예시예요.

![|x400](UndergroundLeaderboardSetup)

## 가장 빠른 지하 리셋
지하 리셋은 가장 명예로운 카테고리예요. 이 카테고리에서는 단 하나의 농지에서 시작하여 `Unlocks.Underground_Leaderboard`를 다시 해금할 때까지 채광 해금 트리를 완전히 자동화해야 해요.

모든 것을 해금할 필요는 없어요. 가능한 한 빨리 `Unlocks.Underground_Leaderboard`를 해금하려고 노력하세요.

`num_unlocked(unlock) > 0`으로 무언가가 해금되었는지 확인할 수 있다는 걸 기억하세요. 해금 항목에 `get_cost()`를 사용하면 비용을 확인할 수 있어서, 필요한 아이템을 자동으로 모을 수 있어요.

`unlock()`은 기술 트리의 선행 조건을 신경 쓰지 않아요. 예를 들어 `Unlocks.Water`보다 먼저 `Unlocks.Fertilizer`를 해금할 수 있어요.

함수 호출:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

동등한 시뮬레이션:
`unlocks = {}
items = {}
globals = {}
#음수 시드 값은 무작위 시드를 의미해요
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

성공 조건:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## 광석
이 리더보드는 광석, 특히 석영을 모으는 실력을 시험해요. 땅 생성 방식이 바뀌어서 땅의 층에서 석탄, 철, 석영이 이 순서대로 나와요.

모든 것이 해금된 상태로 시작해서 가능한 한 빨리 석영 `20000`개를 모으세요.

함수 호출:
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

동등한 시뮬레이션:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

성공 조건:
`num_items(Items.Quartz) >= 20000`

## 보물지도
이 리더보드는 모든 것이 해금되어 있고 파워가 많은 상태로 시작해요. 땅 생성 방식이 바뀌어서 보물지도가 아주 많이 나와요.

드론 한 대로 8x8 크기의 세계에서 진행돼요. 목표는 가능한 한 빨리 골드 `115000`개를 모으는 거예요.

함수 호출:
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

동등한 시뮬레이션:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

성공 조건:
`num_items(Items.Gold) >= 115000`

## 자원 리더보드
이 리더보드들은 특정 자원을 가능한 한 빨리 모으는 데 집중해요. 모든 것이 해금되어 있고 파워가 많은 상태로 시작해요. 유일한 예외는 피라미드 리더보드로, 피라미드를 복원해서 파워를 직접 만들어야 해요.

목표는 정해진 양의 자원을 모으는 거예요.

언제나처럼 목표에 도달하면 프로그램이 종료되도록 해야 해요. 목표에 도달했더라도 프로그램이 끝나기 전까지는 런이 끝나지 않아요.

이 리더보드들은 원하는 자원을 계속해서 찾을 수 있도록 땅 생성 방식이 바뀌어 있어요. 그래서 `clear()`를 할 필요가 없어요. 예를 들어 쌀 리더보드는 점토층으로만 이루어져 있어요.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
성공 조건: `num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
대나무 리더보드에서는 굴착이 허용되지 않는다는 점에 유의하세요.

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
성공 조건: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
성공 조건: `num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
성공 조건: `num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
성공 조건: `num_items(Items.Power) >= 150000`

## 싱글 드론 지하 리더보드
드론 하나로 농사를 짓는 리더보드도 있어요. 드론 한 대와 8x8 농장만 주어지며, 정해진 양의 자원을 가능한 한 빨리 모아야 해요.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
성공 조건: `num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
성공 조건: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
성공 조건: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
성공 조건: `num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
성공 조건: `num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
성공 조건: `num_items(Items.Power) >= 30000`

