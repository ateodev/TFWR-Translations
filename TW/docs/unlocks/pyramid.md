[<- 竹子](docs/unlocks/bamboo.md)
---
# 金字塔

地底現在有古代的金字塔建築，你可以從中收穫能量！

金字塔由沙方塊（`Grounds.Sand`）組成。金字塔本體下方是一層石灰岩地基（`Grounds.Limestone`）。由於年代久遠且受到侵蝕，你找到的金字塔都處於部分毀損的狀態。地基層一定存在，但沙層會有缺口。以下是挖出金字塔時的樣子：

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
    "items": [{"item": "hay", "n": 100}, {"item": "block", "n": 100}],
    "world_size": {"x": 6, "y": 6},
    "execution_speed": 32,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 7,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite", "quartz"]
}
#SETUP
jump(Unlocks.Pyramid)
move(North)
#CODE
while get_ground_type() != Grounds.Limestone:
    dig()
do_a_flip()
z = get_pos_z()
for i in range(6):
    for j in range(6):
        while (get_ground_type() != Grounds.Limestone
                and get_ground_type() != Grounds.Sand
                and get_pos_z() > z):
            dig()
        move(North)
    move(East)
}}

金字塔上方的方塊一定是泥土。如果你想比上面的程式碼更有效率地挖出金字塔，可以利用這一點。

如你所見，沙層中有幾個需要填補的缺口。當你填好這些缺口，把金字塔還原到原本的狀態時，它會自我摧毀，你則會獲得能量作為獎勵。

你可以用 `place(Grounds.Sand)` 指令放置方塊來還原金字塔。沙是一種特殊方塊，沒有適當支撐時會立即崩塌。每次放置沙方塊時，它必須直接放在石灰岩上，或放在 3x3 的沙方塊上。下面是一個手工搭建的小金字塔示範。當然，自己蓋的金字塔不會給你任何能量：

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
    "items": [{"item": "hay", "n": 100}, {"item": "block", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 4,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#CODE
for i in range(3):
    for j in range(3):
        place(Grounds.Limestone)
        move(North)
    move(East)
    
for i in range(3):
    for j in range(3):
        place(Grounds.Sand)
        move(North)
    move(East)
    
move(North)
move(East)
place(Grounds.Sand)
}}

正確還原的金字塔由邊長為奇數的正方形石灰岩地基組成，例如 5x5。地基上方是一層同樣大小（5x5）的沙方塊，接著是逐層縮小的沙層：3x3，然後是 1x1。

金字塔完成時會崩解，並在中央生成一朵大向日葵。你可以收割它來獲得能量。完成的金字塔越大，獲得的能量就越多。

---

[統計資料](docs/stats.md)      [地下感測](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [use_item()](functions/use_item)      [place()](functions/place)
