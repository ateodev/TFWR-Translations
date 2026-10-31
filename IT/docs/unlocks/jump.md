[<- Carbone](docs/unlocks/coal.md)
---
# Salto
Il tuo drone ha sbloccato il comando `jump()`. Per usarlo, passa uno sblocco come argomento, per esempio `Unlocks.Iron`.

Questo comando permette di scegliere come bersaglio determinate risorse nascoste nel terreno e saltare istantaneamente giù fino a esse. È particolarmente utile per il debug o per tornare a una vena mineraria che hai appena mancato.

Dopo il salto, la risorsa bersaglio dovrebbe trovarsi entro 3 blocchi dalla superficie del blocco più in alto. `jump()` può essere usato una sola volta per esecuzione del programma: ulteriori tentativi di salto producono un errore.

L'esempio seguente salta giù fino al [riso](docs/unlocks/rice.md), trova lo strato di argilla e pianta una fila di terrazze di riso:
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
    "items": [{"item": "hay", "n": 10}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms"],
    "starting_chunk": 0
}
#CODE
# Salta vicino alla risorsa del riso
jump(Unlocks.Rice)

# Pianta una fila di terrazze di riso
for i in range(get_world_size()):
    # Il salto non è preciso, scava via gli ultimi blocchi
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## Sblocchi Compatibili
`jump()` funziona solo con i seguenti sblocchi minerari:
- Coal
- Iron
- Quartz
- Rice
- Petrified_Pumpkins
- Special_Soils
- Pyramid
- Treasure_Map
- Mushrooms
- Dynamite

---

[jump()](functions/jump)
