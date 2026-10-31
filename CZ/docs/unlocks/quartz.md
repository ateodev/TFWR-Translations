[<- Železo](docs/unlocks/iron.md) <right>[Houby ->](docs/unlocks/mushroom.md)
---
# Křemen
Pod železnými žílami v `Grounds.Rock` najdeš křemen ve spodní části kamenné vrstvy a v tvrdé `Grounds.Dirt` pod ní (tvrdost zjistíš pomocí `get_hardness()` z odemčení [Podzemní senzory](docs/unlocks/underground_senses.md)).

Následující úryvek kódu se prokope hlínou do kamenné vrstvy. Tam při kopání neustále hledá křemen, dokud není vzdálenost menší než 2. Nakonec vypíše vzdálenost, ke které dospěl.
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
# Prokopej se dolů ke kamenné vrstvě
while get_ground_type() != Grounds.Rock:
    dig()

# Kopej dál, dokud není křemenná žíla blízko
while prospect_quartz() == None or prospect_quartz() >= 2:
    for i in range(10):
        dig()

# Vypiš konečnou vzdálenost k žíle
print(prospect_quartz())
}}

## Struktura žil
Křemen roste v jehlicovitých žilách, které tvoří svislé sloupce, takže metodou pokusu a omylu se hledají dost těžko.

## Hledání křemene
Naštěstí můžeme vzít železo a zkroutit ho do něčeho jako proutkařskou hůlku, která nám pomůže křemenné žíly najít snadněji. Příkaz k tomu je `prospect_quartz()`.

`prospect_quartz()` funguje jinak než `prospect_iron()`. Místo směru, kterým se má dron vydat k nejbližší železné rudě, vrací přesnou 3D vzdálenost mezi nejbližším blokem křemene a dronem (eukleidovskou vzdálenost).

Provedení `prospect_quartz()` stojí 1 železo, takže je dobré příkaz používat střídmě.

Pokud `prospect_quartz()` poblíž žádný křemen nenajde nebo pokud nemáš dost železa na hledání, vrátí `None`.

## Strategie
<spoiler=zobrazit nápovědu>Můžeš opakovaně hledat a pohybovat se a sledovat, jak se mění vzdálenost. Na rovném povrchu tě snaha o co nejmenší vzdálenost může dovést nad křemennou žílu. Abys co nejvíc omezil počet volání `prospect_quartz()` a množství železa, které spotřebují, můžeš použít strategii podobnou binárnímu vyhledávání.

Pokročilejší strategie mohou pomocí 2D geometrie najít průsečík dvou nebo více kružnic, nebo se můžeš vydat obtížnější cestou a použít úplnou trilateraci, protnout tři koule a najít přesnou 3D polohu žíly.

Pamatuj, že odmocninu můžeš spočítat pomocí operátoru mocniny, například odmocninu ze 16 získáš jako `16**0.5`. Neexistují žádné základní matematické funkce pro goniometrii ani vektory, ty si musíš napsat sám. 

Pamatuj také, že poblíž může být víc žil, takže když uděláš několik blízkých měření, nemusí ukazovat na stejnou žílu.</spoiler>

---

[Statistiky](docs/stats.md)      [Těžba](docs/unlocks/mining.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)      [Proměnné](docs/scripting/variables.md)      [Operátoři](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
