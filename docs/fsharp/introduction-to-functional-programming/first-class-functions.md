---
title: Funções de primeira classe
description: 'Saiba mais sobre as funções de primeira classe e como elas são importantes para a programação funcional em F #.'
ms.date: 10/29/2018
ms.openlocfilehash: 1dc8eae1655187282f05bf4e9501ecc8a17deba8
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810905"
---
# <a name="first-class-functions"></a>Funções de primeira classe

Uma característica de definição de linguagens de programação funcional é a elevação de funções para o status de primeira classe. Você deve ser capaz de fazer com uma função o que você pode fazer com valores dos outros tipos internos e ser capaz de fazer isso com um grau de esforço comparável.

As medidas típicas de status de primeira classe incluem o seguinte:

- Você pode associar funções a identificadores? Ou seja, você pode dar a eles nomes?

- É possível armazenar funções em estruturas de dados, como em uma lista?

- Você pode passar uma função como um argumento em uma chamada de função?

- Você pode retornar uma função de uma chamada de função?

As duas últimas medidas definem o que é conhecido como *operações de ordem superior* ou *funções de ordem superior*. As funções de ordem superior aceitam funções como argumentos e retornam funções como o valor de chamadas de função. Essas operações dão suporte a tais fundamentos de programação funcional como funções de mapeamento e composição de funções.

## <a name="give-the-value-a-name"></a>Dê um nome ao valor

Se uma função for um valor de primeira classe, você deverá ser capaz de nomeá-la, assim como você pode nomear inteiros, cadeias de caracteres e outros tipos internos. Isso é referenciado na literatura de programação funcional como associação de um identificador a um valor. F # usa [ `let` associações](../language-reference/functions/let-bindings.md) para associar nomes a valores: `let <identifier> = <value>` . O código a seguir mostra dois exemplos.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

Você pode nomear uma função com a mesma facilidade. O exemplo a seguir define uma função chamada `squareIt` ligando o identificador `squareIt` à [expressão lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n` . `squareIt`A função tem um parâmetro, `n` e retorna o quadrado desse parâmetro.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

O F # fornece a seguinte sintaxe mais concisa para obter o mesmo resultado com menos digitação.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

Os exemplos a seguir usam principalmente o primeiro estilo, `let <function-name> = <lambda-expression>` , para enfatizar as semelhanças entre a declaração de funções e a declaração de outros tipos de valores. No entanto, todas as funções nomeadas também podem ser escritas com a sintaxe concisa. Alguns dos exemplos são escritos de ambas as maneiras.

## <a name="store-the-value-in-a-data-structure"></a>Armazenar o valor em uma estrutura de dados

Um valor de primeira classe pode ser armazenado em uma estrutura de dados. O código a seguir mostra exemplos que armazenam valores em listas e em tuplas.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

Para verificar se um nome de função armazenado em uma tupla, na verdade, é avaliado como uma função, o exemplo a seguir usa os `fst` `snd` operadores e para extrair o primeiro e o segundo elementos da tupla `funAndArgTuple` . O primeiro elemento na tupla é `squareIt` e o segundo elemento é `num` . `num`O identificador está associado em um exemplo anterior ao inteiro 10, um argumento válido para a `squareIt` função. A segunda expressão aplica o primeiro elemento na tupla ao segundo elemento na tupla: `squareIt num` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

Da mesma forma, assim como o identificador `num` e o inteiro 10 podem ser usados de maneira intercambiável, portanto, pode identificador `squareIt` e expressão lambda `fun n -> n * n` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>Passar o valor como um argumento

Se um valor tiver o status de primeira classe em um idioma, você poderá passá-lo como um argumento para uma função. Por exemplo, é comum passar inteiros e cadeias de caracteres como argumentos. O código a seguir mostra inteiros e cadeias de caracteres passados como argumentos em F #.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

Se as funções tiverem o status de primeira classe, você deverá ser capaz de passá-las como argumentos da mesma maneira. Lembre-se de que essa é a primeira característica das funções de ordem superior.

No exemplo a seguir, a função `applyIt` tem dois parâmetros `op` e `arg` . Se você enviar em uma função que tenha um parâmetro para `op` e um argumento apropriado para a função para `arg` , a função retornará o resultado da aplicação `op` de `arg` . No exemplo a seguir, o argumento de função e o argumento de inteiro são enviados da mesma maneira, usando seus nomes.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

A capacidade de enviar uma função como um argumento para outra função baseia-se em abstrações comuns em linguagens de programação funcionais, como operações de mapeamento ou de filtro. Uma operação de mapa, por exemplo, é uma função de ordem superior que captura a computação compartilhada por funções que passam por uma lista, fazem algo para cada elemento e, em seguida, retornam uma lista dos resultados. Você pode desejar incrementar cada elemento em uma lista de inteiros ou para quadradoar cada elemento ou para alterar cada elemento em uma lista de cadeias de caracteres para letras maiúsculas. A parte propensa a erros da computação é o processo recursivo que percorre a lista e cria uma lista dos resultados a serem retornados. Essa parte é capturada na função de mapeamento. Tudo o que você precisa escrever para um aplicativo específico é a função que você deseja aplicar a cada elemento de lista individualmente (adicionando, elevando, alterando maiúsculas e minúsculas). Essa função é enviada como um argumento para a função de mapeamento, assim como `squareIt` é enviada para `applyIt` no exemplo anterior.

O F # fornece métodos de mapa para a maioria dos tipos de coleção, incluindo [listas](../language-reference/lists.md), [matrizes](../language-reference/arrays.md)e [sequências](../language-reference/sequences.md). Os exemplos a seguir usam listas. A sintaxe é `List.map <the function> <the list>`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

Para obter mais informações, consulte [listas](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Retornar o valor de uma chamada de função

Por fim, se uma função tiver o status de primeira classe em um idioma, você deverá ser capaz de retorná-la como o valor de uma chamada de função, assim como retorna outros tipos, como inteiros e cadeias de caracteres.

As chamadas de função a seguir retornam inteiros e as exibem.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

A chamada de função a seguir retorna uma cadeia de caracteres.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

A chamada de função a seguir, declarada embutida, retorna um valor booliano. O valor exibido é `True` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

A capacidade de retornar uma função como o valor de uma chamada de função é a segunda característica de funções de ordem superior. No exemplo a seguir, `checkFor` é definido como uma função que usa um argumento, `item` e retorna uma nova função como seu valor. A função retornada usa uma lista como seu argumento, `lst` e procura `item` em `lst` . Se `item` estiver presente, a função retornará `true` . Se `item` não estiver presente, a função retornará `false` . Como na seção anterior, o código a seguir usa uma função de lista fornecida, [list. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists), para pesquisar a lista.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

O código a seguir usa `checkFor` para criar uma nova função que usa um argumento, uma lista e pesquisa 7 na lista.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

O exemplo a seguir usa o status de primeira classe de funções em F # para declarar uma função, `compose` , que retorna uma composição de dois argumentos de função.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> Para obter uma versão ainda mais curta, consulte a seção a seguir, "na forma curried Functions".

O código a seguir envia duas funções como argumentos para `compose` , que usam um único argumento do mesmo tipo. O valor de retorno é uma nova função que é uma composição dos dois argumentos de função.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> O F # fornece dois operadores `<<` e `>>` , que compõem funções. Por exemplo, `let squareAndDouble2 = doubleIt << squareIt` é equivalente a `let squareAndDouble = compose doubleIt squareIt` no exemplo anterior.

O exemplo a seguir de retornar uma função como o valor de uma chamada de função cria um jogo de adivinhação simples. Para criar um jogo, chame `makeGame` com o valor que você deseja que alguém Adivinhe envie `target` . O valor de retorno da função `makeGame` é uma função que usa um argumento (a estimativa) e informa se a estimativa está correta.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

O código a seguir chama `makeGame` , enviando o valor `7` para `target` . `playGame`O identificador está associado à expressão lambda retornada. Portanto, `playGame` é uma função que usa como um valor de um argumento para `guess` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>Funções na forma curried

Muitos dos exemplos na seção anterior podem ser escritos de forma mais concisa aproveitando as *currying* implícitas em declarações de função F #. Currying é um processo que transforma uma função que tem mais de um parâmetro em uma série de funções inseridas, cada uma com um único parâmetro. Em F #, as funções que têm mais de um parâmetro são inerentemente na forma curried. Por exemplo, `compose` da seção anterior pode ser escrito conforme mostrado no estilo conciso a seguir, com três parâmetros.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

No entanto, o resultado é uma função de um parâmetro que retorna uma função de um parâmetro que, por sua vez, retorna outra função de um parâmetro, como mostrado em `compose4curried` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

Você pode acessar essa função de várias maneiras. Cada um dos exemplos a seguir retorna e exibe 18. Você pode substituir `compose4` por `compose4curried` em qualquer um dos exemplos.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

Para verificar se a função ainda funciona como antes, tente os casos de teste originais novamente.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> Você pode restringir currying por meio de parâmetros delimitadores em tuplas. Para obter mais informações, consulte "padrões de parâmetro" em [parâmetros e argumentos](../language-reference/parameters-and-arguments.md).

O exemplo a seguir usa o currying implícito para gravar uma versão mais curta do `makeGame` . Os detalhes de como `makeGame` construções e Devoluções da `game` função são menos explícitos nesse formato, mas você pode verificar usando os casos de teste originais que o resultado é o mesmo.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

Para obter mais informações sobre currying, consulte "aplicativo parcial de argumentos" em [funções](../language-reference/functions/index.md).

## <a name="identifier-and-function-definition-are-interchangeable"></a>Identificador e definição de função são intercambiáveis

O nome da variável `num` nos exemplos anteriores é avaliado como o inteiro 10, e não é surpresa que o local `num` seja válido, 10 também é válido. O mesmo vale para identificadores de função e seus valores: em qualquer lugar, o nome da função pode ser usado, a expressão lambda à qual ele está associado pode ser usada.

O exemplo a seguir define uma `Boolean` função chamada `isNegative` e, em seguida, usa o nome da função e a definição da função de forma intercambiável. Os próximos três exemplos retornam e exibem `False` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

Para levá-lo um passo adiante, substitua o valor que `applyIt` está associado a para `applyIt` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>Funções são valores de primeira classe em F\#

Os exemplos nas seções anteriores demonstram que as funções em F # atendem aos critérios para serem valores de primeira classe em F #:

- Você pode associar um identificador a uma definição de função.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- Você pode armazenar uma função em uma estrutura de dados.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- Você pode passar uma função como um argumento.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- Você pode retornar uma função como o valor de uma chamada de função.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

Para obter mais informações sobre F #, consulte a [referência de linguagem f #](../language-reference/index.md).

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

O código a seguir contém todos os exemplos neste tópico.

### <a name="code"></a>Código

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>Confira também

- [Listas](../language-reference/lists.md)
- [Tuplas](../language-reference/tuples.md)
- [Funções](../language-reference/functions/index.md)
- [`let` Associações](../language-reference/functions/let-bindings.md)
- [Expressões lambda: a `fun` palavra-chave](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
