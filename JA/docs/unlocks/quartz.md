[<- 鉄](docs/unlocks/iron.md) <right>[キノコ ->](docs/unlocks/mushroom.md)
---
# 石英

`Grounds.Rock`の鉄の鉱脈よりさらに進むと、岩の層の下部と、その下の硬い`Grounds.Dirt`で石英が見つかります（硬さは[地下の感覚](docs/unlocks/underground_senses.md)のアンロックで使える`get_hardness()`で確認できます）。

石英は針状の鉱脈として生成され、垂直方向に柱状の形を作るため、当てずっぽうで探すのはかなり困難です。

幸い、鉄を加工して占い棒のようなものを作れば、石英の鉱脈をもっと簡単に探せます。そのコマンドが `prospect_quartz()`です。

`prospect_quartz()`は`prospect_iron()`とは異なります。最も近い石英の鉱石の方角ではなく、そこまでのユークリッド距離（3次元の距離）を返します。`prospect_quartz()`の実行には鉄を1個消費するので、コマンドの使いどころを選ぶとよいでしょう。

近くに石英が見つからない場合、または鉄が足りない場合、`prospect_quartz()`は`None`を返します。

次のコードスニペットでは、ドローンが土を通り抜けて岩の層を深く掘り進めます。運がよければ近くに石英の鉱脈があり、ドローンがそこまでの距離を表示します。

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
    "items": [{"item": "hay", "n": 100}, {"item": "iron", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite"]
}

#CODE
move(East)
move(North)
while get_ground_type() != Grounds.Rock:
    dig()
for i in range(30):
    dig()
do_a_flip()
do_a_flip()
print(prospect_quartz())
}}

探査と移動を繰り返して距離の変化を見れば、鉱脈に近づいているのか遠ざかっているのかがわかります。2Dの幾何学を使って2つ以上の円の交点を求めれば、鉱脈の水平位置がわかり、そこから掘り下げられます。あるいは完全な三辺測量で3つの球の交点を求め、正確な3D位置を割り出すこともできます。

平方根、三角関数、ベクトルのための基本的な数学関数はないので、自分で実装する必要があります。また、近くに複数の鉱脈があることもあるので、近い場所で何度か測定しても同じ鉱脈を指しているとは限らず、惑わされるかもしれません。

---

[統計](docs/stats.md)      [採掘](docs/unlocks/mining.md)      [地下の感覚](docs/unlocks/underground_senses.md)      [変数](docs/scripting/variables.md)      [演算子](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
