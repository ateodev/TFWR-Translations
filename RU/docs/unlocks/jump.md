[<- Уголь](docs/unlocks/coal.md)
---
# Прыжки

Твой дрон разблокировал команду `jump()`. Чтобы использовать ее, нужно передать технологию в качестве аргумента, например `Unlocks.Iron`.

Эта команда позволяет выбрать определенные ресурсы, спрятанные в земле, и мгновенно спуститься к ним. Это особенно удобно для отладки или чтобы быстро добраться до недавно пропущенной рудной жилы.

После прыжка целевой ресурс окажется не глубже 3 блоков от верхнего слоя блоков. За один запуск программы `jump()` можно использовать только один раз, повторные попытки вызовут ошибку.

Следующий пример спускается к [рису](docs/unlocks/rice.md), находит слой глины и сажает ряд рисовых террас:
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
# Прыгнуть поближе к рису
jump(Unlocks.Rice)

# Посадить ряд рисовых террас
for i in range(get_world_size()):
    # Прыжок неточный, раскопать оставшиеся блоки
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## Совместимые технологии
`jump()` работает только со следующими технологиями добычи:
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
