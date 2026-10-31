[<- 稲](docs/unlocks/rice.md) <right>[カラフルなブロック ->](docs/unlocks/debug_place.md)
<right>[ピラミッド ->](docs/unlocks/pyramid.md)
---
# 竹
竹は上へ伸びていく植物です。成長を続けさせるには、ドローンで茶色い実を定期的に摘み取る必要があります。これには新しくアンロックされた`hover`コマンドを使います。

竹は耕した土（`Grounds.Soil`）に植える必要があり、植えるには稲がコストとして消費されます。

次のコードは竹を植え、最初の実がなるまで成長を待ちます。
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
move(East) # 竹が成長できるように離れる
}}

## 実
竹は1秒ごとにちょうど1ブロック成長します。

竹は数ブロックごとに実をつけます。実がつくと竹は成長を止めるので、ドローンで竹の中へ飛び込んで実を壊す必要があります。

実を摘み取るには、まず`hover`で正しい高さまで移動します。次に`move`で実に飛び込んで摘み取り、竹が成長を続けられるように再び`move`で離れます。

竹を`measure()`すると、次の実がどの高さにつくかを調べられます。`measure()`は`0`から数えるので、`hover(measure())`でドローンを実がつく高さへ移動させられます。

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
hover(measure()) # ドローンが実の隣に来る高さまでホバーする

move(East) # 離れて実がなるまで待つ
for i in range(3):
    do_a_flip()

move(West) # 実を摘み取る
move(East) # また離れる
}}

## ホバー
`hover`コマンドは引数を1つ取ります。ホバーする高さで、`0`から`18`までの数値です。ドローンの標準のホバー高さは`1`です。`hover`では固体のエンティティの中へ下降できないため、ドローンがすでに竹の上にいる場合、`hover(0)`を実行しても竹の中へは入れません。

`hover`は、ドローンが指定した高さまでホバーできた場合は`True`を、そうでない場合は`False`を返します。

さらに、ドローンの現在のホバー高さを返す`get_hover`コマンドもあります。

ホバー中に`dig`、`harvest`、`plant`を使うと、ドローンは標準のホバー高さ（`1`）に戻ります。

最後に、`get_pos_z()`はホバーの影響を受けません。常にドローンの下にあるブロックのz座標を返します。

## 竹の収穫
`harvest()`も使えますが、竹畑を収穫するおすすめの方法は、ホバー高さ`0`（`hover(0)`）のドローンで竹の中へ移動することです。これで植物全体を一度に収穫できます。

竹を壊さずに収穫したい場合は、たとえば`hover(3)`のように、どの高さからでも`move`で竹の中へ入れます。その高さから上にある竹の部分をすべて収穫しますが、竹自体は生きたまま残ります。このように一部だけ収穫した竹にはまた実がなるので、もう一度摘み取る必要があります。

どちらの場合も、収穫量は壊した竹の部分の数の2乗になります。つまり竹が高いほど収穫量も多くなります。

---

[統計](docs/stats.md)      [forループ](docs/scripting/for.md)      [変数](docs/scripting/variables.md)      [If文](docs/scripting/if.md)      [関数](docs/scripting/functions.md)      [稲](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
