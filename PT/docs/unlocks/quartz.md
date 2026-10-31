[<- Ferro](docs/unlocks/iron.md) <right>[Cogumelo ->](docs/unlocks/mushroom.md)
---
# Quartzo

Seguindo além dos veios de ferro em `Grounds.Rock`, você encontra quartzo na parte inferior da camada de pedra e na `Grounds.Dirt` dura abaixo dela (verifique a dureza usando `get_hardness()` do desbloqueio [Sentidos Subterrâneos](docs/unlocks/underground_senses.md)).

O código a seguir atravessa a terra e escava até a camada de rocha. Lá, ele prospecta quartzo continuamente enquanto escava, até que a distância seja menor que 2. Por fim, imprime a distância de prospecção a que chegou.
{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "block", "n": 1}, {"item": "iron", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite"]
}
#SETUP
move(East)
move(North)
#CODE
# Escave até a camada de rocha
while get_ground_type() != Grounds.Rock:
    dig()

# Continue escavando até um veio de quartzo estar perto
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# Imprima a distância final até o veio
print(prospect_quartz())
}}

## Estrutura dos Veios
O quartzo cresce em veios semelhantes a agulhas que formam colunas verticais, tornando-os difíceis de encontrar por tentativa e erro.

## Prospecção de Quartzo
Felizmente, podemos transformar nosso ferro em algo parecido com uma vara de radiestesia para localizar esses veios com mais facilidade. O comando é `prospect_quartz()`.

`prospect_quartz()` funciona de forma diferente de `prospect_iron()`. Em vez de retornar a direção em que o drone deve se mover rumo ao minério de ferro mais próximo, retorna a distância 3D exata entre o bloco de quartzo mais próximo e o drone (distância euclidiana).

Executar `prospect_quartz()` custa 1 ferro, então use-o com moderação.

Se `prospect_quartz()` não encontrar quartzo por perto ou você não tiver ferro suficiente, ele retorna `None`.

## Estratégia
<spoiler=mostrar dica>Você pode prospectar e se mover repetidamente para ver como a distância muda. Em uma superfície plana, tentar minimizar a distância pode colocar você acima de um veio de quartzo. Você pode usar uma estratégia parecida com a busca binária para minimizar o número de chamadas de `prospect_quartz()` e a quantidade de ferro que elas consomem.

Estratégias mais elaboradas podem usar geometria 2D para encontrar a interseção entre dois ou mais círculos, ou você pode seguir o caminho difícil e usar trilateração completa para intersectar três esferas e encontrar a posição 3D exata do veio.

Observe que, para calcular uma raiz quadrada, você pode usar o operador de exponenciação. Por exemplo, para obter a raiz quadrada de 16, use `16**0.5`. Não há funções matemáticas embutidas para trigonometria ou vetores; você terá que implementá-las por conta própria. 

Observe também que pode haver vários veios nas proximidades, então, se você fizer várias medições próximas, elas podem não apontar para o mesmo veio.</spoiler>

---

[Estatísticas](docs/stats.md)      [Mineração](docs/unlocks/mining.md)      [Sentidos Subterrâneos](docs/unlocks/underground_senses.md)      [Variáveis](docs/scripting/variables.md)      [Operadores](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
