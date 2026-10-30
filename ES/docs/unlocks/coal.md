[<- Minería](docs/unlocks/mining.md) <right>[Hierro ->](docs/unlocks/iron.md)
<right>[Saltar ->](docs/unlocks/jump.md)
---
# Carbón

Bajo tierra hay distintos minerales escondidos, esperando a que los encuentres y los extraigas. Si excavas a través de la superficie hasta `Grounds.Dirt`, el primer mineral que encuentras es el carbón.

No tienes que hacer nada especial para extraer carbón: basta con ejecutar `dig()` mientras el dron está justo encima de un bloque de `Grounds.Coal`. Usa `get_ground_type()` para comprobar qué hay debajo del dron y `get_ground_type(direction)` para comprobar los cuatro bloques adyacentes.

El siguiente programa es un buen punto de partida para encontrar carbón. Excava hacia abajo en busca de una capa de carbón.
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
    "items": [],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2,
    "exclude_unlocks": ["watering", "fertilizer"]
}
#SETUP
move(North)
move(East)
move(East)
#CODE
while get_ground_type() != Grounds.Coal:
    dig()
dig()
}}

## Nota sobre los derrumbes
Ten en cuenta que solo obtienes carbón por los bloques de carbón que excavas directamente, no por los bloques que se derrumban alrededor del dron. Tenlo presente al pensar cómo extraer carbón, para maximizar los bloques de carbón que extraes frente a los que se pierden en derrumbes.

## Estructura de las vetas
Sus vetas forman capas horizontales de 1 bloque de grosor que tienes que encontrar por casualidad mientras excavas en la tierra. Los bloques de carbón de una capa suelen estar justo unos al lado de otros, pero algunos también pueden estar conectados solo en diagonal.

Las minas de carbón crecen en proporción al tamaño de la granja, así que plantéate seguir desbloqueando [Expandir](unlocks/expand) para aumentar la cantidad de carbón que puedes extraer.

## Estrategia
<spoiler=mostrar pista>
Una estrategia sencilla, sobre todo en granjas pequeñas, es excavar todos los bloques a la profundidad en la que encontraste un bloque de carbón. Para ser más eficiente, puedes llevar la cuenta de dónde has visto bloques de carbón con `get_ground_type(direction)` y no perder tiempo pasando por bloques de tierra. Tendrás que poner especial cuidado en no pasar por alto las conexiones en diagonal, que se te escaparán si solo te mueves sobre bloques de carbón.
</spoiler>

---

[Estadísticas](docs/stats.md)      [Minería](docs/unlocks/mining.md)      [Sentidos subterráneos](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
