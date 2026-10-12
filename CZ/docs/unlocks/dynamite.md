[<- Houby](docs/unlocks/mushroom.md) <right>[Výbušný vrták ->](docs/unlocks/explosive_drill.md)
---
# Dynamit

Revoluční výbušnina, kterou tu nechaly dřívější těžařské výpravy. Naštěstí (nebo bohužel) je tvůj vrták ideální k tomu, aby dynamit odpálil a odstřelil všechny bloky kolem tebe.

Abys dynamit bezpečně vytěžil, musíš najít dvojitou vrstvu `Grounds.Dynamite` a `Grounds.Soot`. Dynamitová půda nahoře už trochu zestárla a do některých jejích bloků se dá bezpečně kopat. Část dynamitu je ale stále živá a při vykopání vybuchne.

{{codeexample 
{
    "camera_position": {"x": -3, "y": -3, "z": 12},
    "show_image": true,
    "image_size": {"x": 900, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": false,
    "autoplay": true,
    "items": [{"item": "hay", "n": 100}],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 8,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 4,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()
dig()
dig()
}}

Dokážeš najít a vykopat všechny slepé bloky a nechat jen ty živé? Každý živý blok obklopený jen dalšími živými bloky nebo bloky sazí ti dá dynamit navíc, jakmile dynamitová vrstva zmizí.

Naštěstí ti pomohou bloky sazí dole: dokážou zjistit počet sousedních dynamitových bloků, které obsahují živý dynamit. Neřeknou ti přesně, které bloky jsou živé, jen celkový počet, takže musíš zkombinovat údaje z více bloků sazí a vymyslet to sám.

Volání `measure()` na bloku sazí vrátí počet min v osmi sousedních políčkách dynamitové vrstvy nad ním. Číslo může být od `0` (žádné živé miny) do `8` (každý soused obsahuje živou minu).

První kopnutí do dynamitové vrstvy je vždy slepé. Každý vytěžený blok dynamitu dá trochu dynamitu. Když je dynamitová vrstva zničena, ať už úspěšným vykopáním všech slepých bloků, nebo nechtěným kopnutím do živého dynamitu, získáš navíc dynamit v množství rovném druhé mocnině počtu plně odkrytých živých bloků.

Pokud kopneš do živého dynamitu, obě vrstvy vybuchnou. Můžeš to zkontrolovat pomocí `get_ground_type()` po kopnutí do `Grounds.Dynamite`. Pokud půda není `Grounds.Soot`, hádanku jsi nevyřešil. Naopak pokud vykopeš poslední slepý blok dynamitu, všechny dynamitové bloky zmizí a získáš maximální výnos z hádanky. Vrstva sazí zůstane, ale `measure()` vrací `None`, což znamená, že hádanka byla úspěšně vyřešena.

`# Kopni do dynamitového bloku a zkontroluj stav hádanky
def dig_dynamite():
    dig()
    if get_ground_type() != Grounds.Soot:
        # Kopnuto do živého dynamitu, hádanka selhala
        return False
    elif measure() == None:
        # Vykopán poslední slepý blok, hádanka vyřešena
        return True
    else:
        # Měření vrátilo počet, hádanka pokračuje
        return None
`

Počet živých min v dynamitové vrstvě, a tedy i obtížnost jejich nalezení, roste s hloubkou.

Sebraný dynamit lze použít pomocí `use_item(Items.Dynamite)`; vybuchne okamžitě pod dronem.

Vylepši dynamit, aby se zvýšil výnos z kopání do dynamitových bloků a z plného odkrytí živých bloků. Vylepšení také zvýší energii explozí dynamitu o 30 %.

---

[Statistiky](docs/stats.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)      [Slovníky](docs/scripting/dicts.md)      [Sets](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
