---
title: Funções como valores de primeira classe (F#)
description: 'Saiba como as funções são elevadas para o status de primeira classe em F # linguagem de programação.'
ms.date: 05/16/2016
ms.openlocfilehash: cccff5fcf9de150da26422f80cae032ddf21014c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566659"
---
# <a name="functions-as-first-class-values"></a>Funções como valores de primeira classe

Uma característica de definição de linguagens de programação funcionais é a elevação de funções para o status de primeira classe. Você deve ser capaz de fazer com uma função que você pode fazer com os valores dos outros tipos internos e ser capaz de fazer isso com um nível semelhante de esforço.

Medidas típicas de primeira classe status incluem o seguinte:

- Você pode associar funções aos identificadores? Ou seja, pode dá-los nomes?

- Você pode armazenar funções nas estruturas de dados, como em uma lista?

- Você pode passar uma função como um argumento em uma chamada de função?

- Você pode retornar uma função de uma chamada de função?

As últimas duas medidas que definem o que é conhecido como *operações de ordem superior* ou *funções de ordem superior*. Funções de ordem superior aceitam funções como argumentos e retornam funções como o valor de chamadas de função. Essas operações oferecem suporte a esses fundamentos da programação funcional como mapeamento de funções e a composição de funções.


## <a name="give-the-value-a-name"></a>Nomeie o valor

Se uma função é um valor de primeira classe, você deve ser capaz de nome, assim como você pode nomear inteiros, cadeias de caracteres e outros tipos internos. Isso é conhecido na literatura de programação funcional como um identificador de associação para um valor. F # usa [ `let` associações](../language-reference/functions/let-bindings.md) para associar nomes de valores: `let <identifier> = <value>`. O código a seguir mostra dois exemplos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

Você pode nomear uma função com a maior facilidade. O exemplo a seguir define uma função chamada `squareIt` associando o identificador `squareIt` para o [expressão lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`. Função `squareIt` tem um parâmetro, `n`, e retorna o quadrado do parâmetro.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F # fornece a seguinte sintaxe mais conciso para alcançar o mesmo resultado com menos digitação.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

Os exemplos a seguir geralmente usam o estilo primeiro, `let <function-name> = <lambda-expression>`, para enfatizar as semelhanças entre a declaração de funções e a declaração de outros tipos de valores. No entanto, todas as funções nomeadas também podem ser escritas com a sintaxe concisa. Alguns exemplos são gravados em ambos os sentidos.


## <a name="store-the-value-in-a-data-structure"></a>Armazene o valor em uma estrutura de dados

Um valor de primeira classe pode ser armazenado em uma estrutura de dados. O código a seguir mostra exemplos que armazenam valores em listas em tuplas.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

Para verificar se um nome de função armazenado em uma tupla na verdade avaliado como uma função, o exemplo a seguir usa o `fst` e `snd` operadores para extrair os elementos de primeiro e segundo de tupla `funAndArgTuple`. O primeiro elemento na tupla é `squareIt` e o segundo elemento é `num`. Identificador `num` está associada a um exemplo anterior para o inteiro 10, um argumento válido para o `squareIt` função. A segunda expressão aplica-se o primeiro elemento na tupla para o segundo elemento na tupla: `squareIt num`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

Da mesma forma, apenas como identificador `num` e inteiro 10 pode ser usados alternadamente, pode ser identificador `squareIt` e uma expressão lambda `fun n -> n * n`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a>Passe o valor como um argumento

Se um valor tiver um status de primeira classe em um idioma, você pode passá-lo como um argumento para uma função. Por exemplo, é comum para transmitir números inteiros e cadeias de caracteres como argumentos. O código a seguir mostra os números inteiros e cadeias de caracteres transmitidas como argumentos em F #.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

Se as funções que o status de primeira classe, você deve ser capaz para passá-las como argumentos, da mesma maneira. Lembre-se de que esta é a primeira característica de funções de ordem superior.

No exemplo a seguir, a função `applyIt` tem dois parâmetros, `op` e `arg`. Se você enviar em uma função que tem um parâmetro para `op` e um argumento apropriado para a função `arg`, a função retorna o resultado da aplicação `op` para `arg`. No exemplo a seguir, o argumento da função e o argumento inteiro são enviados da mesma forma, usando seus nomes.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

A capacidade de enviar uma função como um argumento para outra função subjacente abstrações comuns em linguagens de programação funcionais, como operações de mapa ou filtro. Uma operação de mapa, por exemplo, é uma função de ordem superior que captura a computação compartilhada por funções que percorrer uma lista, fazer alguma coisa para cada elemento e, em seguida, retornam uma lista dos resultados. Você pode deseja incrementar a cada elemento em uma lista de números inteiros, ou quadrado cada elemento ou alterar cada elemento em uma lista de cadeias de caracteres para maiusculas. A parte propensas a erros de computação é o processo de recursiva que percorre a lista e cria uma lista de resultados para retornar. Essa parte é capturada na função de mapeamento. Você precisa gravar para um determinado aplicativo é a função que você deseja aplicar a cada elemento da lista individualmente (Adicionar, elevar, alterando caso). Que função será enviada como um argumento para a função de mapeamento, assim como `squareIt` é enviada para `applyIt` no exemplo anterior.

F # fornece métodos de mapa para a maioria dos tipos de coleção, incluindo [lista](../language-reference/lists.md), [matrizes](../language-reference/arrays.md), e [sequências](../language-reference/sequences.md). Os exemplos seguintes usam listas. A sintaxe é `List.map <the function> <the list>`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

Para obter mais informações, consulte [lista](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>O valor de retorno de uma chamada de função

Por fim, se uma função tiver o status de primeira classe em um idioma, você deve ser capaz para retorná-lo como o valor de uma chamada de função, assim como retornam outros tipos, como números inteiros e cadeias de caracteres.

As chamadas de função a seguir retornam números inteiros e exibem-los.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

A chamada de função a seguir retorna uma cadeia de caracteres.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

A chamada de função a seguir, declarada em linha, retorna um valor booliano. O valor exibido é `True`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

A capacidade de retornar de uma função como o valor de uma chamada de função é a segunda característica de funções de ordem superior. No exemplo a seguir, `checkFor` está definido para ser uma função que usa um argumento, `item`e retorna uma nova função como seu valor. A função retornada usa uma lista como seu argumento, `lst`e procura por `item` em `lst`. Se `item` estiver presente, a função retornará `true`. Se `item` não estiver presente, a função retornará `false`. Como na seção anterior, o código a seguir usa uma função de lista fornecida, [EXISTS](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), para a lista de pesquisa.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

O código a seguir usa `checkFor` para criar uma nova função que usa um argumento, uma lista e procura 7 na lista.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

O exemplo a seguir usa o status de primeira classe das funções em F # para declarar uma função, `compose`, que retorna uma composição dos dois argumentos de função.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
Para obter uma versão ainda mais curta, consulte a seção a seguir, "Curried funções".


O código a seguir envia duas funções como argumentos para `compose`, ambos do que utilizam um argumento único do mesmo tipo. O valor de retorno é uma nova função que é uma composição dos argumentos da função de dois.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
F # fornece dois operadores, `<<` e `>>`, que compõem a funções. Por exemplo, `let squareAndDouble2 = doubleIt << squareIt` é equivalente a `let squareAndDouble = compose doubleIt squareIt` no exemplo anterior.

O exemplo de retorno de uma função como o valor de uma chamada de função a seguir cria um simples de adivinhação de jogo. Para criar um jogo, chame `makeGame` com o valor que você deseja que alguém adivinhar enviada para `target`. O valor de retorno da função `makeGame` é uma função que usa um argumento (a suposição) e informa se a previsão está correta.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

O código a seguir chama `makeGame`, enviar o valor `7` para `target`. Identificador `playGame` está associada à expressão lambda retornado. Portanto, `playGame` é uma função que usa um valor como um argumento para `guess`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a>Funções na forma curried

Muitos dos exemplos na seção anterior podem ser escritos mais maneira concisa, aproveitando o implícita *currying* nas declarações de função em F #. Currying é um processo que transforma uma função que tem mais de um parâmetro em uma série de funções internas, cada qual com um único parâmetro. Em F #, funções que têm mais de um parâmetro são inerentemente na forma curried. Por exemplo, `compose` da seção anterior pode ser escrito como mostrado no seguinte estilo conciso, com três parâmetros.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

No entanto, o resultado é uma função de um parâmetro que retorna uma função de um parâmetro que por sua vez retorna outra função de um parâmetro, conforme mostrado no `compose4curried`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

Você pode acessar essa função de várias maneiras. Cada um dos exemplos a seguir retorna e exibe a 18. Você pode substituir `compose4` com `compose4curried` em qualquer um dos exemplos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

Para verificar se a função ainda funciona como antes, tente novamente os casos de teste originais.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
Você pode restringir currying colocando parâmetros em tuplas. Para obter mais informações, consulte "Padrões de parâmetro" [parâmetros e argumentos](../language-reference/parameters-and-arguments.md).

O exemplo a seguir usa currying implícita para gravar uma versão reduzida da `makeGame`. Os detalhes de como `makeGame` constrói e retorna o `game` função são menos explícitas neste formato, mas você pode verificar usando os casos de teste originais que o resultado é o mesmo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

Para obter mais informações sobre currying, consulte o "Aplicativo parcial de argumentos" [funções](../language-reference/functions/index.md).


## <a name="identifier-and-function-definition-are-interchangeable"></a>Identificador e uma definição de função são intercambiáveis
O nome da variável `num` no anterior exemplos é avaliada para o inteiro 10 e não é surpresa que foram `num` é válido, 10 também é válido. O mesmo é verdadeiro de identificadores de função e seus valores: em qualquer lugar do nome da função pode ser usado, a expressão lambda ao qual ele está vinculado pode ser usada.

O exemplo a seguir define uma `Boolean` função chamada `isNegative`e usa o nome da função e a definição da função de maneira intercambiável. Os três exemplos todos retornar e exibir `False`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

Para ir um pouco mais, o valor de substituição que `applyIt` é vinculado ao `applyIt`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>Funções são valores de primeira classe em F # #

Os exemplos nas seções anteriores demonstram que funções em F # atendem aos critérios para valores de primeira classe em F #:

- Você pode associar um identificador para uma definição de função.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- Você pode armazenar uma função em uma estrutura de dados.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- Você pode passar uma função como um argumento.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- Você pode retornar uma função como o valor de uma chamada de função.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Para obter mais informações sobre F #, consulte o [referência da linguagem F #](../language-reference/index.md).

## <a name="example"></a>Exemplo

### <a name="description"></a>Descrição

O código a seguir contém todos os exemplos neste tópico.

### <a name="code"></a>Código

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a>Consulte também

[Listas](../language-reference/lists.md)

[Tuplas](../language-reference/tuples.md)

[Funções](../language-reference/functions/index.md)

[`let` Associações](../language-reference/functions/let-bindings.md)

[Expressões lambda: A `fun` palavra-chave](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
