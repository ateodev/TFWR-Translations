[<- Mineração](docs/unlocks/mining.md) <right>[Ferro ->](docs/unlocks/iron.md)
<right>[Salto ->](docs/unlocks/jump.md)
---
# Carvão

Diferentes minérios estão escondidos no subsolo, esperando que você os encontre e escave. Se você escavar através da superfície até `Grounds.Dirt`, o primeiro minério que encontra é o carvão.

Seus veios formam camadas horizontais com 1 bloco de espessura que você precisa encontrar por acaso enquanto escava a terra. Os blocos de carvão de uma camada ficam quase sempre diretamente lado a lado, mas alguns também podem estar ligados apenas na diagonal.

Você não precisa fazer nada de especial para minerar carvão, basta executar `dig()` enquanto o drone está diretamente em cima de um bloco de `Grounds.Coal`. Use `get_ground_type()` para verificar o que está embaixo do drone e `get_ground_type(direction)` para verificar os quatro blocos adjacentes.

Observe que você só recebe carvão pelos blocos de carvão que escava diretamente, e não pelos blocos que desabam ao redor do drone. Lembre-se disso ao pensar em como minerar carvão, para maximizar os blocos de carvão minerados em relação aos que se perdem nos desabamentos.

As minas de carvão crescem proporcionalmente ao tamanho da fazenda, então considere continuar desbloqueando [Expandir](unlocks/expand) para aumentar a quantidade de carvão que você pode minerar.

O programa a seguir é um bom ponto de partida para encontrar carvão. Ele escava para baixo em busca de uma camada de carvão e depois escava a leste e a oeste na esperança de encontrar mais.

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2
}
#SETUP
move(North)
move(East)
move(East)
#CODE
while get_ground_type() != Grounds.Coal:
    dig()
do_a_flip()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

Uma estratégia simples, principalmente para fazendas menores, é escavar todos os blocos na profundidade em que você encontrou um bloco de carvão. Para ser mais eficiente, você pode registrar onde viu blocos de carvão usando `get_ground_type(direction)` e evitar perder tempo passando por blocos de terra. Tome cuidado redobrado para não perder as ligações na diagonal, que você vai perder se andar apenas sobre blocos de carvão.

---

[Estatísticas](docs/stats.md)      [Mineração](docs/unlocks/mining.md)      [Sentidos Subterrâneos](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
