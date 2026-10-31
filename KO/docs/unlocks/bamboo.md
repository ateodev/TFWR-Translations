[<- 벼](docs/unlocks/rice.md) <right>[알록달록 블록 ->](docs/unlocks/debug_place.md)
<right>[피라미드 ->](docs/unlocks/pyramid.md)
---
# 대나무
대나무는 위로 자라는 식물입니다. 대나무가 계속 자랄 수 있도록 드론이 갈색 열매를 주기적으로 따 주어야 합니다. 새로 해금된 `hover` 명령으로 이 일을 할 수 있습니다.

대나무는 경작된 토양(`Grounds.Soil`)에 심어야 하며, 대나무를 심으면 벼를 소모합니다.

다음 코드는 대나무를 심고 첫 열매가 열릴 때까지 자라기를 기다립니다.
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
move(East) # 대나무가 자랄 수 있도록 비켜 주기
}}

## 열매
대나무는 정확히 초당 1블록씩 자랍니다.

대나무는 몇 블록마다 열매를 맺습니다. 열매가 열리면 대나무는 자라기를 멈추며, 드론으로 대나무 안으로 날아 들어가 열매를 없애야 합니다.

열매를 따려면 먼저 `hover`로 알맞은 높이까지 떠올라야 합니다. 그런 다음 열매 쪽으로 `move`해서 열매를 따고, 대나무가 다시 자랄 수 있도록 다시 `move`해서 비켜 주어야 합니다.

대나무를 `measure()`하면 다음 열매가 어느 높이에 열릴지 확인할 수 있습니다. `measure()`는 `0`부터 세므로 `hover(measure())`를 사용하면 드론이 열매가 열릴 높이로 이동합니다.

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
hover(measure()) # 드론이 열매 옆에 오도록 떠오르기

move(East) # 비켜서 자라기를 기다리기
for i in range(3):
    do_a_flip()

move(West) # 열매 따기
move(East) # 다시 비켜 주기
}}

## 호버
`hover` 명령은 떠오를 높이를 인수 하나로 받으며, 이 값은 `0`부터 `18`까지의 숫자입니다. 드론의 기본 호버 높이는 `1`입니다. `hover`로는 단단한 엔티티 안으로 내려갈 수 없으므로, 드론이 이미 대나무 위에 있다면 `hover(0)`을 실행해도 대나무 안으로 들어갈 수 없습니다.

`hover`는 드론이 지정한 높이로 떠오르는 데 성공하면 `True`를, 그렇지 않으면 `False`를 반환합니다.

또한 드론의 현재 호버 높이를 반환하는 `get_hover` 명령도 있습니다.

호버 중에 `dig`, `harvest`, `plant`를 사용하면 드론은 기본 호버 높이(`1`)로 돌아갑니다.

마지막으로 `get_pos_z()`는 호버의 영향을 받지 않습니다. 항상 드론 아래에 있는 블록의 z 위치를 반환합니다.

## 대나무 수확하기
`harvest()`를 사용할 수도 있지만, 대나무 밭을 수확하는 데 권장되는 방법은 드론을 호버 높이 `0`(`hover(0)`)에 두고 대나무 안으로 이동하는 것입니다. 이렇게 하면 식물 전체를 한 번에 수확합니다.

대나무를 없애지 않고 수확하고 싶다면 아무 높이에서나, 예를 들어 `hover(3)`에서 대나무 안으로 `move`하면 됩니다. 이렇게 하면 그 높이부터 위쪽의 대나무 조각을 모두 수확하지만 대나무는 살아 있습니다. 이렇게 일부만 수확한 대나무는 열매가 다시 열리므로 열매를 다시 따 주어야 합니다.

어느 경우든 수확량은 없앤 대나무 조각 수의 제곱과 같으므로, 대나무가 높이 자랄수록 수확량이 늘어납니다.

---

[통계](docs/stats.md)      [for 루프](docs/scripting/for.md)      [변수](docs/scripting/variables.md)      [If문](docs/scripting/if.md)      [함수](docs/scripting/functions.md)      [벼](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
