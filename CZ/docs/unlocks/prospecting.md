[<- Železo](docs/unlocks/iron.md)
---
# Hledání železa

Možná sis všiml, že železné žíly je někdy těžké najít. Mohl bys kopat kolem a zkoušet je najít náhodou, ale existuje lepší způsob: železo je magnetické, takže ho můžeme najít na dálku.

Přesně to dělá příkaz `prospect_iron()`. `prospect_iron()` vrací světovou stranu (`North`, `East`, `South` nebo `West`), kterou by se dron musel vydat, aby udělal krok k nejbližší železné rudě.

Provedení příkazu stojí 1 uhlí.

`prospect_iron()` vrací `None`, pokud je dron už přímo nad nejbližší železnou rudou, pokud nemáš dost uhlí na provedení příkazu nebo pokud v dosahu žádné železo není.

Následující kód posune dron o krok blíž k nejbližší železné rudě:

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
    "items": [{"item": "coal", "n": 100}],
    "world_size": {"x": 5, "y": 5},
    "execution_speed": 1,
    "digging_speed": 10,
    "action_ticks": 200,
    "operation_ticks": 50,
    "seed": 8,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "quartz"]
}
#SETUP
jump(Unlocks.Iron)
#CODE
if prospect_iron() != None:
    move(prospect_iron())
}}

Tento kód bys mohl optimalizovat pomocí proměnné, protože teď volá `prospect_iron()` dvakrát, což stojí 2 uhlí.

## Výpočet vzdálenosti
Nejbližší železná ruda se určuje podle počtu kroků, které musí dron udělat. Pokud je železná ruda 2 bloky na východ a 3 bloky na sever od dronu, počítá se to jako vzdálenost 5, protože by dronu trvalo pět kroků se tam dostat.

Kopání se také počítá jako krok. Takže pokud je železo navíc zakopané 7 bloků hluboko, počítá se to jako vzdálenost 12, protože by dron potřeboval pět kroků, aby se dostal nad železo, a pak sedm kopnutí, aby k němu dosáhl.

---

[Železo](docs/unlocks/iron.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [prospect_iron()](functions/prospect_iron)
