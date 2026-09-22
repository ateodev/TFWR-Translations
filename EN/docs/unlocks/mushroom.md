[<- Quartz](docs/unlocks/quartz.md) <right>[Dynamite ->](docs/unlocks/dynamite.md)
---
# Mushroom

Many types of mushrooms grow in colonies underground. Look for a stratum of `Grounds.Mushroom` while digging. You can `measure()` the ground to get the mushroom type as a number, starting from `0`.

Mushrooms of the same type like to be together, but they are a bit too shy to grow on top of each other. Push a mushroom block on top of another mushroom block of the same type and they will disappear, earning you mushrooms as a reward.

You can use `can_push(direction)` to check whether the block under the drone can be pushed and whether anything is blocking it in the given direction. `push(direction)` pushes the block and returns whether the push was successful.

Blocks cannot be pushed upward, and the push will fail if another block is in the way. When pushed into the air, blocks fall and land on the next block below them.

Remember that you can call `place(Grounds.Dirt)` to place blocks below the drone. This can be useful for filling in holes so that you can push blocks over them.

---

[Stats](docs/stats.md)      [Underground Senses](docs/unlocks/underground_senses.md)      [Dictionaries](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
