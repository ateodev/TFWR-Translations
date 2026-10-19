[<- Rozšíření 1](docs/unlocks/expand_1.md) <right>[Podzemní senzory ->](docs/unlocks/underground_senses.md)
<right>[Rýže ->](docs/unlocks/rice.md)
<right>[Uhlí ->](docs/unlocks/coal.md)
---
# Těžba

Tvůj dron získal primitivní vrták, se kterým může hledat poklady v podzemí.

Příkazem `dig()` kopeš do bloku pod sebou.

Pro začátek nasbíráme pár bloků:

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
    "execution_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal", "special_soils"]
}
#SETUP
move(North)
move(East)
#CODE
dig()
do_a_flip()
dig()
do_a_flip()
dig()
do_a_flip()
clear()
}}

Pokud se chceš vrátit na povrch, můžeš kdykoli použít `clear()`. To zároveň obnoví tvou farmu.

<desktop>Najetí myší na blok</desktop><mobile>Klepnutí na blok</mobile> zobrazí jeho název, stabilitu a tvrdost.

# Vrták

Čím hlouběji kopeš, tím tvrdší jsou bloky a tím déle kopání trvá. Naštěstí si můžeme vrták vylepšit!

Aby se tvůj dron v podzemí vyznal, měl bys rychle odemknout [podzemní senzory](docs/unlocks/underground_senses.md). Díky nim zjistí svou vlastní pozici z a také druh půdy pod sebou, její tvrdost a stabilitu.

S [podzemními senzory](docs/unlocks/underground_senses.md) například pomocí `get_hardness()` zjistíš tvrdost bloku pod sebou. Pokud narazíš na oblast obzvlášť tvrdých bloků, může být moudré je obejít, abys postupoval rychleji:

`while True:
        if get_hardness() < 5:
                dig()
        else:
                move(East)`

Bloky jsou samozřejmě čím dál tvrdší, takže tahle strategie sice pomáhá, ale jen do určité míry.

## Sesuvy

Kopání dolů způsobí sesuv okolních bloků. Čtyři bloky vedle dronu jsou zničeny vždy. Poté se sesuv šíří podle stability půdy. Blok se stabilitou 1, například louka, vydrží výškový rozdíl 1. Jinými slovy, pokud má louka svislého nebo vodorovného souseda, jehož souřadnice z je o 2 nebo více bloků hlouběji, louka se zničí.

Stabilita bloku je uvedena v jeho nápovědě<desktop> po najetí myší</desktop>.

Když se blok sesune, odstraní i všechny bloky nad sebou. Suroviny získáš jen z bloků, které dron vykope přímo, takže bloky ztracené při sesuvu se zničí bez jakéhokoli výnosu.

---

[Podzemní senzory](docs/unlocks/underground_senses.md)      [While Loop](docs/scripting/while.md)

[move()](functions/move)      [dig()](functions/dig)
