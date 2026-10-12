[<- 採礦](docs/unlocks/mining.md)
---
# 地下感測

讓我們加裝幾個感測器，好讓你的無人機能在地底找到方向。

你現在可以使用 `get_pos_z()` 取得無人機的高度（從 0 開始，無人機下降時變為負數）。

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#CODE
move(North)
move(North)
move(East)
dig()
dig()
dig()
print(get_pos_z())
}}

`get_ground_type()` 會回傳無人機下方的地面類型。你可以傳入一個方向引數（例如 `get_ground_type(North)`）來取得相鄰格的地面類型。

檢查無人機下方的方塊是否為泥土的方法如下：

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
    "items": [{"item": "hay", "n": 100}, {"item": "wood", "n": 100}],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#CODE
dig()
if get_ground_type() == Grounds.Dirt:
    do_a_flip()
}}


`get_hardness()` 會回傳無人機下方地面格的硬度。你可以傳入一個方向引數，例如 `get_hardness(North)`。格子的硬度越高，挖掘所需的時間就越長。

`get_stability()` 會回傳無人機下方地面格的穩定度。你可以傳入一個方向引數，例如 `get_stability(North)`。穩定度為 1 表示該方塊在崩塌前可以承受 1 的高度差。

請注意，無人機向下挖掘時，緊鄰無人機的四個方塊無論穩定度如何都會被移除，除非該方塊有特殊功能。例如，黏土、鐵和石英就不會因為這條規則被移除。不過，它們仍然可能因為方塊穩定度不足而崩塌。
---

[採礦](docs/unlocks/mining.md)      [感測](docs/unlocks/senses.md)

[get_pos_z()](functions/get_pos_z)      [get_ground_type()](functions/get_ground_type)      [get_hardness()](functions/get_hardness)      [get_stability()](functions/get_stability)
