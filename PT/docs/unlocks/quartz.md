[<- Ferro](docs/unlocks/iron.md) <right>[Cogumelo ->](docs/unlocks/mushroom.md)
---
# Quartzo

Seguindo além dos veios de ferro em `Grounds.Rock`, você encontra quartzo na parte inferior da camada de pedra e na `Grounds.Dirt` dura abaixo dela (verifique a dureza usando `get_hardness()` do desbloqueio [Sentidos Subterrâneos](docs/unlocks/underground_senses.md)).

O quartzo cresce em veios semelhantes a agulhas que formam colunas verticais, tornando-os difíceis de encontrar por tentativa e erro.

Felizmente, podemos transformar nosso ferro em algo parecido com uma vara de radiestesia para localizar esses veios com mais facilidade. O comando é `prospect_quartz()`.

`prospect_quartz()` funciona de forma diferente de `prospect_iron()`. Em vez de retornar a direção do quartzo mais próximo, retorna a distância euclidiana (distância 3D) até ele. Executar `prospect_quartz()` custa 1 ferro, então use-o com moderação.

Se `prospect_quartz()` não encontrar quartzo por perto ou você não tiver ferro suficiente, ele retorna `None`.

O código a seguir faz o drone atravessar a terra e escavar fundo na camada de rocha. Com um pouco de sorte, haverá um veio de quartzo por perto, e o drone imprimirá a distância até ele.

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
    "items": [{"item": "hay", "n": 100}, {"item": "iron", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite"]
}

#CODE
move(East)
move(North)
while get_ground_type() != Grounds.Rock:
    dig()
for i in range(30):
    dig()
do_a_flip()
do_a_flip()
print(prospect_quartz())
}}

Você pode prospectar e se mover repetidamente e ver como a distância muda, para saber se está se aproximando ou se afastando de um veio. Você pode usar geometria 2D para encontrar a interseção entre dois ou mais círculos, achar a posição horizontal de um veio e escavar para baixo. Ou pode usar trilateração completa para intersectar três esferas e encontrar a posição 3D exata.

Observe que não há funções matemáticas básicas para raiz quadrada, trigonometria ou vetores; você terá que implementá-las por conta própria. Observe também que pode haver vários veios nas proximidades, então, se você fizer várias medições próximas, elas podem não apontar para o mesmo veio e acabar te confundindo.

---

[Estatísticas](docs/stats.md)      [Mineração](docs/unlocks/mining.md)      [Sentidos Subterrâneos](docs/unlocks/underground_senses.md)      [Variáveis](docs/scripting/variables.md)      [Operadores](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
