[<- Rice](docs/unlocks/rice.md)
---
# Pyramids

The underground now contains ancient pyramidal structures from which you can harvest energy!

Pyramids are made from sand blocks (`Grounds.Sand`). Below the pyramid itself is a foundation layer of limestone (`Grounds.Limestone`). Because they are old and eroded, you will find them only in a partially destroyed state: the foundation layer is always present, but the pyramid itself will have several vertical holes in the sand.

When you fill these holes and restore the pyramid to its previous state, it destroys itself and you receive power as a reward.

You can restore a pyramid by placing blocks with the command `place(Grounds.Sand)`. Sand is a special block that will cave in immediately when it is not supported properly. Whenever you place a sand block, it must either be placed directly on limestone, or on a 3x3 of sand blocks.

Once a sand block is in place, it is fine to dig around it, though this causes cave-ins according to the usual cave-in rules. It might be a good idea to think about how you're going to complete the pyramid without destroying blocks that you've already restored.

A correctly restored pyramid consists of a square limestone foundation with odd-numbered side lengths—for example, 5x5. Above it is a layer of sand blocks of the same size (5x5), followed by progressively smaller layers: 3x3, then 1x1.

When a pyramid is completed, it crumbles away and a large sunflower is spawned in the middle. You can harvest it to receive power. The larger the pyramid you completed, the more power you receive.

---

[Stats](docs/stats.md)      [Underground Senses](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [use_item()](functions/use_item)
