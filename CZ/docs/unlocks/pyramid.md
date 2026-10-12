[<- Bambus](docs/unlocks/bamboo.md)
---
# Pyramidy

V podzemí se teď nacházejí starověké pyramidové stavby, ze kterých můžeš získávat energii!

Pyramidy jsou z bloků písku (`Grounds.Sand`). Pod samotnou pyramidou je základová vrstva vápence (`Grounds.Limestone`). Protože jsou staré a zvětralé, najdeš je jen částečně zničené. Základová vrstva je vždy přítomná, ale v písku budou díry. Takhle vypadá pyramida, když ji vykopeš:

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
    "items": [{"item": "hay", "n": 100}, {"item": "block", "n": 100}],
    "world_size": {"x": 6, "y": 6},
    "execution_speed": 32,
    "digging_speed": 16,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 7,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "dynamite", "quartz"]
}
#SETUP
jump(Unlocks.Pyramid)
move(North)
#CODE
while get_ground_type() != Grounds.Limestone:
    dig()
do_a_flip()
z = get_pos_z()
for i in range(6):
    for j in range(6):
        while (get_ground_type() != Grounds.Limestone
                and get_ground_type() != Grounds.Sand
                and get_pos_z() > z):
            dig()
        move(North)
    move(East)
}}

Bloky nad pyramidou jsou vždy hlína. Pokud chceš pyramidu vykopat efektivněji než výše uvedený kód, můžeš toho využít.

Jak vidíš, v písku je několik děr, které bude třeba zaplnit. Když tyto díry zaplníš a obnovíš pyramidu do původního stavu, sama se zničí a ty dostaneš jako odměnu energii.

Pyramidu obnovíš pokládáním bloků příkazem `place(Grounds.Sand)`. Písek je speciální blok, který se okamžitě sesune, když není správně podepřený. Blok písku musí být položen buď přímo na vápenec, nebo na čtverec 3x3 bloků písku. Pro ukázku malá ručně postavená pyramida. Vlastnoruční stavba ti samozřejmě žádnou energii nedá:

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
    "items": [{"item": "hay", "n": 100}, {"item": "block", "n": 100}],
    "world_size": {"x": 3, "y": 3},
    "execution_speed": 4,
    "digging_speed": 4,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 9,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz"]
}
#CODE
for i in range(3):
    for j in range(3):
        place(Grounds.Limestone)
        move(North)
    move(East)
    
for i in range(3):
    for j in range(3):
        place(Grounds.Sand)
        move(North)
    move(East)
    
move(North)
move(East)
place(Grounds.Sand)
}}

Správně obnovená pyramida se skládá ze čtvercového vápencového základu s lichou délkou strany, například 5x5. Nad ním je vrstva bloků písku stejné velikosti (5x5) a pak postupně menší vrstvy: 3x3 a potom 1x1.

Když je pyramida dokončena, rozpadne se a uprostřed se objeví velká slunečnice. Sklidíš ji a získáš energii. Čím větší pyramidu dokončíš, tím více energie dostaneš.

---

[Statistiky](docs/stats.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [use_item()](functions/use_item)      [place()](functions/place)
