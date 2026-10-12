[<- 稻米](docs/unlocks/rice.md)
---
# 石化南瓜

看來地底下也能找到南瓜。它們已經變硬石化了，但對我們來說還是夠用。

石化南瓜會以 3x3x3 或 5x5x5 的方塊群出現在地底。沒有萬無一失的找法，只能希望無人機剛好挖中。不過，它們出現在石頭和鐵層下方的硬土中，高度和石英大致相同（如果你已解鎖石英）。

這是一種不必在地面種植就能取得南瓜的替代方式。如果你比較喜歡種植，完全可以忽略石化南瓜。

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
    "items": [{"item": "hay", "n": 100}],
    "exclude_unlocks": ["mushrooms", "watering", "fertilizer", "pyramid", "dynamite"],
    "world_size": {"x": 6, "y": 6},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 3
}
#SETUP
jump(Unlocks.Petrified_Pumpkins)
move(East)
move(North)
move(North)
move(North)
#CODE
while get_ground_type() != Grounds.Petrified_Pumpkin:
    dig()
z = get_pos_z()
for i in range(get_world_size()):
    for j in range(get_world_size()):
        while get_pos_z() > z:
            dig()
        move(North)
    move(East)
}}

---

[統計資料](docs/stats.md)      [採礦](docs/unlocks/mining.md)      [地下感測](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
