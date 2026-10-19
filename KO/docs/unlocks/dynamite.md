[<- 버섯](docs/unlocks/mushroom.md) <right>[폭발 드릴 ->](docs/unlocks/explosive_drill.md)
---
# 다이너마이트

이전의 채광 탐사대가 남긴 획기적인 폭발물입니다. 다행이라고 해야 할지 불행이라고 해야 할지, 드론의 드릴은 다이너마이트를 폭발시켜 주변의 모든 블록을 날려 버리기에 안성맞춤이죠.

다이너마이트를 안전하게 굴착하려면 `Grounds.Dynamite` 층과 그 바로 아래에 이어지는 `Grounds.Soot` 층을 찾으세요. 위쪽의 다이너마이트 층은 조금 오래되었기 때문에 일부 블록은 안전하게 굴착할 수 있습니다. 하지만 일부 다이너마이트 블록은 아직 활성 상태이므로 파면 폭발합니다.

{{codeexample 
{
    "camera_position": {"x": -5, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 900, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}],
    "world_size": {"x": 11, "y": 11},
    "execution_speed": 8,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 5,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(5):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [East, South, West, West, North, North, East, East, South, West]
def dig_dynamite_neighbors():
    for dir in circle_directions:
        move(dir)
        while get_ground_type() != Grounds.Soot:
            dig()

while get_ground_type() == Grounds.Soot and measure() == 0:
    dig_dynamite_neighbors()
    move(circle_directions[random() * len(circle_directions)])
}}

불발 다이너마이트 블록을 모두 찾아 굴착하고 활성 블록만 남길 수 있나요? 다른 활성 블록이나 그을음 블록으로만 둘러싸인 활성 블록은 다이너마이트 지층이 사라질 때 추가 다이너마이트를 제공합니다.

다행히 아래의 그을음 블록이 도움이 되겠군요. 이 블록은 인접한 다이너마이트 블록 중 활성 다이너마이트가 있는 블록의 수를 감지할 수 있습니다. 어느 블록이 활성인지는 알려주지 않고 총 몇 개가 있는지만 알려주므로, 여러 그을음 블록의 측정값을 조합해 스스로 추론해야 합니다.

그을음 블록에서 `measure()`를 호출하면 위쪽 다이너마이트 지층의 인접한 여덟 타일에 있는 활성 다이너마이트의 수를 반환합니다. 숫자는 `0`(활성 다이너마이트 없음)부터 `8`(모든 인접 블록에 활성 다이너마이트가 있음)까지입니다.

다이너마이트 지층에서 처음 파내는 블록은 항상 불발탄입니다. 다이너마이트 블록을 굴착할 때마다 다이너마이트를 약간 얻습니다. 모든 불발탄을 굴착하는 데 성공하거나 활성 다이너마이트를 실수로 파서 지층이 파괴되면, 완전히 드러난 활성 블록 수의 제곱만큼 다이너마이트를 추가로 얻습니다.

활성 다이너마이트를 파면 두 지층이 폭발합니다. `Grounds.Dynamite`를 판 뒤 `get_ground_type()`를 사용해 이를 확인할 수 있습니다. 땅이 `Grounds.Soot`가 아니라면 퍼즐을 풀지 못한 겁니다. 반대로 마지막 비활성 다이너마이트 블록을 굴착하면 모든 다이너마이트 블록이 사라지면서 퍼즐에서 얻을 수 있는 최대 수확량을 받을 수 있습니다. 그을음 지층은 남지만 `measure()`가 `None`을 반환해 퍼즐을 성공적으로 풀었음을 알려줍니다.

`# 다이너마이트 블록을 굴착해 퍼즐 상태 확인
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # 활성 다이너마이트를 굴착함, 퍼즐 실패
        return False
    elif measure() == None:
        # 마지막 불발탄 블록을 굴착함, 퍼즐 해결
        return True
    else:
        # 측정값을 얻음, 퍼즐 진행 중
        return None
`

다이너마이트 지층의 활성 다이너마이트 수와 다이너마이트를 찾는 난이도는 깊이에 따라 증가합니다. 전체 다이너마이트 수는 농장 크기에 따라 늘어나므로, 다이너마이트 지층을 정리했을 때 얻을 수 있는 최대 수확량도 늘어납니다.

모은 다이너마이트는 `use_item(Items.Dynamite)`로 사용할 수 있으며 드론 바로 아래에서 즉시 폭발합니다.

다이너마이트를 업그레이드하면 다이너마이트 블록을 굴착하거나 활성 블록을 완전히 드러내서 얻는 수확량이 늘어납니다. 또한 다이너마이트 폭발 에너지가 30% 증가합니다.

---

[통계](docs/stats.md)      [지하 감지](docs/unlocks/underground_senses.md)      [딕셔너리](docs/scripting/dicts.md)      [세트](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
