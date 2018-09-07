---
title: Correspondência padrão (F#)
description: 'Saiba como os padrões são usados em F # para comparar dados com estruturas lógicas, decompor os dados em partes constituintes ou extrair informações de dados.'
ms.date: 05/16/2016
ms.openlocfilehash: 5ad3d3e1a78246afdfa2948fd0fb84fa04686d30
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44077178"
---
# <a name="pattern-matching"></a>Correspondência padrão

Os padrões são regras para transformar dados de entrada. Eles são usados em toda a linguagem F # para comparar dados com um ou mais estruturas lógicas, decompor os dados em partes constituintes ou extrair informações de dados de várias maneiras.

## <a name="remarks"></a>Comentários

Padrões são usados em muitas construções de linguagem, tais como o `match` expressão. Eles são usados quando você estiver processando argumentos para funções em `let` associações, expressões lambda e nos manipuladores de exceção associados com o `try...with` expressão. Para obter mais informações, consulte [expressões de correspondência](match-expressions.md), [associações let](functions/let-bindings.md), [expressões Lambda: A `fun` palavra-chave](functions/lambda-expressions-the-fun-keyword.md), e [exceções: A `try...with` Expressão](exception-handling/the-try-with-expression.md).

Por exemplo, nos `match` expressão, o *padrão* é o que segue o símbolo de pipe.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Cada padrão atua como uma regra de transformação de entrada de alguma maneira. No `match` expressão, cada padrão é examinado em turnos para verificar se os dados de entrada serão compatíveis com o padrão. Se uma correspondência for encontrada, a expressão resultante é executada. Se uma correspondência não for encontrada, a próxima regra padrão será testada. Opcional quando *condição* parte é explicada [expressões de correspondência](match-expressions.md).

Padrões suportados são mostrados na tabela a seguir. Em tempo de execução, a entrada é testada em relação a cada um dos seguintes padrões na ordem listada na tabela e padrões são aplicados recursivamente, do primeiro ao último como aparecem no seu código e da esquerda para a direita para os padrões em cada linha.

|Nome|Descrição|Exemplo|
|----|-----------|-------|
|Padrão de constante|Qualquer numérico, caractere ou cadeia de caracteres literal, uma constante de enumeração ou um identificador literal definido|`1.0`, `"test"`, `30`, `Color.Red`|
|Padrão de identificador|Um valor de caso de uma união discriminada, um rótulo de exceção ou um caso de padrão do Active Directory|`Some(x)`<br /><br />`Failure(msg)`|
|Padrão de variável|*identifier*|`a`|
|`as` Padrão|*padrão de* como *identificador*|`(a, b) as tuple1`|
|OU padrão|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|E o padrão|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Padrão constante|*identificador* :: *identificador da lista*|`h :: t`|
|Padrão de lista|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Padrão de matriz|[&#124; *pattern_1*;..; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Padrão posto entre parênteses|( *padrão* )|`( a )`|
|Padrão de tupla|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Padrão de registro|{ *identifier1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Padrão de curinga|_|`_`|
|Padrão juntamente com a anotação de tipo|*padrão de* : *tipo*|`a : int`|
|Padrão de teste de tipo|:? *tipo de* [como *identificador* ]|`:? System.DateTime as dt`|
|Padrão zero|nulo|`null`|

## <a name="constant-patterns"></a>Padrões constante

Os padrões constantes são numéricos, caracteres e literais de cadeia de caracteres, constantes de enumeração (com o nome de tipo de enumeração incluído). Um `match` expressão que possui apenas constantes padrão pode ser comparado a uma instrução case em outras linguagens. A entrada é comparada com o valor literal e o padrão corresponde se os valores forem iguais. O tipo do literal deve ser compatível com o tipo da entrada.

O exemplo a seguir demonstra o uso de padrões de literal e também usa um padrão de variável e um padrão OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Outro exemplo de um padrão literal é um padrão baseado em constantes de enumeração. Você deve especificar o nome do tipo de enumeração quando usa constantes de enumeração.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Padrões do identificador

Se o padrão é uma cadeia de caracteres que forme um identificador válido, o formato do identificador determina como o padrão é correspondido. Se o identificador tem mais de um único caractere e começa com um caractere maiusculo, o compilador tentará fazer uma correspondência com o padrão do identificador. O identificador para esse padrão pode ser um valor marcado com o atributo Literal, um caso união discriminado, um identificador de exceção ou um caso de padrão do Active Directory. Se nenhum identificador correspondente for encontrado, a correspondência falhará e a próxima regra padrão, o padrão de variável é comparada à entrada.

Padrões de união discriminados podem ser casos nomeados simples ou eles podem ter um valor ou uma tupla que contém vários valores. Se houver um valor, você deve especificar um identificador para o valor. No caso de uma tupla, você deve fornecer um padrão de tupla com um identificador para cada elemento da tupla ou um identificador com um nome de campo para um ou mais campos nomeados de união. Consulte os exemplos nesta seção para obter exemplos de código.

O `option` o tipo é uma união discriminada que tem dois casos, `Some` e `None`. Um caso (`Some`) tem um valor, mas o outro (`None`) é apenas um caso nomeado. Portanto, `Some` precisa ter uma variável para o valor associado a `Some` caso, mas `None` deve aparecer sozinho. No código a seguir, a variável `var1` recebe o valor obtido pela correspondência para o `Some` caso.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

No exemplo a seguir, o `PersonName` união discriminada contém uma mistura de cadeias de caracteres e caracteres que representam possíveis formas de nomes. São os casos da união discriminada `FirstOnly`, `LastOnly`, e `FirstLast`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Para as uniões discriminadas com campos nomeados, use o sinal de igual (=) para extrair o valor de um campo nomeado. Por exemplo, considere uma união discriminada com uma declaração semelhante ao seguinte.

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

Quando você especifica vários campos, use o ponto e vírgula (;) como um separador.

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Padrões ativos permitem que você defina a correspondência de padrão personalizado mais complexa. Para obter mais informações sobre padrões ativos, consulte [padrões ativos](active-patterns.md).

O caso em que o identificador é uma exceção é usado na correspondência de padrões no contexto de manipuladores de exceção. Para obter informações sobre correspondência de padrões no tratamento de exceções, consulte [exceções: A `try...with` expressão](exception-handling/the-try-with-expression.md).

## <a name="variable-patterns"></a>Padrões variáveis

O padrão de variável atribui o valor que está sendo correspondido para um nome de variável, em seguida, está disponível para uso na expressão de execução à direita do `->` símbolo. Um padrão variável sozinho corresponde a qualquer entrada, mas padrões variáveis geralmente aparecem dentro de outros padrões, portanto, ativando estruturas mais complexas, como tuples e matrizes a serem decompostos em variáveis.

O exemplo a seguir demonstra um padrão variável dentro de um padrão de tupla.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>como padrão

O `as` padrão é um padrão que tem um `as` cláusula anexada a ele. O `as` cláusula associa o valor correspondente a um nome que pode ser usado na expressão de execução de um `match` expressão, ou, no caso em que esse padrão é usado em um `let` de associação, o nome é adicionado como uma associação para o escopo local.

O exemplo a seguir usa um `as` padrão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>OU padrão

O padrão OR é usado quando os dados de entrada podem corresponder a vários padrões, e você deseja executar o mesmo código como resultado. Os tipos de ambos os lados do padrão OR devem ser compatíveis.

O exemplo a seguir demonstra o padrão OR.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>E o padrão

O padrão AND requer que a entrada corresponda a dois padrões. Os tipos de ambos os lados do padrão AND devem ser compatíveis.

O exemplo a seguir é semelhante `detectZeroTuple` mostra a [padrão de tupla](https://msdn.microsoft.com/library/#tuple) seção mais adiante neste tópico, mas aqui `var1` e `var2` são obtidos como valores usando o padrão AND.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Padrão constante

O padrão cons é usado para decompor uma lista no primeiro elemento, o *head*e uma lista que contém os elementos restantes, o *tail*.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Padrão de lista

O padrão de lista permite que as listas sejam decompostas em um número de elementos. O padrão de lista pode corresponder apenas às listas de um número específico de elementos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Padrão de matriz

O padrão de matriz lembra o padrão de lista e pode ser usado para decompor matrizes de um período específico.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Padrão posto entre parênteses

Parênteses podem ser agrupados em torno dos padrões para obter a associatividade desejada. No exemplo a seguir, os parênteses são usados para controlar a associatividade entre padrão e e um padrão de constante.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Padrão de tupla

O padrão de tupla corresponde à entrada no formulário de tupla e permite que a tupla seja decomposta em seus elementos constituintes usando variáveis para cada posição na tupla de correspondência de padrão.

O exemplo a seguir demonstra o padrão de tupla e também usa padrões de literal, padrões de variável e o padrão de curinga.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Padrão de registro

O padrão de registro é usado para decompor registros para extrair os valores dos campos. O padrão não precisa fazer referência a todos os campos do registro; apenas, os campos omitidos não participam da correspondência e não são extraídos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Padrão de curinga

O padrão de curinga é representado por um sublinhado (`_`) de caracteres e corresponde a qualquer entrada, assim como o padrão de variável, exceto que a entrada é descartada, em vez de atribuída a uma variável. O padrão de curinga geralmente é usado em outros padrões como um espaço reservado para valores que não são necessários na expressão à direita do `->` símbolo. O padrão de curinga também frequentemente é usado no final de uma lista de padrões para corresponder a qualquer entrada sem correspondência. O padrão de curinga é demonstrado em muitos exemplos de código neste tópico. Consulte o código anterior para obter um exemplo.

## <a name="patterns-that-have-type-annotations"></a>Padrões que possuem anotações de tipo

Os padrões podem ter anotações de tipo. Eles se comportam como outras anotações de tipo e Inferência de tipos, como outras anotações de tipo de guia. Os parênteses são necessários em torno de anotações de tipo em padrões. O código a seguir mostra um padrão que tem uma anotação de tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Padrão de teste de tipo

O padrão de teste de tipo é usado para corresponder à entrada com relação a um tipo. Se o tipo de entrada é uma correspondência (ou um tipo derivado de) o tipo especificado no padrão, a correspondência será bem-sucedida.

O exemplo a seguir demonstra o padrão de teste de tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a>Padrão zero

O padrão nulo corresponde ao valor nulo que pode aparecer quando você estiver trabalhando com tipos que permitem que um valor nulo. Padrões nulos são frequentemente usados ao interoperar com código do .NET Framework. Por exemplo, o valor retornado de uma API do .NET pode ser a entrada para um `match` expressão. Você pode controlar o fluxo do programa com base em se o valor de retorno é nulo e também em outras características do valor retornado. Você pode usar o padrão de null para impedir que valores nulos propaguem para o restante do seu programa.

O exemplo a seguir usa o padrão de null e o padrão de variável.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Consulte também

- [Expressões Match](match-expressions.md)
- [Padrões Ativos](active-patterns.md)
- [Referência da Linguagem F#](index.md)
