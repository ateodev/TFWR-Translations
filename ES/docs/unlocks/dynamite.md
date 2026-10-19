[<- Hongo](docs/unlocks/mushroom.md) <right>[Taladro explosivo ->](docs/unlocks/explosive_drill.md)
---
# Dinamita

El explosivo revolucionario que dejaron atrás expediciones mineras anteriores. Por (mala) suerte, tu taladro es perfecto para hacer explotar la dinamita y volar todos los bloques que te rodean.

Para extraer dinamita de forma segura, encuentra una capa de `Grounds.Dynamite` seguida justo debajo de otra capa de `Grounds.Soot`. La capa de dinamita de arriba se ha quedado algo vieja y es seguro excavar algunos de sus bloques. Sin embargo, algunos de los bloques de dinamita siguen activos y explotarán al excavarlos.

{{codeexample 
{
    "camera_position": {"x": -5, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 900, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}],
    "world_size": {"x": 11, "y": 11},
    "execution_speed": 8,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 5,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(5):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [East, South, West, West, North, North, East, East, South, West]
def dig_dynamite_neighbors():
    for dir in circle_directions:
        move(dir)
        while get_ground_type() != Grounds.Soot:
            dig()

while get_ground_type() == Grounds.Soot and measure() == 0:
    dig_dynamite_neighbors()
    move(circle_directions[random() * len(circle_directions)])
}}

¿Puedes encontrar y excavar todos los bloques de dinamita inertes dejando solo los activos? Cada bloque activo que esté rodeado únicamente por otros bloques activos o bloques de hollín te dará dinamita adicional cuando desaparezca el estrato de dinamita.

Por suerte, los bloques de hollín inferiores te ayudarán: pueden detectar cuántos bloques de dinamita vecinos contienen dinamita activa. No te dirán exactamente cuáles están activos, solo el número total, así que tendrás que combinar las lecturas de varios bloques de hollín y deducirlo por tu cuenta.

Llamar a `measure()` sobre un bloque de hollín devuelve el número de minas que hay en las ocho casillas vecinas del estrato de dinamita superior. El número puede ir de `0` (ninguna mina activa) a `8` (cada bloque vecino contiene una mina activa).

La primera excavación en el estrato de dinamita siempre da con un bloque inerte. Cada bloque de dinamita extraído produce un poco de dinamita. Cuando se destruye el estrato, ya sea por haber excavado correctamente todos los bloques inertes o por excavar sin querer dinamita activa, también obtienes una cantidad de dinamita igual al cuadrado del número de bloques activos descubiertos por completo.

Si excavas dinamita activa, los dos estratos explotan. Puedes comprobarlo usando `get_ground_type()` después de excavar `Grounds.Dynamite`. Si el terreno no es `Grounds.Soot`, no has resuelto el puzle. En cambio, si excavas el último bloque de dinamita inerte, todos los bloques de dinamita desaparecen y obtienes el rendimiento máximo del puzle. El estrato de hollín permanece, pero `measure()` devuelve `None`, lo que indica que el puzle se ha resuelto correctamente.

`# Excava un bloque de dinamita y comprueba el estado del puzle
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # Se excavó dinamita activa; el puzle ha fallado
        return False
    elif measure() == None:
        # Se excavó el último bloque inerte; puzle resuelto
        return True
    else:
        # La medición dio un número; el puzle sigue en curso
        return None
`

El número de minas activas en el estrato de dinamita y, por tanto, la dificultad para encontrarlas aumentan con la profundidad. El número total de minas aumenta con el tamaño de la granja y, con él, el rendimiento máximo posible al despejar un estrato de dinamita.

La dinamita recogida se puede usar con `use_item(Items.Dynamite)` y explota inmediatamente debajo del dron.

Mejora la dinamita para aumentar el rendimiento de excavar bloques de dinamita y de descubrir por completo bloques activos. La mejora también aumenta un 30 % la energía de las explosiones de dinamita.

---

[Estadísticas](docs/stats.md)      [Sentidos subterráneos](docs/unlocks/underground_senses.md)      [Diccionarios](docs/scripting/dicts.md)      [Conjuntos](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
