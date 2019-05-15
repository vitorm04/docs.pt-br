---
title: Uniões discriminadas
description: Saiba como usar F# uniões discriminadas.
ms.date: 05/16/2016
ms.openlocfilehash: 27fb9205f3f216adc435483fd1dcc839a6e13e03
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557968"
---
# <a name="discriminated-unions"></a>Uniões discriminadas

As uniões discriminadas fornecem suporte para valores que podem ser um dos vários casos nomeados, possivelmente cada um com tipos e valores diferentes. As uniões discriminadas são úteis para dados heterogêneos; dados que podem ter casos especiais, incluindo válido e casos de erro. dados que variam em tipo de uma instância para outro; e como uma alternativa para hierarquias de objetos pequenos. Além disso, discriminadas recursivas uniões são usadas para representar estruturas de dados de árvore.

## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Comentários

As uniões discriminadas são semelhantes aos tipos de união em outros idiomas, mas há diferenças. Como com um tipo de união no C++ ou um tipo variante em Visual Basic, os dados armazenados no valor não é fixo; ele pode ser uma das várias opções diferentes. Ao contrário de uniões em outras linguagens, no entanto, cada uma das opções possíveis recebe um *identificador de caso*. Os identificadores de caso são nomes para os vários tipos possíveis de valores que podem ser objetos desse tipo; os valores são opcionais. Se os valores não estiverem presentes, o caso é equivalente a um caso de enumeração. Se valores estiverem presentes, cada valor pode ser um único valor de um tipo especificado ou um tuple que agregue vários campos dos tipos iguais ou diferentes. Você pode dar a um campo individual um nome, mas o nome é opcional, mesmo se outros campos no mesmo caso forem nomeados.

Padrões de acessibilidade para uniões discriminadas para `public`.

Por exemplo, considere a seguinte declaração de um tipo de forma.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

O código anterior declara uma união discriminada Shape, que pode ter valores de qualquer um dos três casos: Rectangle, Circle e Prism. Cada caso tem um conjunto diferente de campos. O caso Rectangle tem dois nomeados de campos, ambos do tipo `float`, que têm os nomes width e length. O caso de círculo tem apenas um campo nomeado, raio. O caso Prism têm três campos, duas das quais (largura e altura) são campos nomeadas. Campos sem nome são chamados de campos anônimos.

Você constrói objetos fornecendo valores para os campos nomeados e anônimos de acordo com os exemplos a seguir.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Este código mostra que você pode usar os campos nomeados na inicialização, ou você pode confiar na ordem dos campos na declaração e apenas por sua vez, fornecer os valores para cada campo. A chamada de construtor para `rect` no código anterior usa os campos nomeados, mas a chamada de construtor para `circ` usa a ordenação. Você pode combinar os campos ordenados e nomeados, como a construção de `prism`.

O `option` o tipo é uma união discriminada simples no F# biblioteca principal. O `option` tipo é declarado da seguinte maneira.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

O código anterior Especifica que o tipo `Option` é uma união discriminada que tem dois casos, `Some` e `None`. O `Some` caso tem um valor associado que consiste em um campo anônimo cujo tipo é representado pelo parâmetro de tipo `'a`. O `None` caso não tem nenhum valor associado. Portanto, o `option` tipo Especifica um tipo genérico que tem um valor de qualquer tipo ou nenhum valor. O tipo `Option` também tem um alias de tipo em minúscula, `option`, que é mais comumente usadas.

Os identificadores de caso podem ser usados como construtores para o tipo de união discriminado. Por exemplo, o código a seguir é usado para criar valores da `option` tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Os identificadores de caso também são usados em expressões de correspondência. Em um expressão de correspondência de padrão, os identificadores são fornecidos para os valores associados com os casos individuais. Por exemplo, no código a seguir, `x` é o identificador dado o valor que está associado com o `Some` caso o `option` tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Em expressões de correspondência, você pode usar campos nomeados para especificar correspondências de união discriminadas. Para o tipo de forma que foi declarado anteriormente, você pode usar os campos nomeados como o código a seguir mostra para extrair os valores dos campos.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Normalmente, os identificadores de caso podem ser usados sem qualificá-los com o nome da união. Se você quiser que o nome seja sempre qualificado com o nome da união, você pode aplicar a [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) de atributo para a definição de tipo de união.

### <a name="unwrapping-discriminated-unions"></a>Uniões discriminadas descompactação

No F# uniões discriminadas geralmente são usadas na modelagem de domínio para um único tipo de encapsulamento. É fácil extrair o valor subjacente por meio de correspondência de padrões também. Você não precisa usar uma expressão de correspondência para um único caso:

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

O exemplo a seguir demonstra este:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

Correspondência de padrões também é permitida diretamente nos parâmetros de função, portanto, é possível desencapsular a um caso de único:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Uniões discriminadas de struct

Começando com F# 4.1, você também pode representar as uniões discriminadas como estruturas.  Isso é feito com o `[<Struct>]` atributo.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Como esses são tipos de valor e tipos de referência não, há extra uniões discriminadas de considerações em comparação com a referência:

1. Eles são copiados como tipos de valor e têm semântica de tipo de valor.
2. Você não pode usar uma definição de tipo recursiva com um struct multicase Discriminated Union.
3. Você deve fornecer nomes exclusivos de casos para um struct multicase Discriminated Union.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Usando uniões discriminadas em vez de hierarquias de objeto

Você também pode usar uma união discriminada como uma alternativa mais simples para uma hierarquia de objetos pequenos. Por exemplo, a seguinte união discriminada poderia ser usada em vez de um `Shape` classe base que tem tipos derivados para círculo, quadrado, e assim por diante.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Em vez disso, de um método virtual para calcular uma área ou o perímetro, como você usaria em uma implementação orientada a objeto, você pode usar a correspondência de padrões para ramificar para fórmulas apropriadas para calcular essas quantidades. No exemplo a seguir, fórmulas diferentes são usadas para calcular a área, dependendo da forma.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

A saída é a seguinte:

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Usando uniões discriminadas para estruturas de dados de árvore

As uniões discriminadas podem ser recursivas, que significa que a própria união pode ser incluída no tipo de um ou mais casos. Recursiva uniões discriminadas podem ser usadas para criar estruturas de árvore, que são usados para modelar expressões nas linguagens de programação. No código a seguir, uma recursivas discriminadas union é usado para criar uma estrutura de dados de árvore binária. A união consiste em dois casos, `Node`, que é um nó com um valor inteiro e subárvores esquerdas e direita, e `Tip`, que finaliza a árvore.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

No código anterior, `resultSumTree` tem o valor 10. A ilustração a seguir mostra a estrutura de árvore para `myTree`.

![Diagrama que mostra a estrutura de árvore para o myTree.](../media/discriminated-unions/tree-structure-mytree.png)

As uniões discriminadas funcionarão bem se os nós na árvore forem heterogêneos. No código a seguir, o tipo `Expression` representa a árvore de sintaxe abstrata de uma expressão em uma linguagem de programação simples que dê suporte à adição e multiplicação de números e variáveis. Alguns dos casos de união não são recursivos e representam números (`Number`) ou variáveis (`Variable`). Outros casos são recursivos e representam operações (`Add` e `Multiply`), onde os operandos também são expressões. O `Evaluate` função usa uma expressão de correspondência para processar recursivamente a árvore de sintaxe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Quando esse código é executado, o valor de `result` é 5.

## <a name="common-attributes"></a>Atributos comuns

Os seguintes atributos são geralmente vistos em uniões discriminadas:

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
