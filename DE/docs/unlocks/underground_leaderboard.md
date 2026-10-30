# Untergrund-Bestenliste
Der Untergrund hält noch größere Herausforderungen bereit. Bist du bereit, deine Bergbau- und Farmprogramme zu optimieren?
Mit dieser Freischaltung kannst du in der Tiefe um die effizientesten Methoden wetteifern.

Du kannst einen Untergrund-Bestenlisten-Lauf starten, indem du `leaderboard_run(leaderboard, filename, speedup)` aufrufst.
Dies startet eine [Simulation](docs/unlocks/simulation.md) mit festgelegten Startbedingungen. Jede Kategorie hat unterschiedliche Ziele.

Der Lauf ist erfolgreich, wenn die Erfolgsbedingung am Ende der Simulation `True` ist. Bei Erfolg wird deine Zeit zur Bestenliste hinzugefügt.
Denke daran, dein Programm zu beenden, wenn das Ziel erreicht ist.

Um Schwankungen zu verringern, müssen alle Läufe mindestens 2 Stunden dauern (in Echtzeit umgerechnet). Endet ein Lauf früher, wird er wiederholt, und die durchschnittliche Zeit wird hochgeladen.

Für die Untergrund-Bestenlisten gelten zwei besondere Bedingungen: Erstens ist Graben in der Bambus-Bestenliste nicht erlaubt, da sie an der Oberfläche stattfindet. Zweitens ist das Pflanzen in den Bestenlisten deaktiviert, die es nicht benötigen.

## Schnellster Untergrund-Reset
Automatisiere das Spiel vollständig von einem einzelnen Farmfeld bis zum erneuten Freischalten der Untergrund-Bestenlisten.

Versuche, `Unlocks.Underground_Leaderboard` so schnell wie möglich freizuschalten.

Funktionsaufruf:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Erfolgsbedingung:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Ressourcen-Bestenlisten
Diese Bestenlisten drehen sich darum, bestimmte unterirdische Ressourcen so schnell wie möglich zu farmen. Du startest mit allen Freischaltungen und den Ressourcen, die du für den Anfang brauchst.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Gold) >= 100`

## Einzel-Drohnen-Bestenlisten im Untergrund
Herausforderungen im Untergrund, bei denen du nur eine einzelne Drohne hast.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Erfolgsbedingung: `num_items(Items.Gold) >= 100`
