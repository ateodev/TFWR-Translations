[<- Hierro](docs/unlocks/iron.md) <right>[Hongo ->](docs/unlocks/mushroom.md)
---
# Cuarzo
Más abajo que las vetas de hierro en `Grounds.Rock`, encontrarás cuarzo en la parte inferior de la capa de roca y en la `Grounds.Dirt` dura que hay debajo (comprueba la dureza con `get_hardness()` del desbloqueo [Sentidos subterráneos](docs/unlocks/underground_senses.md)).

El siguiente fragmento de código excava más allá de la tierra hasta la capa de roca. Allí hace prospecciones de cuarzo continuamente mientras excava, hasta que la distancia es menor que 2. Por último, imprime la distancia de prospección a la que ha llegado.
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
# Excava hasta la capa de roca
while get_ground_type() != Grounds.Rock:
    dig()

# Sigue excavando hasta que haya una veta de cuarzo cerca
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# Imprime la distancia final hasta la veta
print(prospect_quartz())
}}

## Estructura de las vetas
El cuarzo crece en vetas con forma de aguja que forman columnas verticales, por lo que resulta bastante difícil encontrarlas por ensayo y error.

## Prospección de cuarzo
Por suerte, podemos usar nuestro hierro y deformarlo hasta convertirlo en algo parecido a una vara de zahorí que nos permita localizar estas vetas de cuarzo más fácilmente. El comando para hacerlo es `prospect_quartz()`.

`prospect_quartz()` funciona de forma distinta a `prospect_iron()`. En vez de devolver la dirección en la que debe moverse el dron para acercarse al mineral de hierro más cercano, devuelve la distancia 3D exacta entre el bloque de cuarzo más cercano y el dron (distancia euclídea).

Ejecutar `prospect_quartz()` cuesta 1 hierro, así que conviene usar el comando con moderación.

Si `prospect_quartz()` no encuentra cuarzo cerca o no tienes suficiente hierro para realizar la búsqueda, devuelve `None`.

## Estrategia
<spoiler=mostrar pista>Puedes hacer prospecciones y moverte varias veces para ver cómo cambia la distancia. En una superficie plana, intentar minimizar la distancia puede situarte encima de una veta de cuarzo. Puedes usar una estrategia parecida a la búsqueda binaria para minimizar el número de llamadas a `prospect_quartz()` y la cantidad de hierro que consumen.

Las estrategias más elaboradas pueden usar geometría 2D para hallar la intersección de dos o más círculos, o puedes ir por el camino difícil y hacer una trilateración completa para intersecar tres esferas y encontrar la posición 3D exacta de la veta.

Ten en cuenta que, para calcular una raíz cuadrada, puedes usar el operador de exponente; por ejemplo, para obtener la raíz cuadrada de 16, usa `16**0.5`. No hay funciones matemáticas integradas para trigonometría ni vectores; tendrás que implementarlas tú. 

Ten en cuenta también que puede haber varias vetas cerca, así que si tomas varias medidas próximas, puede que no apunten a la misma veta.</spoiler>

---

[Estadísticas](docs/stats.md)      [Minería](docs/unlocks/mining.md)      [Sentidos subterráneos](docs/unlocks/underground_senses.md)      [Variables](docs/scripting/variables.md)      [Operadores](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
