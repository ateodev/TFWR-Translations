[<- 採掘](docs/unlocks/mining.md) <right>[竹 ->](docs/unlocks/bamboo.md)
<right>[石化したカボチャ ->](docs/unlocks/petrified_pumpkins.md)
<right>[パーライトと壌土 ->](docs/unlocks/special_soils.md)
---
# 稲

地表と`Grounds.Dirt`の層の下に、薄い`Grounds.Clay`の層があることに気づいたかもしれません。この肥沃で水を含んだ地面は、稲の苗を植えるのにぴったりです。

草や茂みと同じように、ドローンが`Grounds.Clay`ブロックの上にいる間は、`plant(Entities.Rice)`で粘土に稲の苗を植え、`can_harvest()`で稲が育ちきったか確認し、最後に`harvest()`で米を収穫できます。

稲を植えると、地面は稲が育つのに最適な環境の`Grounds.Rice_Terrace`に変わります。稲が育ちきると地面は乾いて`Grounds.Dry_Rice_Terrace`になり、もう稲を植えることはできません。幸い、層は数ブロックの厚みがあるので、`dig()`でブロックを取り除けば、その下の`Grounds.Clay`に新しい稲を植えられます。層を使い切っても、いつでも`clear()`でワールドを元に戻し、新しい層まで掘り下げられます。

粘土が見つかるまで下へ掘るには、次のコードが役立つでしょう。

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 8,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(East)
#CODE
while get_ground_type() != Grounds.Clay:
    dig()
plant(Entities.Rice)
move(North)
do_a_flip()
}}

---

[統計](docs/stats.md)      [採掘](docs/unlocks/mining.md)      [地下の感覚](docs/unlocks/underground_senses.md)      [If文](docs/scripting/if.md)      [forループ](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
