# Classement souterrain
Le monde souterrain réserve des défis encore plus grands. Es-tu prêt à optimiser tes programmes d’exploitation minière et de culture ?
Avec ce déblocage, tu peux rivaliser pour trouver les méthodes les plus efficaces dans les profondeurs.

Tu peux démarrer une course de classement souterrain en appelant `leaderboard_run(leaderboard, filename, speedup)`.
Cela lance une [simulation](docs/unlocks/simulation.md) avec des conditions de départ fixes. Chaque catégorie a des objectifs différents.

La course réussit si la condition de succès est `True` lorsque la simulation se termine. Si elle réussit, ton temps sera ajouté au classement.
N’oublie pas d’arrêter ton programme une fois l’objectif atteint.

Pour réduire la variance, toutes les courses doivent durer au moins 2 heures (en équivalent temps réel). Si une course se termine plus tôt, elle est répétée, et le temps moyen est envoyé.

Les classements souterrains ont deux conditions particulières : d’abord, le classement du bambou interdit de forer, car il se déroule en surface. Ensuite, planter est désactivé dans les classements qui n’en ont pas besoin.

## Réinitialisation souterraine la plus rapide
Automatise entièrement le jeu, depuis une unique parcelle jusqu’au nouveau déblocage des classements souterrains.

Essaie de débloquer `Unlocks.Underground_Leaderboard` aussi vite que possible.

Appel de fonction :
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Condition de succès :
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Classements de ressources
Ces classements consistent à cultiver certaines ressources souterraines le plus rapidement possible. Tu commences avec tous les déblocages et les ressources nécessaires pour te lancer.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Condition de succès : `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Condition de succès : `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Condition de succès : `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Condition de succès : `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Condition de succès : `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Condition de succès : `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Condition de succès : `num_items(Items.Gold) >= 100`

## Classements souterrains avec un seul drone
Des défis limités à un seul drone dans le monde souterrain.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Condition de succès : `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Condition de succès : `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Condition de succès : `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Condition de succès : `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Condition de succès : `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Condition de succès : `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Condition de succès : `num_items(Items.Gold) >= 100`
