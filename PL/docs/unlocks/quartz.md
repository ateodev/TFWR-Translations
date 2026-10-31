[<- Żelazo](docs/unlocks/iron.md) <right>[Grzyby ->](docs/unlocks/mushroom.md)
---
# Kwarc

Poniżej żył żelaza w `Grounds.Rock` znajdziesz kwarc w dolnej części warstwy skał i w twardej `Grounds.Dirt` poniżej (twardość sprawdzisz za pomocą `get_hardness()` z odblokowania [Podziemne zmysły](docs/unlocks/underground_senses.md)).

Poniższy fragment kodu przekopuje się przez ziemię do warstwy skał. Tam podczas kopania nieustannie szuka kwarcu, dopóki odległość nie spadnie poniżej 2. Na koniec wypisuje odległość, na której się zatrzymał.
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
# Kop w dół do warstwy skał
while get_ground_type() != Grounds.Rock:
    dig()

# Kop dalej, aż żyła kwarcu będzie blisko
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# Wypisz końcową odległość do żyły
print(prospect_quartz())
}}

## Struktura żył
Kwarc występuje w żyłach przypominających igły, które tworzą pionowe kolumny, dlatego trudno znaleźć je metodą prób i błędów.

## Poszukiwanie kwarcu
Na szczęście możemy przerobić żelazo na coś w rodzaju różdżki radiestezyjnej, która ułatwia odnajdywanie żył kwarcu. Służy do tego polecenie `prospect_quartz()`.

`prospect_quartz()` działa inaczej niż `prospect_iron()`. Zamiast kierunku, w którym dron ma się poruszyć, aby zbliżyć się do najbliższej rudy żelaza, zwraca dokładną odległość 3D między najbliższym blokiem kwarcu a dronem (odległość euklidesową).

Wykonanie `prospect_quartz()` kosztuje 1 żelazo, więc warto używać go oszczędnie.

Jeśli `prospect_quartz()` nie znajdzie kwarcu w pobliżu albo nie masz dość żelaza na poszukiwanie, zwróci `None`.

## Strategia
<spoiler=pokaż podpowiedź>Możesz wielokrotnie prowadzić poszukiwania i się przemieszczać, obserwując, jak zmienia się odległość. Na płaskiej powierzchni dążenie do jak najmniejszej odległości może doprowadzić cię nad żyłę kwarcu. Możesz użyć strategii podobnej do wyszukiwania binarnego, aby ograniczyć liczbę wywołań `prospect_quartz()` i ilość zużywanego przez nie żelaza.

Bardziej złożone strategie mogą wykorzystywać geometrię 2D do znalezienia punktu przecięcia dwóch lub więcej okręgów. Możesz też pójść trudniejszą drogą i użyć pełnej trilateracji, aby przeciąć trzy sfery i znaleźć dokładną pozycję 3D żyły.

Pamiętaj, że pierwiastek kwadratowy możesz obliczyć za pomocą operatora potęgowania, na przykład pierwiastek kwadratowy z 16 to `16**0.5`. Nie ma wbudowanych funkcji matematycznych do trygonometrii ani wektorów, więc musisz je napisać sam.

Pamiętaj też, że w pobliżu może być kilka żył, więc jeśli wykonasz kilka pomiarów blisko siebie, mogą nie wskazywać tej samej żyły.</spoiler>

---

[Statystyki](docs/stats.md)      [Górnictwo](docs/unlocks/mining.md)      [Podziemne zmysły](docs/unlocks/underground_senses.md)      [Zmienne](docs/scripting/variables.md)      [Operatory](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
