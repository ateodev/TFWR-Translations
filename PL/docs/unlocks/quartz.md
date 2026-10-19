[<- Żelazo](docs/unlocks/iron.md) <right>[Grzyby ->](docs/unlocks/mushroom.md)
---
# Kwarc

Poniżej żył żelaza w `Grounds.Rock` znajdziesz kwarc w dolnej części warstwy skał i w twardej `Grounds.Dirt` poniżej (twardość sprawdzisz za pomocą `get_hardness()` z odblokowania [Podziemne zmysły](docs/unlocks/underground_senses.md)).

Kwarc występuje w żyłach przypominających igły, które tworzą pionowe kolumny, dlatego trudno znaleźć je metodą prób i błędów.

Na szczęście możemy przerobić żelazo na coś w rodzaju różdżki radiestezyjnej, która ułatwia odnajdywanie żył kwarcu. Służy do tego polecenie `prospect_quartz()`.

`prospect_quartz()` działa inaczej niż `prospect_iron()`. Zamiast kierunku do najbliższej rudy kwarcu zwraca odległość euklidesową (odległość 3D) do najbliższego kwarcu. Wykonanie `prospect_quartz()` kosztuje 1 żelazo, więc warto używać go oszczędnie.

Jeśli `prospect_quartz()` nie znajdzie kwarcu w pobliżu albo nie masz dość żelaza na poszukiwanie, zwróci `None`.

Poniższy fragment kodu pozwala dronowi przekopać się przez ziemię i głęboko wejść w warstwę skał. Przy odrobinie szczęścia w pobliżu znajdzie się żyła kwarcu, a dron wyświetli odległość do niej.

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

Możesz wielokrotnie prowadzić poszukiwania i się przemieszczać, obserwując, jak zmienia się odległość, aby wiedzieć, czy zbliżasz się do żyły, czy się od niej oddalasz. Za pomocą geometrii 2D możesz znaleźć punkt przecięcia dwóch lub więcej okręgów, ustalić poziome położenie żyły i kopać w dół. Możesz też użyć pełnej trilateracji, aby przeciąć trzy sfery i znaleźć dokładną pozycję 3D.

Pamiętaj, że nie ma podstawowych funkcji matematycznych do pierwiastka kwadratowego, trygonometrii ani wektorów, więc musisz je napisać sam. Pamiętaj też, że w pobliżu może być kilka żył, więc jeśli wykonasz kilka pomiarów blisko siebie, mogą nie wskazywać tej samej żyły i wprowadzić cię w błąd.

---

[Statystyki](docs/stats.md)      [Górnictwo](docs/unlocks/mining.md)      [Podziemne zmysły](docs/unlocks/underground_senses.md)      [Zmienne](docs/scripting/variables.md)      [Operatory](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
