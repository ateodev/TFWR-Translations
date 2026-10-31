[<- Houby](docs/unlocks/mushroom.md) <right>[Výbušný vrták ->](docs/unlocks/explosive_drill.md)
---
# Dynamit
Revoluční výbušnina, kterou tu nechaly dřívější těžařské výpravy. Bohužel je tvůj vrták ideální k tomu, aby dynamit odpálil a odstřelil všechny bloky kolem tebe. Sebraný dynamit lze použít pomocí `use_item(Items.Dynamite)` a vybuchne okamžitě pod dronem.

Abys dynamit bezpečně vytěžil, najdi vrstvu `Grounds.Dynamite`, pod kterou hned následuje vrstva `Grounds.Soot`. Dynamitová vrstva nahoře už trochu zestárla a do některých jejích bloků se dá bezpečně kopat. Některé bloky dynamitu jsou ale stále živé a vybuchnou, když do nich kopneš.

Tento příklad kopne do dynamitu a pak všude kolem prvního místa kopnutí, čímž odkryje vrstvu sazí s čísly, a vypisuje naměřené hodnoty:
{{codeexample 
{
    "camera_position": {"x": -3, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 800, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 7, "y": 7},
    "execution_speed": 2,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 6,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(3):
    move(East)
    move(North)
#CODE
# Prokopej se dolů přes dynamitovou vrstvu až k vrstvě sazí
while get_ground_type() != Grounds.Soot:
    dig()

# Seznam směrů, díky kterým se dron pohybuje v kruhu
circle_directions = [
    East, South, West, West, 
    North, North, East, East
]
for dir in circle_directions:
    move(dir)
    dig()
    print(measure()) # Číslo na bloku sazí
}}

## Dynamitové hledání min
Dokážeš najít a vykopat všechny slepé bloky dynamitu a nechat jen ty živé? Každý živý blok obklopený jen dalšími živými bloky nebo bloky sazí ti dá dynamit navíc, jakmile dynamitová vrstva zmizí.

Naštěstí ti pomohou bloky sazí dole: dokážou zjistit počet sousedních dynamitových bloků, které obsahují živý dynamit. Neřeknou ti přesně, které bloky jsou živé, jen celkový počet, takže musíš zkombinovat údaje z více bloků sazí a vymyslet to sám.

Volání `measure()` na bloku sazí vrátí počet min v osmi sousedních políčkách dynamitové vrstvy nad ním. Číslo může být od `0` (žádné živé miny) do `8` (každý soused obsahuje živou minu).

První kopnutí do dynamitové vrstvy je vždy slepé. Každý vytěžený blok dynamitu dá trochu dynamitu. Když je dynamitová vrstva zničena, ať už úspěšným vykopáním všech slepých bloků, nebo nechtěným kopnutím do živého dynamitu, získáš navíc dynamit v množství rovném druhé mocnině počtu plně odkrytých živých bloků.

## Struktura vrstev
Počet živých min v dynamitové vrstvě, a tedy i obtížnost jejich nalezení, roste s hloubkou. Celkový počet min roste s velikostí farmy, a s ním i nejvyšší možný výnos za vyčištění dynamitové vrstvy.

Vylepši dynamit, aby se zvýšil výnos z kopání do dynamitových bloků a z plného odkrytí živých bloků. Vylepšení také zvýší energii explozí dynamitu o 30 %.

## Jak poznat úspěch a neúspěch
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

## Strategie
<spoiler=nápověda>
Následující kód kopne do dynamitové vrstvy a hledá bloky sazí, které naměří `0`. U každého takového bloku vykope všechny dynamitové bloky, které ho obklopují:
{{codeexample 
{
    "camera_position": {"x": -5, "y": 0, "z": 15},
    "show_image": true,
    "image_size": {"x": 800, "y": 500},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 7, "y": 7},
    "execution_speed": 4,
    "digging_speed": 8,
    "action_ticks": 200,
    "operation_ticks": 20,
    "seed": 6,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "quartz", "petrified_pumpkins"]
}
#SETUP
jump(Unlocks.Dynamite)
for _ in range(3):
    move(East)
    move(North)
#CODE
while get_ground_type() != Grounds.Soot:
    dig()

circle_directions = [
    East, South, West, West, North,
    North, East, East, South, West
]
# Obejdi blok, do kterého jsme kopli jako první
for dir in circle_directions:
    # Pokud saze naměří 0,
    # víme, že všechny okolní dynamitové bloky jsou slepé
    if get_ground_type() == Grounds.Soot and measure() == 0:
        # Udělej další kruh přes okolní bloky
        for dir2 in circle_directions:
            move(dir2)
            # Vykopej slepý blok dynamitu
            while get_ground_type() != Grounds.Soot:
                dig()
    move(dir)
}}
</spoiler>

---

[Statistiky](docs/stats.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)      [Slovníky](docs/scripting/dicts.md)      [Množiny](docs/scripting/sets.md)

[move()](functions/move)      [dig()](functions/dig)      [measure()](functions/measure)      [use_item()](functions/use_item)
