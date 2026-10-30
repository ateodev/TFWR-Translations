[<- 石炭](docs/unlocks/coal.md)
---
# ジャンプ

ドローンが`jump()`コマンドをアンロックしました。`Unlocks.Iron`のようなアンロックを引数として渡すと使うことができます。

このコマンドを使うと、地中に隠れている特定のアンロックを指定して、その場所へ一瞬で飛び降りることができます。これはデバッグや、さっき見逃した鉱石の鉱脈まで移動するときに特に便利です。

ジャンプした後は、対象のアンロックが一番上のブロックの表面から3ブロック以内にあるはずです。`jump()`を使えるのはプログラムの実行ごとに1回だけで、それ以上ジャンプしようとするとエラーになります。

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

## 対応するアンロック
`jump()`は次の採掘関連のアンロックでのみ使えます。
- 石炭（Coal）
- 鉄（Iron）
- 石英（Quartz）
- 稲（Rice）
- 石化したカボチャ（Petrified_Pumpkins）
- 特殊な土壌（Special_Soils）
- ピラミッド（Pyramid）
- 宝物の地図（Treasure_Map）
- キノコ（Mushrooms）
- ダイナマイト（Dynamite）

---

[jump()](functions/jump)
