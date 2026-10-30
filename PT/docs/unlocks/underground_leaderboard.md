# Placar de Líderes Subterrâneo
O subsolo guarda desafios ainda maiores. Você está preparado para otimizar seus programas de mineração e cultivo?
Com este desbloqueio, você pode competir pelos métodos mais eficientes nas profundezas.

Você pode iniciar uma tentativa no placar de líderes subterrâneo chamando `leaderboard_run(leaderboard, filename, speedup)`.
Isso inicia uma [simulação](docs/unlocks/simulation.md) com condições iniciais fixas. Cada categoria tem objetivos diferentes.

A tentativa é bem-sucedida se a condição de sucesso for `True` quando a simulação terminar. Se for bem-sucedida, seu tempo será adicionado ao placar de líderes.
Lembre-se de encerrar o programa quando o objetivo for alcançado.

Para reduzir a variação, todas as tentativas devem durar pelo menos 2 horas (equivalente em tempo real). Se uma tentativa terminar antes, ela será repetida, e a média de tempo será enviada.

Os placares de líderes subterrâneos têm duas condições especiais: primeiro, o placar do bambu não permite escavar, porque acontece na superfície. Segundo, o plantio fica desativado nos placares que não precisam dele.

## Reset Subterrâneo Mais Rápido
Automatize completamente o jogo, começando com um único quadrado de fazenda até desbloquear os placares de líderes subterrâneos novamente.

Tente desbloquear `Unlocks.Underground_Leaderboard` o mais rápido possível.

Chamada de Função:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Condição de Sucesso:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Placares de Líderes de Recursos
Estes placares se concentram em cultivar recursos subterrâneos específicos o mais rápido possível. Você começa com tudo desbloqueado e com os recursos iniciais necessários.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Condição de Sucesso: `num_items(Items.Rice) >= 25000000`

### `Leaderboards.Ores`
`leaderboard_run(Leaderboards.Ores, filename, speedup)`
Condição de Sucesso: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo`
`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Condição de Sucesso: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Condição de Sucesso: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Condição de Sucesso: `num_items(Items.Mushroom) >= 120000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Condição de Sucesso: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures`
`leaderboard_run(Leaderboards.Treasures, filename, speedup)`
Condição de Sucesso: `num_items(Items.Gold) >= 100`

## Placares de Líderes Subterrâneos de Drone Único
Desafios limitados a um único drone no subsolo.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Rice) >= 1250000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Quartz) >= 200`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Dynamite) >= 100`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Mushroom) >= 60000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Power) >= 100`

### `Leaderboards.Treasures_Single`
`leaderboard_run(Leaderboards.Treasures_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Gold) >= 100`
