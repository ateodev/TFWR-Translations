[<-煤炭](docs/unlocks/coal.md)
---
# 跳轉

無人機已解鎖 `jump()` 指令。使用時，傳入一個解鎖項作為參數，例如 `Unlocks.Iron`。

此指令可以指定某些藏在地下的解鎖項，讓無人機立即跳轉下去。偵錯程式，或者回頭尋找剛剛錯過的礦脈時，這特別有用。

跳轉後，目標解鎖項應該位於最上層地塊表面以下 3 個地塊之內。每次執行程式只能使用一次 `jump()`，再次嘗試跳轉會產生錯誤。

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
jump(Unlocks.Rice)

for i in range(get_world_size()):
    while get_ground_type() != Grounds.Clay:
        dig()

    plant(Entities.Rice)

    move(East)
}}

## 相容的解鎖項
`jump()` 只適用於以下採礦解鎖項：
- Coal（煤炭）
- Iron（鐵礦）
- Quartz（石英）
- Rice（水稻）
- Petrified_Pumpkins（石化南瓜）
- Special_Soils（特殊土壤）
- Pyramid（金字塔）
- Treasure_Map（藏寶圖）
- Mushrooms（蘑菇）
- Dynamite（炸藥）

---

[jump()](functions/jump)
