# Untergrund-Bestenliste
Der Untergrund hält noch größere Herausforderungen bereit. Bist du bereit, deine Bergbau- und Farmprogramme zu optimieren?
Mit dieser Freischaltung kannst du in der Tiefe um die effizientesten Methoden wetteifern.

Du kannst einen Untergrund-Bestenlisten-Lauf starten, indem du `leaderboard_run(leaderboard, filename, speedup)` aufrufst.
Dies startet eine [Simulation](docs/unlocks/simulation.md), ähnlich wie `simulate()`, außer dass die Startbedingungen festgelegt sind. Jede Bestenlisten-Kategorie hat unterschiedliche Start- und Erfolgsbedingungen.

Der Bestenlisten-Lauf ist erfolgreich, wenn die Erfolgsbedingung am Ende der Simulation `True` ist. 

Die Simulation wird NICHT automatisch enden, wenn das Ziel erreicht ist. Du musst sicherstellen, dass das Programm terminiert.
Wenn der Lauf erfolgreich ist, wird deine Zeit zur Bestenliste hinzugefügt.

Um Schwankungen zu verringern, müssen alle Durchläufe mindestens 2 Stunden simulierter Zeit umfassen. Du kannst die Simulation beschleunigen, sodass dies in Echtzeit nicht so lange dauert. Endet ein Durchlauf früher, wird er wiederholt, bis insgesamt 2 Stunden simulierte Zeit erreicht sind. Anschließend wird die durchschnittliche Zeit aller Durchläufe als dein Ergebnis hochgeladen.

Hier ist ein Beispiel-Setup, das dich auf die Bestenliste `Leaderboards.Rice_Single` bringt.

![|x400](UndergroundLeaderboardSetup)

## Schnellster Untergrund-Reset
Der Untergrund-Reset ist die prestigeträchtigste Kategorie. In dieser Kategorie automatisierst du den Bergbau-Forschungsbaum vollständig. Du beginnst mit einem einzelnen Farmfeld, und der Lauf endet, wenn du `Unlocks.Underground_Leaderboard` erneut freischaltest.

Du musst nicht alles freischalten, versuche einfach, `Unlocks.Underground_Leaderboard` so schnell wie möglich freizuschalten.

Denke daran, dass du `num_unlocked(unlock) > 0` verwenden kannst, um zu prüfen, ob etwas freigeschaltet ist. Außerdem kannst du `get_cost()` auf Freischaltungen anwenden, um zu sehen, was sie kosten, damit du automatisch die richtigen Gegenstände farmen kannst.

`unlock()` berücksichtigt Abhängigkeiten im Forschungsbaum nicht. Du kannst beispielsweise `Unlocks.Fertilizer` vor `Unlocks.Water` freischalten.

Funktionsaufruf:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Äquivalente Simulation:
`unlocks = {}
items = {}
globals = {}
#ein negativer Seed-Wert bedeutet ein zufälliger Seed
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Erfolgsbedingung:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Erze
Diese Bestenliste testet dein Können beim Farmen von Erzen, insbesondere von Quarz. Sie verändert die Bodengenerierung so, dass dir die Bodenschichten zuerst Kohle, dann Eisen und dann Quarz liefern, in genau dieser Reihenfolge.

Beginne mit allem freigeschaltet und farme `20000` Quarz so schnell du kannst.

Funktionsaufruf:
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

Äquivalente Simulation:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Erfolgsbedingung:
`num_items(Items.Quartz) >= 20000`

## Schatzkarte
Diese Bestenliste beginnt mit allem freigeschaltet und viel Energie. Sie verändert die Bodengenerierung so, dass es sehr viele Schatzkarten gibt.

Sie findet auf einer 8x8-Welt mit einer einzelnen Drohne statt. Das Ziel ist es, `115000` Gold so schnell wie möglich zu farmen.

Funktionsaufruf:
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

Äquivalente Simulation:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Erfolgsbedingung:
`num_items(Items.Gold) >= 115000`

## Ressourcen-Bestenlisten
Diese Bestenlisten drehen sich darum, bestimmte Ressourcen so schnell wie möglich zu farmen. Du startest mit allen Freischaltungen und viel Energie. Die einzige Ausnahme ist die Pyramiden-Bestenliste, bei der du die Energie selbst erzeugen musst, indem du Pyramiden wiederherstellst.

Das Ziel ist es, eine festgelegte Menge an Ressourcen zu farmen.

Wie immer musst du sicherstellen, dass dein Programm terminiert, wenn du das Ziel erreichst. Ein Lauf ist nicht beendet, bis das Programm endet, auch wenn das Ziel erreicht ist.

Diese Bestenlisten verändern die Bodengenerierung so, dass die gewünschte Ressource immer wieder gefunden werden kann. Du musst also nicht `clear()` verwenden. Die Reis-Bestenliste besteht zum Beispiel nur aus Tonschichten.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
Beachte, dass in der Bambus-Bestenliste das Graben nicht erlaubt ist.

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Power) >= 150000`

## Einzel-Drohnen-Bestenlisten im Untergrund
Es gibt auch Bestenlisten für das Farmen mit einer einzelnen Drohne. Du bekommst nur eine Drohne und eine 8x8-Farm und musst eine bestimmte Menge an Ressourcen so schnell wie möglich farmen.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Power) >= 30000`

