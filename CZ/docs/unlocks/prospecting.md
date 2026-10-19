[<- Železo](docs/unlocks/iron.md)
---
# Hledání železa

Možná sis všiml, že železné žíly je někdy těžké najít. Mohl bys kopat kolem a zkoušet je najít náhodou, ale existuje lepší způsob: železo je magnetické, takže ho můžeme najít na dálku.

Přesně to dělá příkaz `prospect_iron()`. `prospect_iron()` vrací světovou stranu (`North`, `East`, `South` nebo `West`), kterou by se dron musel vydat, aby udělal krok k nejbližší železné rudě. Provedení příkazu stojí 1 uhlí.

`prospect_iron()` vrací `None`, pokud je dron už přímo nad nejbližší železnou rudou, pokud nemáš dost uhlí na provedení příkazu nebo pokud v dosahu žádné železo není.

Následující kód posune dron o krok blíž k nejbližší železné rudě:

`if prospect_iron() != None:
    move(prospect_iron())
`

Tento kód bys mohl optimalizovat pomocí proměnné, protože teď volá `prospect_iron()` dvakrát, což stojí 2 uhlí.

Nejbližší železná ruda se určuje podle počtu kroků, které musí dron udělat. Pokud je železná ruda 2 bloky na východ a 3 bloky na sever od dronu, počítá se to jako vzdálenost 5, protože by dronu trvalo pět kroků se tam dostat.

Kopání se také počítá jako krok. Takže pokud je železo navíc zakopané 7 bloků hluboko, počítá se to jako vzdálenost 12, protože by dron potřeboval pět kroků, aby se dostal nad železo, a pak sedm kopnutí, aby k němu dosáhl.

---

[Železo](docs/unlocks/iron.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[move()](functions/move)      [dig()](functions/dig)      [prospect_iron()](functions/prospect_iron)
