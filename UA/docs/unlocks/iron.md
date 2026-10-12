[<- Вугілля](docs/unlocks/coal.md) <right>[Кварц ->](docs/unlocks/quartz.md)
<right>[Пошук заліза ->](docs/unlocks/prospecting.md)
<right>[Карта скарбів ->](docs/unlocks/treasure_map.md)
---
# Залізо

Ви знайшли залізні жили в кам'яному шарі під глиною.

Спочатку залізні жили маленькі, і щоб їх знайти, потрібна удача. З підвищенням рівня цього розблокування максимальний розмір жили зростає. Для надійнішого способу пошуку заліза зверніть увагу на розблокування пошуку руди.

Залізна жила завжди неперервна, без діагональних стрибків. Знайшовши шматок заліза, пошукайте ще під ним або поруч, щоб зібрати всю жилу.

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

[Статистика](docs/stats.md)      [Видобуток](docs/unlocks/mining.md)      [Пошук заліза](docs/unlocks/prospecting.md)      [Підземні сенсори](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)
