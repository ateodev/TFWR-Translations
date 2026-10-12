[<- 石英](docs/unlocks/quartz.md) <right>[炸藥 ->](docs/unlocks/dynamite.md)
---
# 蘑菇

許多種類的蘑菇會在地底成群生長。挖掘時留意 `Grounds.Mushroom` 地層。然後你可以對地面 `measure()`，以數字形式取得蘑菇類型，從 `0` 開始。

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 6},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "hay", "n": 100}, {"item": "iron", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "digging_speed": 6,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "dynamite", "iron"]
}

#SETUP
jump(Unlocks.Mushrooms)
#CODE
while get_ground_type() != Grounds.Mushroom:
    dig()
do_a_flip()
print(measure())
}}

同類型的蘑菇喜歡聚在一起，但它們太害羞了，不會長在彼此上面。把一個蘑菇方塊推到另一個同類型的蘑菇方塊上，它們就會消失，並以蘑菇作為獎勵。

你可以使用 `can_push(direction)` 檢查無人機下方的方塊是否可以被推動，以及指定方向上是否有東西擋住。`push(direction)` 會推動方塊並回傳推動是否成功。

方塊無法向上推，如果有其他方塊擋路，推動就會失敗。被推到空中的方塊會掉落並停在下方最近的方塊上。

記住，你可以呼叫 `place(Grounds.Dirt)` 在無人機下方放置方塊。這在填洞時很有用，這樣你就能把方塊推過去。

---

[統計資料](docs/stats.md)      [地下感測](docs/unlocks/underground_senses.md)      [字典](docs/scripting/dicts.md)

[move()](functions/move)      [measure()](functions/measure)      [can_push()](functions/can_push)      [push()](functions/push)      [place()](functions/place)      [get_ground_type()](functions/get_ground_type)
