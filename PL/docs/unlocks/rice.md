[<- Górnictwo](docs/unlocks/mining.md) <right>[Bambus ->](docs/unlocks/bamboo.md)
<right>[Skamieniałe dynie ->](docs/unlocks/petrified_pumpkins.md)
<right>[Perlit i gleba próchnicza ->](docs/unlocks/special_soils.md)
---
# Ryż

Pod powierzchnią i warstwą `Grounds.Dirt` mogłeś zauważyć cienką warstwę `Grounds.Clay`. Okazuje się, że to żyzne i nasiąknięte podłoże idealnie nadaje się do sadzenia ryżu.

Tak jak w przypadku trawy czy krzewów, dopóki dron znajduje się nad blokiem `Grounds.Clay`, możesz użyć `plant(Entities.Rice)`, aby posadzić sadzonki ryżu w glinie, następnie `can_harvest()`, aby sprawdzić, czy ryż w pełni urósł, a na koniec `harvest()`, aby zebrać ryż.

Gdy posadzisz ryż, podłoże zmieni się w `Grounds.Rice_Terrace`, aby zapewnić ryżowi idealne warunki do dojrzewania. Gdy ryż w pełni urośnie, podłoże wyschnie, zmieni się w `Grounds.Dry_Rice_Terrace` i nie można już na nim sadzić ryżu. Na szczęście warstwa ma grubość kilku bloków, więc możesz usunąć blok za pomocą `dig()` i posadzić nowy ryż na `Grounds.Clay` poniżej. A jeśli warstwa się skończy, zawsze możesz użyć `clear()` na świecie i dokopać się do świeżej warstwy.

Poniższy kod może pomóc ci kopać w dół, aż znajdziesz glinę.

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
    "exclude_unlocks": ["watering", "fertilizer"],
    "world_size": {"x": 4, "y": 4},
    "execution_speed": 8,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1
}
#SETUP
move(East)
#CODE
while get_ground_type() != Grounds.Clay:
    dig()
plant(Entities.Rice)
move(North)
do_a_flip()
}}

---

[Statystyki](docs/stats.md)      [Górnictwo](docs/unlocks/mining.md)      [Podziemne zmysły](docs/unlocks/underground_senses.md)      [If](docs/scripting/if.md)      [Pętla for](docs/scripting/for.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)
