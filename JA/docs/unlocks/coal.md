[<- 採掘](docs/unlocks/mining.md) <right>[鉄 ->](docs/unlocks/iron.md)
<right>[ジャンプ ->](docs/unlocks/jump.md)
---
# 石炭

地下にはさまざまな鉱石が隠れていて、見つけて掘り出されるのを待っています。地表を掘り抜いて`Grounds.Dirt`に入ると、最初に見つかる鉱石は石炭です。

石炭の鉱脈は厚さ1ブロックの水平な層になっていて、土を掘り進めながら偶然見つける必要があります。層の中の石炭ブロックはたいてい隣り合っていますが、斜めにしかつながっていないものもあります。

石炭を採掘するのに特別なことは必要ありません。ドローンが`Grounds.Coal`ブロックの真上にいるときに`dig()`を実行するだけです。`get_ground_type()`でドローンの下にあるものを、`get_ground_type(direction)`で隣接する4つのブロックを確認できます。

石炭が手に入るのは直接掘った石炭ブロックの分だけで、ドローンの周りで崩落したブロックからは手に入りません。石炭の掘り方を考えるときはこれを念頭に置き、崩落で失うブロックより掘り出す石炭ブロックをできるだけ多くしましょう。

炭鉱は農場の大きさに比例して広がるので、採掘できる石炭の量を増やすために[拡大](unlocks/expand)をさらにアンロックすることも検討しましょう。

次のプログラムは石炭探しの出発点にぴったりです。石炭の層を探して下に掘り、見つけたら東西にも掘ってさらに石炭を探します。

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
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2
}
#SETUP
move(North)
move(East)
move(East)
#CODE
while get_ground_type() != Grounds.Coal:
    dig()
do_a_flip()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

特に小さな農場では、石炭ブロックを見つけた深さのブロックをすべて掘るのがシンプルな戦略です。効率を上げるには、`get_ground_type(direction)`で石炭ブロックを見かけた場所を記録しておき、土ブロックの上を移動する時間を省きましょう。石炭ブロックの上だけを移動していると斜めのつながりを見逃してしまうので、特に注意が必要です。

---

[統計](docs/stats.md)      [採掘](docs/unlocks/mining.md)      [地下の感覚](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
