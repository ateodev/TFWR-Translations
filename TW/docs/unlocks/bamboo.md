[<-水稻](docs/unlocks/rice.md) <right>[彩色地塊->](docs/unlocks/debug_place.md)
<right>[金字塔->](docs/unlocks/pyramid.md)
---
# 竹子
竹子是一種會往上生長的植物。你的無人機需要定期摘掉它的棕色果實，竹子才能繼續生長。新解鎖的 `hover` 指令可以幫我們做到這一點。

竹子必須種在已耕作的土壤（`Grounds.Soil`）上，種植竹子需要消耗水稻。

以下程式碼會種下竹子，並等待它長出第一顆果實。
{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
move(East) # 移開，讓竹子能夠生長
}}

## 果實
竹子每秒長高 1 個地塊。

竹子每長幾個地塊就會結出果實。這時竹子會停止生長，你需要讓無人機飛進竹子裡，把果實摧毀。

要摘下果實，你得先用 `hover` 升到正確的高度。接著用 `move` 移進果實把它摘掉，再用 `move` 移開，讓竹子能繼續生長。

你可以對竹子使用 `measure()`，檢視下一顆果實會出現在哪個高度。`measure()` 從 `0` 開始計數，因此 `hover(measure())` 會把無人機帶到果實將出現的高度。

{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
hover(measure()) # 懸停到無人機會在果實旁邊的高度

move(East) # 移開並等待竹子生長
for i in range(3):
    do_a_flip()

move(West) # 摘下果實
move(East) # 再次移開
}}

## 懸停
`hover` 指令接受一個參數，也就是要懸停的高度，範圍是 `0` 到 `18` 的數字。無人機的預設懸停高度是 `1`。`hover` 無法向下移進實心的實體，所以如果無人機已經在竹子上方，執行 `hover(0)` 並不能讓它移進竹子裡。

如果無人機成功懸停到指定高度，`hover` 會回傳 `True`，否則回傳 `False`。

另外還有 `get_hover` 指令，會回傳無人機目前的懸停高度。

如果你在懸停時使用 `dig`、`harvest` 或 `plant`，無人機會回到預設的懸停高度（`1`）。

最後，`get_pos_z()` 不受懸停影響。它一律回傳無人機下方地塊的 z 座標。

## 收穫竹子
雖然你可以使用 `harvest()`，但收穫竹田的建議做法是讓無人機在懸停高度 `0`（`hover(0)`）時移進竹子。這樣可以一次收穫整株竹子。

如果你想收穫竹子又不想摧毀它，可以在任何高度用 `move` 移進竹子，例如 `hover(3)`。這會收穫從該高度往上的所有竹節，但竹子會保留下來。以這種方式部分收穫的竹子會重新長出果實，所以你需要再把果實摘掉。

無論哪種方式，產量都等於被摧毀的竹節數量的平方，所以竹子長得越高，產量就越好。

---

[統計資料](docs/stats.md)      [For 迴圈](docs/scripting/for.md)      [變數](docs/scripting/variables.md)      [If 陳述式](docs/scripting/if.md)      [函式](docs/scripting/functions.md)      [水稻](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
