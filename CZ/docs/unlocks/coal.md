[<- Těžba](docs/unlocks/mining.md) <right>[Železo ->](docs/unlocks/iron.md)
<right>[Skok ->](docs/unlocks/jump.md)
---
# Uhlí

Pod zemí se skrývají různé rudy a čekají, až je najdeš a vykopeš. Když se prokopeš povrchem do `Grounds.Dirt`, první rudou, kterou najdeš, je uhlí.

Jeho žíly tvoří vodorovné vrstvy o tloušťce 1 bloku, které musíš najít náhodou při kopání hlínou. Bloky uhlí ve vrstvě leží většinou přímo vedle sebe, některé ale mohou být spojené jen úhlopříčně.

K těžbě uhlí nemusíš dělat nic zvláštního, stačí provést `dig()`, když je dron přímo nad blokem `Grounds.Coal`. Pomocí `get_ground_type()` zjistíš, co je pod dronem, a pomocí `get_ground_type(direction)` zkontroluješ čtyři sousední bloky.

Uhlí dostaneš jen za bloky uhlí, do kterých přímo kopneš, ne za bloky, které se kolem dronu zřítí. Pamatuj na to, až budeš vymýšlet, jak uhlí těžit, abys vytěžil co nejvíc bloků uhlí a co nejméně jich ztratil při závalech.

Uhelné doly rostou úměrně velikosti farmy, takže zvaž další odemykání [Rozšíření](unlocks/expand), abys zvětšil množství uhlí, které můžeš vytěžit.

Následující program je dobrý začátek pro hledání uhlí. Kope dolů, dokud nenajde vrstvu uhlí, a pak kope na východ a na západ v naději, že najde další uhlí.

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
    "execution_speed": 4,
    "digging_speed": 2,
    "action_ticks": 200,
    "operation_ticks": 200,
    "seed": 2
}
#SETUP
move(North)
move(East)
move(East)
#CODE
while get_ground_type() != Grounds.Coal:
    dig()
do_a_flip()
dig()
move(East)
dig()
move(West)
move(West)
dig()
}}

Jednoduchá strategie, hlavně u menších farem, je vykopat všechny bloky v hloubce, kde jsi našel blok uhlí. Abys byl efektivnější, můžeš si pomocí `get_ground_type(direction)` zapamatovat, kde jsi viděl bloky uhlí, a neztrácet čas pohybem nad bloky hlíny. Dej si přitom zvlášť pozor, abys nepřehlédl úhlopříčná spojení, která mineš, když se budeš pohybovat jen nad bloky uhlí.

---

[Statistiky](docs/stats.md)      [Těžba](docs/unlocks/mining.md)      [Podzemní senzory](docs/unlocks/underground_senses.md)

[move()](functions/move)      [get_ground_type()](functions/get_ground_type)      [dig()](functions/dig)
