[<- Arroz](docs/unlocks/rice.md) <right>[Blocos Coloridos ->](docs/unlocks/debug_place.md)
<right>[Pirâmides ->](docs/unlocks/pyramid.md)
---
# Bambu

O bambu é uma planta que cresce para cima. Seu drone vai precisar arrancar os frutos marrons dele regularmente para que ele continue crescendo. Podemos fazer isso com o comando `hover`, que acabou de ser desbloqueado.

O bambu precisa ser plantado em terra arada (`Grounds.Soil`), e plantá-lo custa arroz.

O código a seguir planta bambu e espera ele crescer até o primeiro fruto.
{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
move(East) # afaste-se para o bambu poder crescer
}}

## Frutos

O bambu cresce exatamente 1 bloco por segundo.

O bambu produz frutos a cada poucos blocos. Quando isso acontece, o bambu para de crescer e você precisa voar com o drone para dentro dele para destruir o fruto.

Para arrancar os frutos, primeiro use `hover` para chegar à altura certa. Depois, use `move` para entrar no fruto e arrancá-lo, e `move` de novo para se afastar e deixar o bambu continuar crescendo.

Você pode usar `measure()` no bambu para verificar em que altura o próximo fruto vai aparecer. `measure()` começa a contar em `0`, então `hover(measure())` leva o drone até a altura onde o fruto vai estar.

{{codeexample
{
"camera_position": {"x": -1, "y": 0, "z": 10},
"show_image": true,
"image_size": {"x": 800, "y": 500},
"show_code": true,
"show_inventory": true,
"show_output": false,
"collapsing": true,
"autoplay": false,
"items": [{"item": "rice", "n": 100}],
"world_size": {"x": 4, "y": 4},
"execution_speed": 2,
"action_ticks": 200,
"operation_ticks": 200,
"seed": 1,
"exclude_unlocks": ["watering", "fertilizer", "mushrooms", "coal"]
}
#SETUP
move(North)
move(East)
#CODE
till()
plant(Entities.Bamboo)
hover(measure()) # paire de modo que o drone fique ao lado do fruto

move(East) # afaste-se e espere ele crescer
for i in range(3):
    do_a_flip()

move(West) # arranque o fruto
move(East) # afaste-se de novo
}}

## Pairar

O comando `hover` recebe um argumento, a altura em que o drone deve pairar, que é um número de `0` a `18`. A altura padrão em que o drone paira é `1`. `hover` não consegue descer para dentro de entidades sólidas, então, se o drone já estiver acima de um bambu, você não consegue entrar nele executando `hover(0)`.

`hover` retorna `True` se o drone conseguiu pairar na altura indicada, e `False` caso contrário.

Além disso, existe o comando `get_hover`, que retorna a altura atual em que o drone está pairando.

Se você usar `dig`, `harvest` ou `plant` enquanto paira, o drone volta para a altura padrão (`1`).

Por fim, `get_pos_z()` não é afetado pela altura em que o drone paira. Ele sempre retorna a posição z do bloco abaixo do drone.

## Colhendo Bambu

Embora você possa usar `harvest()`, a forma recomendada de colher plantações de bambu é entrar em um bambu com o drone na altura `0` (`hover(0)`). Isso colhe a planta inteira de uma vez.

Se quiser colher o bambu sem destruí-lo, você pode usar `move` para entrar nele em qualquer altura, por exemplo `hover(3)`. Isso colhe todos os pedaços de bambu dessa altura para cima, mas mantém o bambu vivo. Um bambu colhido parcialmente dessa forma volta a produzir frutos, então você vai precisar arrancá-los de novo.

Em ambos os casos, sua produção é igual ao quadrado do número de pedaços de bambu destruídos, então, quanto mais alto o bambu, melhor a produção.

---

[Estatísticas](docs/stats.md)      [Loop For](docs/scripting/for.md)      [Variáveis](docs/scripting/variables.md)      [If](docs/scripting/if.md)      [Funções](docs/scripting/functions.md)      [Arroz](docs/unlocks/rice.md)

[harvest()](functions/harvest)      [plant()](functions/plant)      [move()](functions/move)      [till()](functions/till)      [measure()](functions/measure)
