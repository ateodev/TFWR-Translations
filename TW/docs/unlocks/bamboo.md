[<- 稻米](docs/unlocks/rice.md) <right>[彩色方塊 ->](docs/unlocks/debug_place.md)
<right>[金字塔 ->](docs/unlocks/pyramid.md)
---
# 竹子

竹子是一種最高可以長到 6 格的植物。上方有無人機時它不會生長，所以使用 `plant(Entities.Bamboo)` 後記得把無人機 `move` 開。種植竹子需要消耗稻米。

竹子長到某個隨機決定的高度時會開花。使用 `measure()` 可以查看它會在哪個高度開花。`measure()` 從 0 開始計數，所以如果竹子在第二格開花，`measure()` 會回傳 1：

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 1000, "y": 500},
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
print(measure())
move(East)
}}

當無人機正好在花的正上方時 `harvest()`，竹子的產量最高。每差一格，產量就會除以八。
例如，如果它的花在高度 3，但你在高兩格的地方收割，產量就會除以 64。

要收割位置較高的花，請在無人機處於所需高度時飛進竹子。新解鎖的 `place()` 指令可以幫上忙。

使用 `place(Grounds.Dirt)` 在竹子旁邊堆疊方塊往上爬。然後使用 `move()` 從側面飛進竹子。呼叫 `harvest()` 時，無人機應該正好在花的正上方。

`place(Grounds.Dirt)` 會消耗你 1 個方塊！你也可以放置其他地面，例如 `Grounds.Rock`，但不能放置 `Grounds.Clay` 之類的特殊方塊。

竹子每秒正好長高 1 格。

{{codeexample 
{
    "camera_position": {"x": -1, "y": 0, "z": 8},
    "show_image": true,
    "image_size": {"x": 1000, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [{"item": "block", "n": 100}, {"item": "rice", "n": 100}],
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
print(measure())
move(East)
place(Grounds.Dirt)
do_a_flip() # 稍等一下
do_a_flip()
move(West)
harvest()
}}

---

[統計資料](docs/stats.md)      [for 迴圈](docs/scripting/for.md)      [變數](docs/scripting/variables.md)      [if 陳述式](docs/scripting/if.md)      [函式](docs/scripting/functions.md)      [稻米](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [place()](functions/place)      [measure()](functions/measure)
