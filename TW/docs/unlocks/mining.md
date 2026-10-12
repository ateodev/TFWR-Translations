[<- 擴張 1](docs/unlocks/expand_1.md) <right>[地下感測 ->](docs/unlocks/underground_senses.md)
<right>[稻米 ->](docs/unlocks/rice.md)
<right>[煤炭 ->](docs/unlocks/coal.md)
---
# 採礦

你的無人機獲得了一個簡陋的鑽頭，可以用來在地底搜尋寶物。

你可以使用 `dig()` 指令挖掘你下方的方塊。

現在，先來收集一些方塊：

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
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "special_soils"]
}
#SETUP
move(North)
move(East)
#CODE
dig()
do_a_flip()
dig()
do_a_flip()
dig()
do_a_flip()
clear()
}}

如果你想回到地面，隨時可以使用 `clear()`。這也會還原你的農場。

<desktop>將滑鼠懸停在方塊上</desktop><mobile>點選方塊</mobile>會顯示它的名稱、穩定度和硬度。

# 鑽頭

隨著你越挖越深，你會發現方塊越來越硬，挖掘也會花更多時間。幸好我們可以升級鑽頭來解決這個問題！

你可以使用 `get_hardness()` 檢查下方方塊的硬度。如果遇到一片特別硬的方塊，繞過它們或許比較明智，這樣你可以更快前進：

`while True:
        if get_hardness() < 5:
                dig()
        else:
                move(East)`

當然，方塊會隨著深度越來越硬，所以這個策略雖然有幫助，但效果有限。

## 崩塌

向下挖掘會導致周圍的方塊崩塌。無人機旁邊的四個方塊一定會被摧毀。之後，崩塌會依據地面的穩定度擴散。穩定度為 1 的方塊（例如草地）可以承受 1 的高度差。換句話說，如果草地的垂直或水平相鄰方塊的 z 座標低了 2 格以上，這塊草地就會被摧毀。

方塊的<desktop>懸停</desktop>提示中會顯示其穩定度。

方塊崩塌時，也會移除它上方的所有方塊。你只能從無人機直接挖掘的方塊獲得資源，所以在崩塌中失去的方塊都會被摧毀而不產出任何資源。

---

[地下感測](docs/unlocks/underground_senses.md)      [while 迴圈](docs/scripting/while.md)

[move()](functions/move)      [dig()](functions/dig)
