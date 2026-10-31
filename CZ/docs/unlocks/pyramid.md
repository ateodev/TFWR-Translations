[<- Bambus](docs/unlocks/bamboo.md)
---
# Pyramidy
V podzemí se teď nacházejí starověké pyramidové stavby, ze kterých můžeš získávat energii, která zrychlí tvůj dron!

Pyramidy jsou z bloků písku (`Grounds.Sand`). Pod samotnou pyramidou je základová vrstva vápence (`Grounds.Limestone`). Protože jsou staré a zvětralé, najdeš je jen částečně zničené. Základová vrstva je vždy přítomná, ale v písku budou díry.

Takhle vypadá ruina pyramidy, když ji vykopeš:
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
# Kopej dolů, dokud nenajdeš základ pyramidy
while get_ground_type() != Grounds.Limestone:
    dig()

z = get_pos_z() # Zapamatuj si hloubku základu

# Vykopej všechno, co není součástí pyramidy
for i in range(6):
    for j in range(6):
        while (get_ground_type() != Grounds.Limestone
                and get_ground_type() != Grounds.Sand
                and get_pos_z() > z):
            dig()
        move(North)
    move(East)
}}

## Obnovení pyramidy
Jak vidíš, v písku je několik děr, které bude třeba zaplnit. Když tyto díry zaplníš a obnovíš pyramidu do původního stavu, sama se zničí a uprostřed vápencového základu se objeví velká slunečnice. Sklidíš ji a získáš `Items.Power`. Čím větší pyramidu dokončíš, tím více energie dostaneš.

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
# Potřebujeme vápencový základ, na který položíme písek
for i in range(3):
    for j in range(3):
        place(Grounds.Limestone)
        move(North)
    move(East)

# Polož na vápenec vrstvu písku 3x3
for i in range(3):
    for j in range(3):
        place(Grounds.Sand)
        move(North)
    move(East)

# Zkus položit další vrstvu 3x3
# Všimni si, že podepřený je jen prostřední blok, a jen ten zůstane
for i in range(3):
    for j in range(3):
        place(Grounds.Sand)
        move(North)
    move(East)
}}

Správně obnovená pyramida se skládá ze čtvercového vápencového základu s lichou délkou strany, například 5x5. Nad ním je vrstva bloků písku stejné velikosti (5x5) a pak postupně menší vrstvy: 3x3 a potom 1x1.

Bloky nad pyramidou jsou vždy hlína. Pokud chceš pyramidu vykopat efektivně, můžeš toho využít.

## Energie
Dokud máš energii, dron ji využije k běhu dvojnásobnou rychlostí.
Spotřebuje 1 energii každých 30 akcí, jako jsou pohyby, sklizně nebo sázení.
Provádění jiných programových příkazů může energii také spotřebovávat, ale mnohem méně než akce dronu.

Obecně platí, že vše, co zrychlují vylepšení rychlosti, zrychluje i energie.
Cokoli je zrychlené energií, zároveň spotřebovává energii úměrně času vykonávání, bez ohledu na vylepšení rychlosti.

Energie nemá vliv na `dig()`.

---

[Statistiky](docs/stats.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [use_item()](functions/use_item)      [place()](functions/place)
