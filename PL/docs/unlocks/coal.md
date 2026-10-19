[<- Górnictwo](docs/unlocks/mining.md) <right>[Żelazo ->](docs/unlocks/iron.md)
<right>[Skok ->](docs/unlocks/jump.md)
---
# Węgiel

Pod ziemią kryją się różne rudy, które czekają, aż je znajdziesz i wykopiesz. Jeśli przekopiesz się przez powierzchnię do `Grounds.Dirt`, pierwszą rudą, jaką znajdziesz, będzie węgiel.

Jego żyły tworzą poziome pokłady o grubości 1 bloku, które musisz znaleźć przypadkiem, przekopując się przez ziemię. Bloki węgla w pokładzie leżą zwykle tuż obok siebie, ale niektóre mogą łączyć się tylko po przekątnej.

Aby wydobyć węgiel, nie musisz robić nic specjalnego: wystarczy wykonać `dig()`, gdy dron znajduje się bezpośrednio nad blokiem `Grounds.Coal`. Użyj `get_ground_type()`, aby sprawdzić, co jest pod dronem, i `get_ground_type(direction)`, aby sprawdzić cztery sąsiednie bloki.

Pamiętaj, że węgiel dostajesz tylko za bloki węgla, w które kopiesz bezpośrednio, a nie za bloki, które zawalą się wokół drona. Weź to pod uwagę, planując wydobycie węgla, aby wydobyć jak najwięcej bloków węgla, a jak najmniej stracić w zawałach.

Kopalnie węgla rosną proporcjonalnie do rozmiaru farmy, więc rozważ dalsze odblokowywanie [Rozszerzenia](unlocks/expand), aby zwiększyć ilość węgla, którą możesz wydobyć.

Poniższy program to dobry punkt wyjścia do poszukiwania węgla. Kopie w dół w poszukiwaniu pokładu, a następnie na wschód i zachód, licząc na znalezienie większej ilości węgla.

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
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2
}
#SETUP
move(North)
move(East)
move(East)
#CODE
while get_ground_type() != Grounds.Coal:
    dig()
do_a_flip()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

Prosta strategia, zwłaszcza na mniejszych farmach, to wykopanie wszystkich bloków na głębokości, na której znalazłeś blok węgla. Aby działać wydajniej, możesz zapamiętywać za pomocą `get_ground_type(direction)`, gdzie widziałeś bloki węgla, i nie tracić czasu na przechodzenie nad blokami ziemi. Uważaj szczególnie, by nie przeoczyć połączeń po przekątnej, które ominiesz, jeśli będziesz poruszać się tylko nad blokami węgla.

---

[Statystyki](docs/stats.md)      [Górnictwo](docs/unlocks/mining.md)      [Podziemne zmysły](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
