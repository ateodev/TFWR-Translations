[<- 채광](docs/unlocks/mining.md) <right>[철 ->](docs/unlocks/iron.md)
<right>[점프 ->](docs/unlocks/jump.md)
---
# 석탄
땅속에는 여러 광석이 숨겨져 있어 당신이 찾아내 캐내기를 기다리고 있습니다. 지표를 뚫고 `Grounds.Dirt`까지 파 내려가면 가장 먼저 찾게 되는 광석은 석탄입니다.

석탄을 캐는 데 특별한 것은 필요 없습니다. 드론이 `Grounds.Coal` 블록 바로 위에 있을 때 `dig()`를 실행하기만 하면 됩니다. `get_ground_type()`로 드론 아래에 무엇이 있는지, `get_ground_type(direction)`로 인접한 네 블록을 확인할 수 있습니다.

다음 프로그램은 석탄을 찾는 좋은 시작점입니다. 석탄층을 찾아 아래로 굴착합니다.
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
    "items": [],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2,
    "exclude_unlocks": ["watering", "fertilizer"]
}
#SETUP
move(North)
move(East)
move(East)
#CODE
# 석탄 블록이 나올 때까지 파기
while get_ground_type() != Grounds.Coal:
    dig()

# 석탄 캐기
dig()
}}

## 붕괴에 관한 참고 사항
석탄은 직접 판 석탄 블록에 대해서만 얻을 수 있고, 드론 주변에서 무너진 블록에서는 얻을 수 없습니다. 석탄을 캐는 방법을 구상할 때 이 점을 염두에 두고, 붕괴로 잃는 블록보다 캐내는 석탄 블록이 최대한 많아지도록 하세요.

## 광맥 구조
석탄 광맥은 두께가 1블록인 수평 층을 이루며, 흙을 파 내려가다가 우연히 찾아야 합니다. 한 층 안의 석탄 블록은 대부분 바로 옆에 붙어 있지만, 일부는 대각선으로만 이어져 있을 수도 있습니다.

탄광은 농장 크기에 비례해 커지므로, 캘 수 있는 석탄의 양을 늘리려면 [확장](unlocks/expand)을 더 해금하는 것도 고려해 보세요.

## 전략
<spoiler=힌트 보기>
특히 작은 농장에서는 석탄 블록을 찾은 깊이의 모든 블록을 파내는 것이 간단한 전략입니다. 효율을 높이려면 `get_ground_type(direction)`로 석탄 블록을 본 위치를 기록해 두고 흙 블록 위를 지나느라 시간을 낭비하지 않도록 하세요. 석탄 블록 위로만 이동하면 대각선 연결을 놓치게 되니 특히 주의해야 합니다.
</spoiler>

---

[통계](docs/stats.md)      [채광](docs/unlocks/mining.md)      [지하 감지](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
