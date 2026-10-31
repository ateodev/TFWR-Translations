[<- 철](docs/unlocks/iron.md) <right>[버섯 ->](docs/unlocks/mushroom.md)
---
# 석영
`Grounds.Rock`의 철 광맥에서 더 내려가면 암석층 아래쪽과 그 아래의 단단한 `Grounds.Dirt`에서 석영을 찾을 수 있습니다(경도는 [지하 감지](docs/unlocks/underground_senses.md) 해금의 `get_hardness()`로 확인하세요).

다음 코드는 흙층을 뚫고 암석층까지 내려갑니다. 그곳에서 거리가 2보다 작아질 때까지 굴착하면서 계속 석영을 탐사합니다. 마지막으로 도달한 탐사 거리를 출력합니다.
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
    "items": [{"item": "block", "n": 1}, {"item": "iron", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 8,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite"]
}
#SETUP
move(East)
move(North)
#CODE
# 암석층까지 파 내려가기
while get_ground_type() != Grounds.Rock:
    dig()

# 석영 광맥이 가까워질 때까지 계속 파기
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# 광맥까지의 최종 거리 출력하기
print(prospect_quartz())
}}

## 광맥 구조
석영은 바늘 모양의 광맥으로 자라며 수직 기둥을 이루므로 무작정 굴착해서 찾기가 꽤 어렵죠.

## 석영 탐사
다행히 철을 구부려 석영 광맥을 더 쉽게 찾게 해주는 탐지봉 비슷한 걸 만들 수 있습니다. 이 명령은 `prospect_quartz()`입니다.

`prospect_quartz()`는 `prospect_iron()`과 다르게 작동합니다. 가장 가까운 철광석을 향해 드론이 이동할 방향을 반환하는 대신, 가장 가까운 석영 블록과 드론 사이의 정확한 3D 거리(유클리드 거리)를 반환하죠.

`prospect_quartz()`를 실행하면 철 1개를 소모하므로 명령을 최대한 안 쓰는 편이 좋습니다.

`prospect_quartz()`는 근처에서 석영을 찾지 못하거나 탐사할 철이 부족하면 `None`을 반환합니다.

## 전략
<spoiler=힌트 보기>탐사와 이동을 반복하며 거리가 어떻게 바뀌는지 볼 수 있습니다. 평평한 지면에서 거리를 최소화하려고 하다 보면 석영 광맥 바로 위에 도달할 수 있습니다. 이진 탐색과 비슷한 전략을 사용하면 `prospect_quartz()` 호출 횟수와 그에 드는 철의 양을 최소화할 수 있습니다.

더 복잡한 전략으로는 2D 기하학으로 둘 이상의 원이 만나는 지점을 구하거나, 어려운 길을 택해 완전한 삼변측량으로 세 구의 교점을 구해 광맥의 정확한 3D 위치를 찾을 수도 있습니다.

제곱근을 구하려면 지수 연산자를 사용하면 됩니다. 예를 들어 16의 제곱근은 `16**0.5`로 구할 수 있습니다. 삼각함수나 벡터를 위한 내장 수학 함수는 없으므로 직접 구현해야 합니다. 

또한 근처에 광맥이 여러 개 있을 수 있으므로, 가까운 곳에서 여러 번 측정하면 같은 광맥을 가리키지 않을 수도 있습니다.</spoiler>

---

[통계](docs/stats.md)      [채광](docs/unlocks/mining.md)      [지하 감지](docs/unlocks/underground_senses.md)      [변수](docs/scripting/variables.md)      [연산자](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
