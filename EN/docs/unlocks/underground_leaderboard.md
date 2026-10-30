# Underground Leaderboard
The underground holds even greater challenges. Are you prepared to optimize your mining and farming programs?
With this unlock, you can compete for the most efficient methods in the depths.

You can start an underground leaderboard run by calling `leaderboard_run(leaderboard, filename, speedup)`.
This starts a [simulation](docs/unlocks/simulation.md) with fixed starting conditions. Each category has different goals.

The run succeeds if the success condition is `True` when the simulation ends. Your time will be added to the leaderboard upon success.
Remember to terminate your program when the goal is reached.

To reduce variance, all runs are required to run for at least 2 hours (real-time equivalent). If a run is completed earlier, it will be repeated, and the average time will be uploaded.

The underground leaderboards have two special conditions: First, the bamboo leaderboard disallows digging, because it takes place above ground. Second, planting is disabled for the leaderboards that don't need it.

## Fastest Underground Reset
Completely automate the game from a single farm plot to unlocking the underground leaderboards again.

Try to unlock `Unlocks.Underground_Leaderboard` as fast as possible.

Function Call:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Success Condition:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Resource Leaderboards
These leaderboards focus on farming specific underground resources as quickly as possible. You start with everything unlocked and the necessary resources to begin.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Success Condition: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Success Condition: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Success Condition: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Success Condition: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Success Condition: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Success Condition: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Success Condition: `num_items(Items.Gold) >= 100`

## Single Drone Underground Leaderboards
Challenges limited to a single drone in the underground.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Success Condition: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Success Condition: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Success Condition: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Success Condition: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Success Condition: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Success Condition: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Success Condition: `num_items(Items.Gold) >= 100`
