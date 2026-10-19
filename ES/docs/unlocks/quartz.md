[<- Hierro](docs/unlocks/iron.md) <right>[Hongo ->](docs/unlocks/mushroom.md)
---
# Cuarzo

Más abajo que las vetas de hierro en `Grounds.Rock`, encontrarás cuarzo en la parte inferior de la capa de roca y en la `Grounds.Dirt` dura que hay debajo (comprueba la dureza con `get_hardness()` del desbloqueo [Sentidos subterráneos](docs/unlocks/underground_senses.md)).

El cuarzo crece en vetas con forma de aguja que forman columnas verticales, por lo que resulta bastante difícil encontrarlas por ensayo y error.

Por suerte, podemos usar nuestro hierro y deformarlo hasta convertirlo en algo parecido a una vara de zahorí que nos permita localizar estas vetas de cuarzo más fácilmente. El comando para hacerlo es `prospect_quartz()`.

`prospect_quartz()` funciona de forma distinta a `prospect_iron()`. En vez de devolver la dirección del mineral de cuarzo más cercano, devuelve la distancia euclídea (distancia 3D) hasta el cuarzo más cercano. Ejecutar `prospect_quartz()` cuesta 1 hierro, así que conviene usar el comando con moderación.

Si `prospect_quartz()` no encuentra cuarzo cerca o no tienes suficiente hierro para realizar la búsqueda, devuelve `None`.

El siguiente fragmento de código hace que tu dron excave más allá de la tierra y penetre en la capa de roca. Después, con un poco de suerte, habrá una veta de cuarzo cerca, en cuyo caso tu dron imprimirá la distancia hasta ella.

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

Puedes hacer prospecciones y moverte varias veces y ver cómo cambia la distancia, para saber si te acercas o te alejas de una veta. Puedes usar geometría 2D para hallar la intersección de dos o más círculos, encontrar la posición horizontal de una veta y excavar hacia abajo. O puedes usar trilateración completa para intersecar tres esferas y encontrar la posición 3D exacta.

Ten en cuenta que no hay funciones matemáticas básicas para raíces cuadradas, trigonometría ni vectores; tendrás que implementarlas tú. Ten en cuenta también que puede haber varias vetas cerca, así que si tomas varias medidas próximas, puede que no apunten a la misma veta y te despisten.

---

[Estadísticas](docs/stats.md)      [Minería](docs/unlocks/mining.md)      [Sentidos subterráneos](docs/unlocks/underground_senses.md)      [Variables](docs/scripting/variables.md)      [Operadores](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
