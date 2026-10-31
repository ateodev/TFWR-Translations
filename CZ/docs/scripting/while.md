[<- První Program](docs/first_program.md) <right>[Zvýšení rychlosti ->](docs/unlocks/speed.md)
---
# While Loop
Odemkl jsi smyčku `while` a hodnoty `True` a `False`. Smyčka `while` opakovaně provádí tělo smyčky tak dlouho, dokud je podmínka `True`.

`while condition:
	#tělo smyčky`

Nemusíš se bát vytvořit nekonečnou smyčku. Dron se sice může zaseknout, ale celou hru nezmrazí. Běžící program prostě zastavíš a zkusíš to znovu.

## Pro začátečníky
Možná jsi už zkusil napsat několik příkazů `harvest()` za sebou:

{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
do_a_flip()
#CODE
harvest()
harvest()
harvest()
}}
To umožní sklidit několikrát v jednom běhu programu. 
Bylo by ale fajn sklízet víc než jen třikrát a psaní stejného kódu několikrát za sebou z programu rychle udělá nepořádek.
Řešením je smyčka.
Smyčka ti umožní spouštět stejný kód opakovaně.

Smyčka while používá podmínku, což je logická hodnota, která může mít pouze dva stavy: `True` nebo `False`. 
Taková hodnota se nazývá booleovská hodnota.

Smyčka pak provádí kód uvnitř sebe, dokud není podmínka False.
Smyčka while vypadá takto:

`while condition:
	#tělo smyčky
	#tělo smyčky
	#...`

Na místě slova condition musíš uvést booleovskou (logickou) podmínku, a na místě `#tělo smyčky` pak napsat příkazy, které se mají ve smyčce provádět.

Existují dvě konstantní booleovské hodnoty. Konstanty jsou hodnoty, které se během běhu programu nemění.

Pokud chceš vytvořit boolean hodnotu (tedy hodnotu typu pravda/nepravda), která je vždy `True`, jednoduše napiš `True`. Pokud chceš vytvořit hodnotu, která je vždy `False` napiš `False`.
Takže můžeš napsat například:

{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
#CODE
while False:
	do_a_flip()
}}
nebo

{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
#CODE
while True:
	do_a_flip()
}}
První příklad nikdy neudělá otočku, zatímco druhý bude dělat otočky neustále (nekonečná smyčka).

Normálně je vytvoření nekonečné smyčky špatný nápad, protože by program zamrzl.
Ale v této hře jsou mezi jednotlivými cykly smyčky malé prodlevy, takže dron bude pokračovat v otočkách, dokud program ručně nezastavíš opětovným stisknutím tlačítka pro spuštění.

Všimni si, že řádek za dvojtečkou je odsazený.
Takové odsazení se používá k oddělení bloků kódu.
Pro přidání odsazení stiskni Tab, a pro jeho odstranění Shift + Tab (nebo <desktop>Backspace</desktop><mobile>Smazat</mobile>). Pokud je vybráno více řádků, Tab i Shift + Tab se použijí na všechny.

<desktop>Poznámka: pokud hraješ hru přes Steam, stisknutí Shift + Tab místo toho otevře překryvné okno Steamu. Zkratku pro zrušení odsazení můžeš změnit v nastavení hry, nebo zkratku překryvného okna v nastavení překryvného okna Steamu.
</desktop>
Zde se `do_a_flip()` a `pet_the_piggy()` volají opakovaně, protože jsou uvnitř odsazeného bloku `while`. Funkce `harvest()` se ale nikdy nespustí, protože následuje až za tímto blokem.
{{codeexample 
{
    "camera_position": {"x": 0, "y": 1.5, "z": 4},
    "show_image": true,
    "image_size": {"x": 800, "y": 300},
    "show_code": true,
    "show_inventory": true,
    "show_output": false,
    "collapsing": true,
    "autoplay": false,
    "items": [],
    "world_size": {"x": 1, "y": 1},
    "execution_speed": 1,
    "digging_speed": 1,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 1,
    "exclude_unlocks": ["watering", "fertilizer"],
    "starting_chunk": 0,
    "dlc_enabled": false
}
#SETUP
#CODE
while True:
	do_a_flip()
	pet_the_piggy()
harvest()
}}

---

[Cyklus for](docs/scripting/for.md)      [If](docs/scripting/if.md)      [Break](docs/scripting/break.md)      [Continue](docs/scripting/continue.md)<desktop>      [Externí editor](docs/external_editor.md)</desktop>
