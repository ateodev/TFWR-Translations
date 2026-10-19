[<- Železo](docs/unlocks/iron.md) <right>[Houby ->](docs/unlocks/mushroom.md)
---
# Křemen

Pod železnými žílami v `Grounds.Rock` najdeš křemen ve spodní části kamenné vrstvy a v tvrdé `Grounds.Dirt` pod ní (tvrdost zjistíš pomocí `get_hardness()` z odemčení [Podzemní senzory](docs/unlocks/underground_senses.md)).

Křemen roste v jehlicovitých žilách, které tvoří svislé sloupce, takže metodou pokusu a omylu se hledají dost těžko.

Naštěstí můžeme vzít železo a zkroutit ho do něčeho jako proutkařskou hůlku, která nám pomůže křemenné žíly najít snadněji. Příkaz k tomu je `prospect_quartz()`.

`prospect_quartz()` funguje jinak než `prospect_iron()`. Místo směru k nejbližší křemenné rudě vrací eukleidovskou vzdálenost (vzdálenost ve 3D) k nejbližšímu křemeni. Provedení `prospect_quartz()` stojí 1 železo, takže je dobré příkaz používat střídmě.

Pokud `prospect_quartz()` poblíž žádný křemen nenajde nebo pokud nemáš dost železa na hledání, vrátí `None`.

Následující úryvek kódu nechá dron prokopat se hlínou hluboko do kamenné vrstvy. Pak s trochou štěstí bude poblíž křemenná žíla a dron vypíše vzdálenost k ní.

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

Můžeš opakovaně hledat a pohybovat se a sledovat, jak se mění vzdálenost, abys poznal, jestli se k žíle přibližuješ, nebo se od ní vzdaluješ. Pomocí 2D geometrie můžeš najít průsečík dvou nebo více kružnic, určit vodorovnou polohu žíly a kopat dolů. Nebo můžeš použít úplnou trilateraci, protnout tři koule a najít přesnou 3D polohu.

Pamatuj, že neexistují žádné základní matematické funkce pro odmocninu, goniometrii ani vektory, ty si musíš napsat sám. Pamatuj také, že poblíž může být víc žil, takže když uděláš několik blízkých měření, nemusí ukazovat na stejnou žílu a mohou tě svést z cesty.

---

[Statistiky](docs/stats.md)      [Těžba](docs/unlocks/mining.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)      [Proměnné](docs/scripting/variables.md)      [Operátoři](docs/scripting/operators.md)

[move()](functions/move)      [dig()](functions/dig)      [get_ground_type()](functions/get_ground_type)      [prospect_quartz()](functions/prospect_quartz)
