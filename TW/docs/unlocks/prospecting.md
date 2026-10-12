[<- 鐵](docs/unlocks/iron.md)
---
# 鐵礦探勘

你可能已經注意到，有時候鐵礦脈很難找。你可以到處挖掘碰運氣，但還有更好的方法：由於鐵有磁性，我們可以從很遠的地方找到它。

`prospect_iron()` 指令正是做這件事。`prospect_iron()` 會回傳無人機要朝最近的鐵礦走一步所需移動的基本方向（`North`、`East`、`South` 或 `West`）。執行這個指令需要消耗 1 個煤炭。

如果無人機已經在最近的鐵礦正上方、煤炭不足以執行指令，或範圍內沒有鐵，`prospect_iron()` 會回傳 `None`。

你可以用下面的程式碼朝最近的鐵礦靠近一步：

`if prospect_iron() != None:
    move(prospect_iron())
`

你可能會想用變數來最佳化這段程式碼，因為它目前呼叫了兩次 `prospect_iron()`，消耗 2 個煤炭。

最近的鐵礦是以無人機需要走的步數來計算的。如果有一塊鐵礦在無人機東邊 2 格、北邊 3 格的位置，距離就算作 5，因為無人機需要走五步才能到達。

挖掘也算一步。所以如果那塊鐵還埋在地下 7 格深，距離就算作 12，因為無人機需要走五步到鐵的上方，再挖七次才能到達。

---

[鐵](docs/unlocks/iron.md)      [地下感測](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [prospect_iron()](functions/prospect_iron)
