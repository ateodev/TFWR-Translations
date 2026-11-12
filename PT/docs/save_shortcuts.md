# Cópias com Atalhos
O app Atalhos pode copiar seus jogos salvos para um lugar que você escolher, como o iCloud Drive, toda vez que você sai do jogo. Ele faz isso sozinho, sem perguntar. Isso faz parte do jogo completo.

## Como configurar
1. Em **Atalhos**, toque em + para criar um novo atalho, toque em **Editar** no canto superior direito e adicione a ação do jogo **Obter último jogo salvo**.
2. Adicione **Salvar Arquivo** e toque na seta dela. Desative **Perguntar Onde Salvar**, escolha uma pasta e ative **Substituir Se o Arquivo Existir**.
3. Toque em **Buscar** na parte de baixo, depois em **Automação**, e em **Apps** escolha **App**.
4. Na linha que aparece, toque em **App** e escolha o jogo, depois toque em **Aberto** e escolha **Fechado**.

Antes do iOS 27, crie a automação na aba **Automação**: escolha **App**, o jogo, só **For Fechado** e **Executar Imediatamente**, e adicione a ela as ações dos passos 1 e 2. No iOS 16, desative **Perguntar ao Executar** em vez disso.

Cada cópia é um zip com o nome do seu jogo salvo, então você mantém uma cópia atual de cada jogo salvo.

## Guardar cópias antigas
Coloque a variável **Data Atual** no caminho da pasta de **Salvar Arquivo**. As cópias de outra data vão então para uma pasta só delas, e as antigas ficam.

## Mais ações
**Obter jogo salvo** pega um jogo salvo pelo nome. **Obter jogos salvos** pega todos os jogos salvos, ou só os alterados desde uma data.

## Trazer uma cópia de volta
As ações só copiam seus jogos salvos para fora. Para trazer uma cópia de volta, toque em “Importar” na tela de carregamento e escolha o zip dela.

O salvamento na nuvem mantém seus dispositivos no mesmo progresso. Uma cópia do Atalhos é um arquivo seu, guardado onde você escolher, como histórico ou para o jogo de PC.
