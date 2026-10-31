[<- Arroz](docs/unlocks/rice.md) <right>[Bloques de colores ->](docs/unlocks/debug_place.md)
<right>[Pirámides ->](docs/unlocks/pyramid.md)
---
# Bambú
El bambú es una planta que crece hacia arriba. Tu dron tendrá que arrancar sus frutos marrones con regularidad para que pueda seguir creciendo. Podemos conseguirlo con el comando `hover` que acabas de desbloquear.

El bambú debe plantarse en tierra arada (`Grounds.Soil`) y plantarlo cuesta arroz.

El siguiente código planta bambú y espera a que crezca hasta su primer fruto.
{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
move(East) # apártate para que el bambú pueda crecer
}}

## Frutos
El bambú crece exactamente 1 bloque por segundo.

El bambú produce frutos cada pocos bloques. Cuando eso ocurre, el bambú deja de crecer y tendrás que volar hacia él con tu dron para destruir el fruto.

Para arrancar frutos, primero tendrás que usar `hover` para ponerte a la altura correcta. Después, usa `move` para entrar en el fruto y arrancarlo, y vuelve a usar `move` para apartarte y que el bambú pueda seguir creciendo.

Puedes usar `measure()` en el bambú para comprobar a qué altura aparecerá el siguiente fruto. `measure()` empieza a contar desde `0`, así que `hover(measure())` llevará a tu dron a la altura en la que estará el fruto.

{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
hover(measure()) # flota a la altura en la que el dron quedará junto al fruto

move(East) # apártate y espera a que crezca
for i in range(3):
    do_a_flip()

move(West) # arranca el fruto
move(East) # vuelve a apartarte
}}

## Flotar
El comando `hover` recibe un argumento, la altura a la que flotar, que es un número de `0` a `18`. La altura de vuelo predeterminada del dron es `1`. `hover` no puede bajar hacia entidades sólidas, así que si tu dron ya está encima de un bambú, no puedes entrar en él ejecutando `hover(0)`.

`hover` devuelve `True` si el dron consiguió flotar a la altura indicada y `False` en caso contrario.

Además, existe el comando `get_hover`, que devuelve la altura de vuelo actual del dron.

Si usas `dig`, `harvest` o `plant` mientras flotas, el dron volverá a su altura de vuelo predeterminada (`1`).

Por último, `hover` no afecta a `get_pos_z()`. Siempre devuelve la posición z del bloque que hay bajo el dron.

## Cosechar bambú
Aunque podrías usar `harvest()`, la forma recomendada de cosechar campos de bambú es entrar en un bambú con tu dron a la altura de vuelo `0` (`hover(0)`). Así se cosecha toda la planta de una vez.

Si quieres cosechar el bambú sin destruirlo, puedes usar `move` para entrar en él a cualquier altura, por ejemplo con `hover(3)`. Así se cosechan todos los trozos de bambú desde esa altura hacia arriba, pero el bambú sigue vivo. Un bambú cosechado parcialmente de esta forma volverá a producir sus frutos, así que tendrás que arrancarlos de nuevo.

En ambos casos, el rendimiento es igual al cuadrado del número de trozos de bambú destruidos, así que cuanto más alta sea la planta de bambú, mejor será tu rendimiento.

---

[Estadísticas](docs/stats.md)      [Bucle for](docs/scripting/for.md)      [Variables](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Funciones](docs/scripting/functions.md)      [Arroz](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
