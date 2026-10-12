[<- 鐵](docs/unlocks/iron.md)
---
# 藏寶圖

傳說有一位早已過世、健忘的海盜藏了一筆難以捉摸的寶藏，大概是這樣。要是他們把通往寶藏的路徑寫在地圖上，然後又把地圖弄丟了呢？也許他們被熔岩河逼到角落時掉了地圖，而地圖就保存在一層玄武岩下方。測量玄武岩或許能發現什麼。

<spoiler=再多說一點>
你應該留意 `Grounds.Basalt` 地層。試著測量玄武岩，看看它會告訴你什麼。這個提示可能會把你引向藏寶圖，而測量藏寶圖一定會回傳通往寶藏本身的路徑，但你能解讀地圖給你的指示嗎？
</spoiler>

<spoiler=直接告訴我怎麼做>
好吧，是這樣的：找到 `Grounds.Basalt` 地層以及它正下方的 `Grounds.Treasure_Map` 方塊。你可以對玄武岩 `measure()`，取得下方地圖方塊的 `(x, y)` 位置。

在地圖方塊上呼叫 `measure()`，會以方向字母字串的形式取得藏寶路徑。N、E、S 和 W 分別代表 `North`、`East`、`South` 和 `West`，而 D 代表「向下」或「挖掘」。這些字母描述了一條由 `Grounds.Treasure_Path` 方塊組成、通往寶藏的路徑。

```
path = measure()
for letter in path:
    do_something(letter)
```

挖進藏寶圖方塊的那台無人機必須是去找寶藏的那台。它必須全程待在 `Grounds.Treasure_Path` 方塊上。如果它移動到其他地面，路徑就會中斷，寶藏也會消失。

路徑的盡頭是一個 `Grounds.Treasure_Goal` 方塊。如果無人機沒有偏離路徑，它上面就會出現一個 `Entities.Underground_Treasure`。無人機可以 `harvest()` 這個寶箱來收集裡面的黃金。

黃金的數量與藏寶路徑的長度成正比。升級藏寶圖解鎖項會增加路徑的深度，而升級擴張則會給它更多橫向移動的空間。這兩種升級都會增加藏寶路徑的長度和你能找到的黃金數量。
</spoiler>

---

[統計資料](docs/stats.md)      [for 迴圈](docs/scripting/for.md)      [元組](docs/scripting/tuples.md)      [地下感測](docs/unlocks/underground_senses.md)

[harvest()](functions/harvest)      [move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)
