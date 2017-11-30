---
title: "Correspondência padrão (F#)"
description: "Saiba como os padrões são usados em F # para comparar dados com estruturas lógicas, decompor dados em partes constituintes ou extrair informações de dados."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5562ee98-e2f1-4dcd-8e2f-16ae27baaade
ms.openlocfilehash: 7c7a3110a8f34c0c96c12d4584010a9ac4b485fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="pattern-matching"></a>Correspondência padrão

Os padrões são regras de transformação de dados de entrada. Eles são usados em toda a linguagem F # para comparar dados com uma estrutura lógica ou estruturas, decompor dados em partes constituintes ou extrair informações de dados de várias maneiras.


## <a name="remarks"></a>Comentários
Padrões são usados em muitas construções de linguagem, como o `match` expressão. Eles são usados quando você estiver processando os argumentos para funções na `let` associações, as expressões lambda e no manipulador de exceção associado a `try...with` expressão. Para obter mais informações, consulte [correspondência expressões](match-expressions.md), [associações let](functions/let-bindings.md), [expressões Lambda: A `fun` palavra-chave](functions/lambda-expressions-the-fun-keyword.md), e [exceções: A `try...with` Expressão](exception-handling/the-try-with-expression.md).

Por exemplo, o `match` expressão, o *padrão* é o que segue o símbolo de pipe.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Cada padrão atua como uma regra para transformar a entrada de algum modo. No `match` expressão, cada padrão é examinado por sua vez, para ver se os dados de entrada serão compatíveis com o padrão. Se uma correspondência for encontrada, a expressão resultante é executada. Se uma correspondência não for encontrada, a próxima regra padrão será testada. Opcional quando *condição* parte é explicada em [correspondência expressões](match-expressions.md).

Padrões suportados são mostrados na tabela a seguir. Em tempo de execução, a entrada é testada em relação a cada um dos seguintes padrões na ordem listada na tabela e padrões são aplicadas recursivamente, do primeiro ao último como aparecem no seu código e da esquerda para a direita para os padrões em cada linha.

|Nome|Descrição|Exemplo|
|----|-----------|-------|
|Padrão de constante|Qualquer numéricos, caractere ou cadeia de caracteres literal, uma constante de enumeração ou um identificador de literal definido|`1.0`, `"test"`, `30`, `Color.Red`|
|Padrão de identificador|Um valor de caso de uma união discriminada, um rótulo de exceção ou uma ocorrência do padrão ativo|`Some(x)`<br /><br />`Failure(msg)`|
|Padrão de variável|*identifier*|`a`|
|`as`padrão|*padrão de* como *identificador*|`(a, b) as tuple1`|
|OU padrão|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|E o padrão|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Padrão Cons|*identificador* :: *identificador da lista*|`h :: t`|
|Padrão de lista|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Padrão de matriz|[&#124; *pattern_1*;...; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Padrão entre parênteses|( *padrão* )|`( a )`|
|Padrão de tupla|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Padrão de registro|{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Padrão de curinga|_|`_`|
|Padrão junto com a anotação de tipo|*padrão de* : *tipo*|`a : int`|
|Padrão de teste de tipo|:? *tipo* [como *identificador* ]|`:? System.DateTime as dt`|
|Padrão nulo|nulo|`null`|

## <a name="constant-patterns"></a>Padrões de constantes
Constantes padrões são numéricos, caracteres e literais de cadeia de caracteres, constantes de enumeração (com o nome de tipo de enumeração incluído). Um `match` expressão que contém apenas os padrões constantes pode ser comparado a uma instrução case em outros idiomas. A entrada é comparada com o valor literal e o padrão corresponde se os valores são iguais. O tipo do literal deve ser compatível com o tipo da entrada.

O exemplo a seguir demonstra o uso de padrões de literais e também usa um padrão de variável e um padrão de OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Outro exemplo de um padrão de literal é um padrão com base em constantes de enumeração. Você deve especificar o nome do tipo de enumeração ao usar constantes de enumeração.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Padrões de identificador
Se o padrão é uma cadeia de caracteres que constitui um identificador válido, o formato do identificador determina como o padrão é correspondido. Se o identificador é maior do que um único caractere e começa com um caractere maiusculo, o compilador tenta fazer uma correspondência para o padrão de identificador. O identificador para esse padrão pode ser um valor marcado com o atributo Literal, um caso de união discriminado, um identificador de exceção ou um caso de padrão ativo. Se nenhum identificador correspondente for encontrado, a correspondência falhar e a próxima regra padrão, o padrão de variável é comparada com a entrada.

Padrões de união discriminadas podem ser simples denominado casos ou eles podem ter um valor ou uma tupla que contém vários valores. Se houver um valor, você deve especificar um identificador para o valor. No caso de uma tupla, você deve fornecer um padrão de tupla com um identificador para cada elemento da tupla ou um identificador com um nome de campo para uma ou mais chamado campos union. Consulte os exemplos de código nesta seção para obter exemplos.

O `option` tipo é uma união discriminada que tem dois casos, `Some` e `None`. Um caso (`Some`) tem um valor, mas o outro (`None`) é apenas um caso nomeado. Portanto, `Some` deve ter uma variável para o valor associado com o `Some` caso, mas `None` deve aparecer sozinho. No código a seguir, a variável `var1` recebe o valor é obtido por meio da correspondência para o `Some` caso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

No exemplo a seguir, o `PersonName` união discriminada contém uma mistura de cadeias de caracteres e caracteres que representam formas possíveis de nomes. Os casos de união discriminada são `FirstOnly`, `LastOnly`, e `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Para uniões discriminadas que têm campos nomeados, use o sinal de igual (=) para extrair o valor de um campo. Por exemplo, considere uma união discriminada com uma declaração semelhante ao seguinte.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Você pode usar os campos nomeados em uma expressão de correspondência de padrão da seguinte maneira.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

O uso do campo nomeado é opcional, portanto, no exemplo anterior, ambos `Circle(r)` e `Circle(radius = r)` têm o mesmo efeito.

Quando você especificar vários campos, use o ponto e vírgula (;) como separador.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Padrões ativos permitem definir a correspondência de padrão personalizado mais complexas. Para obter mais informações sobre padrões ativos, consulte [padrões ativos](active-patterns.md).

O caso em que o identificador é uma exceção é usado na correspondência de padrão de contexto de manipuladores de exceção. Para obter informações sobre correspondência de padrão de manipulação de exceção, consulte [exceções: A `try...with` expressão](exception-handling/the-try-with-expression.md).


## <a name="variable-patterns"></a>Padrões de variáveis
O padrão de variável atribui o valor sendo correspondido a um nome de variável, que estará disponível para uso na expressão à direita da execução de `->` símbolo. Um padrão de variável sozinho corresponde qualquer entrada, mas padrões variáveis geralmente aparecem em outros padrões, portanto Permitindo estruturas mais complexas, como tuplas e matrizes para ser decomposto em variáveis.

O exemplo a seguir demonstra um padrão de variável dentro de um padrão de tupla.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>como padrão
O `as` padrão é um padrão que tem um `as` cláusula anexada a ele. O `as` cláusula associa o valor correspondente a um nome que pode ser usado na expressão de execução de um `match` expressão, ou, no caso em que esse padrão é usado em um `let` de associação, o nome é adicionado como uma ligação com o escopo local.

O exemplo a seguir usa um `as` padrão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>OU padrão
O padrão ou é usado quando os dados de entrada podem corresponder a vários padrões, e você deseja executar o mesmo código como resultado. Os tipos de ambos os lados do padrão ou devem ser compatíveis.

O exemplo a seguir demonstra o padrão de OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>E o padrão
O padrão e requer que a entrada corresponder dois padrões. Os tipos de ambos os lados do padrão e devem ser compatíveis.

O exemplo a seguir é semelhante `detectZeroTuple` mostra o [padrão de tupla](https://msdn.microsoft.com/library/#tuple) seção mais adiante neste tópico, mas aqui ambos `var1` e `var2` são obtidos como valores usando o padrão e.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Contras padrão
O padrão de contras é usado para decompor uma lista para o primeiro elemento, o *head*e uma lista que contém os elementos restantes, o *final*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Padrão de lista
O padrão de lista permite que a lista ser decomposto em um número de elementos. O padrão de lista em si pode corresponder a apenas uma lista de um número específico de elementos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Padrão de matriz
O padrão de matriz é semelhante ao padrão de lista e pode ser usado para decompor as matrizes de um período específico.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Padrão entre parênteses
Parênteses podem ser agrupados em torno de padrões para alcançar a capacidade de associação desejada. No exemplo a seguir, os parênteses são usados para controlar a associação entre um padrão AND e um padrão de contras.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Padrão de tupla
O padrão de tupla corresponde a entrada na forma de tupla e permite que a tupla a ser decomposto em seus elementos constituintes usando variáveis para cada posição na tupla de correspondência de padrões.

O exemplo a seguir demonstra o padrão de tupla e também usa padrões literal, padrões de variáveis e o padrão de curinga.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Padrão de registro
O padrão de registro é usado para decompor registros para extrair os valores dos campos. O padrão não precisa fazer referência a todos os campos do registro. todos os campos omitidos apenas não participam de correspondência e não são extraídos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Padrão de curinga
O padrão de curinga é representado por um sublinhado (`_`) de caracteres e corresponde qualquer entrada, assim como o padrão de variável, exceto que a entrada é descartada, em vez de atribuído a uma variável. O padrão de curinga é geralmente usado em outros padrões como um espaço reservado para valores que não são necessários na expressão à direita do `->` símbolo. O padrão de curinga é usado frequentemente no final de uma lista de padrões para corresponder a nenhuma entrada não correspondente. O padrão de curinga é demonstrado em muitos exemplos de código neste tópico. Consulte o código anterior para obter um exemplo.


## <a name="patterns-that-have-type-annotations"></a>Padrões com anotações de tipo
Os padrões podem ter anotações de tipo. Eles se comportam como outras anotações de tipo e guia inferência como outras anotações de tipo. São necessários parênteses em torno de anotações de tipo em padrões. O código a seguir mostra um padrão que tem uma anotação de tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Padrão de teste de tipo
O padrão de teste de tipo é usado para corresponder à entrada em relação a um tipo. Se o tipo de entrada é uma correspondência (ou um tipo derivado de) o tipo especificado no padrão, a correspondência for bem-sucedida.

O exemplo a seguir demonstra o padrão de teste de tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Padrão nulo
O padrão de nulo corresponde o valor nulo que pode aparecer quando você estiver trabalhando com tipos que permitem valor nulo. Nulo padrões são usados ao interagir com código do .NET Framework. Por exemplo, o valor de retorno de uma API .NET pode ser a entrada para um `match` expressão. Você pode controlar o fluxo de programa com base em se o valor de retorno é nulo e também em outras características do valor retornado. Você pode usar o padrão de null para impedir que valores nulos sejam propagadas para o restante do seu programa.

O exemplo a seguir usa o padrão de null e o padrão de variável.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Consulte também
[Expressões Match](match-expressions.md)

[Padrões Ativos](active-patterns.md)

[Referência da Linguagem F#](index.md)
