[<- Carvão](docs/unlocks/coal.md) <right>[Quartzo ->](docs/unlocks/quartz.md)
<right>[Prospecção de Ferro ->](docs/unlocks/prospecting.md)
<right>[Mapa do Tesouro ->](docs/unlocks/treasure_map.md)
---
# Ferro

Depois de encontrar carvão em `Grounds.Dirt`, você pode escavar mais fundo, passando pela camada de `Grounds.Clay` até `Grounds.Rock`, para encontrar ferro.

Ao contrário dos veios de carvão, os veios de ferro também se estendem na vertical. Mas todos os blocos de ferro de um veio estão sempre diretamente lado a lado; os blocos nunca se ligam apenas na diagonal.

Mas os veios de ferro começam pequenos, e você precisará de sorte para encontrá-los. Continuar desbloqueando o ferro aumenta o tamanho máximo dos veios e os torna um pouco mais fáceis de encontrar por acaso. Mas para encontrá-los de forma confiável, você deve desbloquear a [prospecção de ferro](docs/unlocks/prospecting.md).

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
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 1,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#SETUP
jump(Unlocks.Iron)
#CODE
for i in range(4):
    dig()
do_a_flip()
}}

---

[Estatísticas](docs/stats.md)      [Mineração](docs/unlocks/mining.md)      [Prospecção de Ferro](docs/unlocks/prospecting.md)      [Sentidos Subterrâneos](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
