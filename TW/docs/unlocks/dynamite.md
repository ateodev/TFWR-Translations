[<- 蘑菇](docs/unlocks/mushroom.md) <right>[爆破鑽頭 ->](docs/unlocks/explosive_drill.md)
---
# 炸藥

這種革命性的炸藥是先前的採礦遠征隊留下的。幸運（或不幸）的是，你的鑽頭非常適合引爆炸藥，把你周圍的所有方塊都炸掉。

要安全地開採炸藥，你必須找到由 `Grounds.Dynamite` 和 `Grounds.Soot` 組成的雙層地層。上方的炸藥地面已經有些老舊，其中有些方塊可以安全挖掘。不過，有些炸藥仍是活性的，挖到就會爆炸。

{{codeexample 
{
    "camera_position": {"x": -3, "y": -3, "z": 12},
    "show_image": true,
    "image_size": {"x": 900, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 8,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 4,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()
dig()
dig()
}}

你能找出並挖掘所有啞彈方塊，只留下活性方塊嗎？每個只被其他活性方塊或煤灰方塊包圍的活性方塊，都會在炸藥地層消失時為你產出額外的炸藥。

幸好，下方的煤灰方塊會幫助你：它們可以偵測相鄰的炸藥方塊中有多少個含有活性炸藥。它們不會告訴你到底哪些方塊是活性的，只會給出總數，所以你需要結合多個煤灰方塊的讀數自己推理出來。

在煤灰方塊上呼叫 `measure()` 會回傳上方炸藥地層中相鄰八格內的地雷數量。這個數字介於 `0`（沒有活性地雷）到 `8`（每個相鄰格都含有活性地雷）之間。

第一次挖進炸藥地層時一定是啞彈。每挖出一個炸藥方塊都會產出一些炸藥。當炸藥地層被摧毀時，不論是成功挖出所有啞彈還是不小心挖到活性炸藥，你還會額外獲得等於完全揭露的活性方塊數量平方的炸藥。

如果挖到活性炸藥，兩層地層都會爆炸。你可以在挖進 `Grounds.Dynamite` 後用 `get_ground_type()` 來檢查。如果地面不是 `Grounds.Soot`，就表示你解謎失敗了。反之，如果最後一個非活性炸藥方塊被挖出，所有炸藥方塊都會消失，你會獲得這道謎題的最大產出。煤灰地層會保留下來，但 `measure()` 會回傳 `None`，表示謎題已成功解決。

`# 挖掘一個炸藥方塊並檢查謎題狀態
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # 挖到了活性炸藥，謎題失敗
        return False
    elif measure() == None:
        # 挖出了最後一個啞彈方塊，謎題解決
        return True
    else:
        # 測量得到了數字，謎題仍在進行中
        return None
`

炸藥地層中的活性地雷數量會隨深度增加，因此找出它們的難度也會增加。

收集到的炸藥可以用 `use_item(Items.Dynamite)` 使用，會立即在無人機下方爆炸。

升級炸藥可以提高挖掘炸藥方塊和完全揭露活性方塊的產出。升級還會讓炸藥爆炸的能量提高 30%。

---

[統計資料](docs/stats.md)      [地下感測](docs/unlocks/underground_senses.md)      [字典](docs/scripting/dicts.md)      [集合](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
