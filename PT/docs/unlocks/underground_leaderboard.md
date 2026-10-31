# Placar de Líderes Subterrâneo
O subsolo guarda desafios ainda maiores. Você está preparado para otimizar seus programas de mineração e cultivo?
Com este desbloqueio, você pode competir pelos métodos mais eficientes nas profundezas.

Você pode iniciar uma tentativa no placar de líderes subterrâneo chamando `leaderboard_run(leaderboard, filename, speedup)`.
Isso inicia uma [simulação](docs/unlocks/simulation.md) parecida com `simulate()`, mas com condições iniciais fixas. Cada categoria do placar tem condições iniciais e de sucesso diferentes.

A tentativa no placar de líderes é bem-sucedida se a condição de sucesso for `True` quando a simulação terminar. 

A simulação NÃO terminará automaticamente quando o objetivo for alcançado. Você deve garantir que o programa termine.
Se a tentativa for bem-sucedida, seu tempo será adicionado ao placar de líderes.

Para reduzir a variação, todas as tentativas devem abranger pelo menos 2 horas de tempo simulado. Você pode acelerar a simulação, então ela não levará tudo isso em tempo real. Se uma tentativa terminar antes, ela será repetida até o tempo simulado total chegar a 2 horas. A média de tempo de todas as tentativas será enviada como sua pontuação.

Aqui está um exemplo de configuração que colocará você no placar `Leaderboards.Rice_Single`.

![|x400](UndergroundLeaderboardSetup)

## Reset Subterrâneo Mais Rápido
O reset subterrâneo é a categoria de maior prestígio. Nela, você automatiza completamente a árvore de desbloqueios de mineração, começando com um único quadrado de fazenda e terminando quando desbloqueia `Unlocks.Underground_Leaderboard` novamente.

Você não precisa desbloquear tudo, apenas tente desbloquear `Unlocks.Underground_Leaderboard` o mais rápido possível.

Lembre-se de que você pode usar `num_unlocked(unlock) > 0` para verificar se algo está desbloqueado. Também pode usar `get_cost()` em desbloqueios para consultar o custo deles e produzir automaticamente os itens certos.

`unlock()` não considera as dependências da árvore de tecnologias. Por exemplo, é possível desbloquear `Unlocks.Fertilizer` antes de `Unlocks.Water`.

Chamada de Função:
`leaderboard_run(Leaderboards.Fastest_Underground_Reset, filename, speedup)`

Simulação Equivalente:
`unlocks = {}
items = {}
globals = {}
#um valor de semente negativo significa uma semente aleatória
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Condição de Sucesso:
`num_unlocked(Unlocks.Underground_Leaderboard) > 0`

## Minérios
Este placar testa suas habilidades de extrair minérios, principalmente quartzo. Ele modifica a geração do solo para que as camadas forneçam carvão, depois ferro e depois quartzo, nessa ordem.

Comece com tudo desbloqueado e obtenha `20000` de quartzo o mais rápido que puder.

Chamada de Função:
`leaderboard_run(Leaderboards.Ores, filename, speedup)`

Simulação Equivalente:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Condição de Sucesso:
`num_items(Items.Quartz) >= 20000`

## Mapa do Tesouro
Este placar começa com tudo desbloqueado e muita energia. Ele modifica a geração do solo para que haja muitos mapas do tesouro.

Ele acontece em um mundo de tamanho 8x8 com um único drone. O objetivo é obter `115000` de ouro o mais rápido possível.

Chamada de Função:
`leaderboard_run(Leaderboards.Treasure_Map, filename, speedup)`

Simulação Equivalente:
`unlocks = Unlocks
items = {Items.Power: 1000000000}
globals = {}
seed = -1
simulate(filename, unlocks, items, globals, seed, speedup)`

Condição de Sucesso:
`num_items(Items.Gold) >= 115000`

## Placares de Líderes de Recursos
Estes placares se concentram em cultivar recursos específicos o mais rápido possível. Você começa com tudo desbloqueado e muita energia. A única exceção é o placar das pirâmides, em que você precisa produzir a energia por conta própria restaurando pirâmides.

O objetivo é cultivar uma quantidade definida de recursos.

Como sempre, você precisa garantir que seu programa termine quando atingir o objetivo. Uma tentativa não termina até que o programa termine, mesmo que o objetivo seja alcançado.

Estes placares modificam a geração do solo para que o recurso desejado possa ser encontrado várias e várias vezes. Isso significa que não é preciso usar `clear()`. Por exemplo, o placar do arroz consiste apenas em camadas de argila.

### `Leaderboards.Rice`
`leaderboard_run(Leaderboards.Rice, filename, speedup)`
Condição de Sucesso: `num_items(Items.Rice) >= 2000000`

### `Leaderboards.Bamboo`
Observe que o placar do bambu não permite escavar.

`leaderboard_run(Leaderboards.Bamboo, filename, speedup)`
Condição de Sucesso: `num_items(Items.Bamboo) >= 500000000`

### `Leaderboards.Dynamite`
`leaderboard_run(Leaderboards.Dynamite, filename, speedup)`
Condição de Sucesso: `num_items(Items.Dynamite) >= 10000000`

### `Leaderboards.Mushrooms`
`leaderboard_run(Leaderboards.Mushrooms, filename, speedup)`
Condição de Sucesso: `num_items(Items.Mushroom) >= 240000`

### `Leaderboards.Pyramids`
`leaderboard_run(Leaderboards.Pyramids, filename, speedup)`
Condição de Sucesso: `num_items(Items.Power) >= 150000`

## Placares de Líderes Subterrâneos de Drone Único
Também há placares para produzir com um único drone. Você recebe apenas um drone e uma fazenda 8x8 e precisa produzir certa quantidade de recursos o mais rápido possível.

### `Leaderboards.Rice_Single`
`leaderboard_run(Leaderboards.Rice_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Rice) >= 100000`

### `Leaderboards.Ores_Single`
`leaderboard_run(Leaderboards.Ores_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Quartz) >= 4000`

### `Leaderboards.Bamboo_Single`
`leaderboard_run(Leaderboards.Bamboo_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Bamboo) >= 25000000`

### `Leaderboards.Dynamite_Single`
`leaderboard_run(Leaderboards.Dynamite_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Dynamite) >= 100000`

### `Leaderboards.Mushrooms_Single`
`leaderboard_run(Leaderboards.Mushrooms_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Mushroom) >= 30000`

### `Leaderboards.Pyramids_Single`
`leaderboard_run(Leaderboards.Pyramids_Single, filename, speedup)`
Condição de Sucesso: `num_items(Items.Power) >= 30000`

