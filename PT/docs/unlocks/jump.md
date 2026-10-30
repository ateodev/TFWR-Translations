[<- Carvão](docs/unlocks/coal.md)
---
# Salto

Seu drone desbloqueou o comando `jump()`. Use-o passando um desbloqueio como argumento, como `Unlocks.Iron`.

Este comando permite escolher como alvo certos desbloqueios escondidos no solo e saltar instantaneamente até eles. É especialmente útil para depuração ou para pular direto para um veio de minério que você acabou de deixar passar.

Depois do salto, o desbloqueio escolhido deve estar a no máximo 3 blocos da superfície. `jump()` só pode ser usado uma vez por execução do programa; novas tentativas de salto produzem um erro.

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
jump(Unlocks.Rice)

for i in range(get_world_size()):
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## Desbloqueios Compatíveis
`jump()` só funciona com os seguintes desbloqueios de mineração:
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
