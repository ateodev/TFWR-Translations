[<- Mineração](docs/unlocks/mining.md) <right>[Bambu ->](docs/unlocks/bamboo.md)
<right>[Abóboras Petrificadas ->](docs/unlocks/petrified_pumpkins.md)
<right>[Perlita e Solo Franco ->](docs/unlocks/special_soils.md)
---
# Arroz

Abaixo da superfície e da camada de `Grounds.Dirt`, talvez você tenha notado uma fina camada de `Grounds.Clay`. Acontece que esse solo fértil e encharcado é perfeito para plantar mudas de arroz.

Assim como com grama ou arbustos, enquanto o drone estiver sobre um bloco de `Grounds.Clay`, você pode usar `plant(Entities.Rice)` para plantar mudas de arroz na argila, depois `can_harvest()` para verificar se o arroz já cresceu totalmente e, por fim, `harvest()` para obter arroz.

Assim que você planta arroz, o solo vira `Grounds.Rice_Terrace` para oferecer o ambiente perfeito para o arroz amadurecer. Quando o arroz cresce totalmente, o solo seca, vira `Grounds.Dry_Rice_Terrace` e não pode mais ser usado para plantar arroz. Felizmente, a camada tem alguns blocos de espessura, então você pode remover o bloco com `dig()` e plantar arroz novo na `Grounds.Clay` abaixo. E, se a camada acabar, você sempre pode usar `clear()` no mundo e escavar até uma camada nova.

O código a seguir pode ajudar você a escavar para baixo até encontrar argila.

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 8,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(East)
#CODE
while get_ground_type() != Grounds.Clay:
    dig()
plant(Entities.Rice)
move(North)
do_a_flip()
}}

---

[Estatísticas](docs/stats.md)      [Mineração](docs/unlocks/mining.md)      [Sentidos Subterrâneos](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [Loop For](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
