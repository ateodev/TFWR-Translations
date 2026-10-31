[<- Ryż](docs/unlocks/rice.md) <right>[Kolorowe bloki ->](docs/unlocks/debug_place.md)
<right>[Piramidy ->](docs/unlocks/pyramid.md)
---
# Bambus
Bambus to roślina, która rośnie w górę. Twój dron będzie musiał regularnie zrywać jego brązowe owoce, aby bambus mógł dalej rosnąć. Pomoże nam w tym nowo odblokowane polecenie `hover`.

Bambus trzeba sadzić na zaoranej glebie (`Grounds.Soil`), a jego sadzenie kosztuje ryż.

Poniższy kod sadzi bambus i czeka, aż urośnie do pierwszego owocu.
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
move(East) # odleć, aby bambus mógł rosnąć
}}

## Owoce
Bambus rośnie dokładnie o 1 blok na sekundę.

Co kilka bloków bambus wytwarza owoce. Gdy tak się stanie, bambus przestaje rosnąć i musisz wlecieć w niego dronem, aby zniszczyć owoc.

Aby zerwać owoce, musisz najpierw za pomocą `hover` wznieść się na odpowiednią wysokość. Następnie wykonaj `move` w stronę owocu, aby go zerwać, i znów `move`, aby odlecieć, dzięki czemu bambus będzie mógł dalej rosnąć.

Za pomocą `measure()` możesz sprawdzić, na jakiej wysokości pojawi się następny owoc. `measure()` liczy od `0`, więc `hover(measure())` przeniesie drona na wysokość, na której będzie owoc.

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
hover(measure()) # unieś się tak, aby dron był obok owocu

move(East) # odleć i poczekaj, aż urośnie
for i in range(3):
    do_a_flip()

move(West) # zerwij owoc
move(East) # znów odleć
}}

## Unoszenie się
Polecenie `hover` przyjmuje jeden argument: wysokość, na której dron ma się unosić. Jest to liczba od `0` do `18`. Domyślna wysokość unoszenia się drona to `1`. `hover` nie może przenieść drona w dół, w stałe obiekty, więc jeśli dron jest już nad bambusem, nie wleci w niego po wykonaniu `hover(0)`.

`hover` zwraca `True`, jeśli dron uniósł się na podaną wysokość, a w przeciwnym razie `False`.

Dostępne jest też polecenie `get_hover`, które zwraca bieżącą wysokość unoszenia się drona.

Jeśli podczas unoszenia się użyjesz `dig`, `harvest` lub `plant`, dron wróci na domyślną wysokość unoszenia się (`1`).

Na koniec: unoszenie się nie wpływa na `get_pos_z()`. Ta funkcja zawsze zwraca pozycję z bloku pod dronem.

## Zbieranie bambusa
Możesz użyć `harvest()`, ale zalecanym sposobem zbierania pól bambusa jest wlecenie w bambus dronem na wysokości unoszenia się `0` (`hover(0)`). Zbiera to całą roślinę naraz.

Jeśli chcesz zebrać bambus, nie niszcząc go, możesz wlecieć w niego za pomocą `move` na dowolnej wysokości, na przykład po `hover(3)`. Zbierzesz wtedy wszystkie kawałki bambusa od tej wysokości w górę, ale bambus pozostanie żywy. Bambusowi zebranemu częściowo w ten sposób odrosną owoce, więc trzeba będzie je ponownie zerwać.

W obu przypadkach plon jest równy kwadratowi liczby zniszczonych kawałków bambusa, więc im wyższy bambus, tym większy plon.

---

[Statystyki](docs/stats.md)      [Pętla For](docs/scripting/for.md)      [Zmienne](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Funkcje](docs/scripting/functions.md)      [Ryż](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
