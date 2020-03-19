---
title: Uniões discriminadas
description: Aprenda a usar sindicatos f# discriminados.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400214"
---
# <a name="discriminated-unions"></a>Uniões discriminadas

Sindicatos discriminados dão suporte a valores que podem ser um dos vários casos nomeados, possivelmente cada um com valores e tipos diferentes. Sindicatos discriminados são úteis para dados heterogêneos; dados que podem ter casos especiais, incluindo casos válidos e de erro; dados que variam de tipo de uma instância para outra; e como alternativa para pequenas hierarquias de objetos. Além disso, sindicatos discriminados recursivos são usados para representar estruturas de dados de árvores.

## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Comentários

Os sindicatos discriminados são semelhantes aos tipos sindicais em outras línguas, mas há diferenças. Como em um tipo de união em C++ ou um tipo de variante no Visual Basic, os dados armazenados no valor não são fixos; pode ser uma das várias opções distintas. Ao contrário dos sindicatos nessas outras línguas, no entanto, cada uma das opções possíveis recebe um *identificador de caso*. Os identificadores de casos são nomes para os vários tipos possíveis de valores que objetos desse tipo poderiam ser; os valores são opcionais. Se os valores não estiverem presentes, o caso é equivalente a um caso de enumeração. Se os valores estiverem presentes, cada valor pode ser um valor único de um tipo especificado ou uma tuplo que agrega vários campos dos mesmos ou diferentes tipos. Você pode dar um nome a um campo individual, mas o nome é opcional, mesmo que outros campos no mesmo caso sejam nomeados.

Acessibilidade para sindicatos discriminados `public`é padrão para .

Por exemplo, considere a seguinte declaração de um tipo de forma.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

O código anterior declara uma forma de união discriminada, que pode ter valores de qualquer um dos três casos: Retângulo, Círculo e Prisma. Cada caso tem um conjunto diferente de campos. O estojo Retângulo tem dois `float`campos nomeados, ambos de tipo, que têm os nomes largura e comprimento. O caso Circle tem apenas um chamado campo, raio. O caso Prism tem três campos, dois dos quais (largura e altura) são nomeados campos. Campos sem nome são chamados de campos anônimos.

Você constrói objetos fornecendo valores para os campos nomeados e anônimos de acordo com os exemplos a seguir.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Este código mostra que você pode usar os campos nomeados na inicialização, ou você pode contar com a ordenação dos campos na declaração e apenas fornecer os valores para cada campo por sua vez. A chamada do `rect` construtor no código anterior usa os campos `circ` nomeados, mas a chamada do construtor para usar o pedido. Você pode misturar os campos ordenados e campos `prism`nomeados, como na construção de .

O `option` tipo é uma simples união discriminada na biblioteca núcleo F#. O `option` tipo é declarado da seguinte forma.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

O código anterior especifica `Option` que o tipo é uma `Some` união `None`discriminada que tem dois casos, e . O `Some` caso possui um valor associado que consiste em um campo `'a`anônimo cujo tipo é representado pelo parâmetro de tipo . O `None` caso não tem valor associado. Assim, `option` o tipo especifica um tipo genérico que tem um valor de algum tipo ou nenhum valor. O `Option` tipo também tem um alias tipo minúsculo, `option`que é mais comumente usado.

Os identificadores de casos podem ser usados como construtores para o tipo de união discriminada. Por exemplo, o código a seguir `option` é usado para criar valores do tipo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Os identificadores de caso também são usados em expressões de correspondência de padrões. Em uma expressão de correspondência de padrão, são fornecidos identificadores para os valores associados aos casos individuais. Por exemplo, no código `x` a seguir, está o identificador `Some` dado `option` o valor que está associado com o caso do tipo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Em expressões de correspondência de padrões, você pode usar campos nomeados para especificar correspondências sindicais discriminadas. Para o tipo de forma que foi declarado anteriormente, você pode usar os campos nomeados como o código a seguir mostra para extrair os valores dos campos.

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

Normalmente, os identificadores de caso podem ser usados sem qualificá-los com o nome do sindicato. Se você quiser que o nome seja sempre qualificado com o nome do sindicato, você pode aplicar o atributo [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) à definição do tipo de união.

### <a name="unwrapping-discriminated-unions"></a>Desembrulhando sindicatos discriminados

Em F# Sindicatos discriminados são frequentemente usados em modelagem de domínio para embrulhar um único tipo. É fácil extrair o valor subjacente através da correspondência de padrões também. Você não precisa usar uma expressão de correspondência para um único caso:

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

O exemplo a seguir demonstra este:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

A correspondência de padrões também é permitida diretamente nos parâmetros de função, para que você possa desembrulhar um único caso lá:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Sindicatos Discriminados de Estrutura

Você também pode representar sindicatos discriminados como estruturas.  Isso é feito `[<Struct>]` com o atributo.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Como são tipos de valor e não tipos de referência, existem considerações extras em comparação com sindicatos discriminados de referência:

1. Eles são copiados como tipos de valor e têm semântica do tipo de valor.
2. Você não pode usar uma definição de tipo recursiva com uma União Discriminada de estrutura multicaixa.
3. Você deve fornecer nomes de casos exclusivos para uma União Discriminada de estrutura multicase.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Usando uniões discriminadas em vez de hierarquias de objetos

Muitas vezes você pode usar uma união discriminada como uma alternativa mais simples a uma pequena hierarquia de objetos. Por exemplo, a seguinte união discriminada `Shape` poderia ser usada em vez de uma classe base que tem tipos derivados para círculo, quadrado e assim por diante.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Em vez de um método virtual para calcular uma área ou perímetro, como você usaria em uma implementação orientada a objetos, você pode usar a correspondência de padrões para ramificar-se às fórmulas apropriadas para calcular essas quantidades. No exemplo a seguir, diferentes fórmulas são usadas para calcular a área, dependendo da forma.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

A saída é da seguinte maneira:

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Usando sindicatos discriminados para estruturas de dados de árvores

Sindicatos discriminados podem ser recursivos, o que significa que o próprio sindicato pode ser incluído no tipo de um ou mais casos. Uniões discriminadas recursivas podem ser usadas para criar estruturas de árvores, que são usadas para modelar expressões em linguagens de programação. No código a seguir, uma união discriminada recursiva é usada para criar uma estrutura binária de dados de árvores. A união consiste em `Node`dois casos, que é um nó com valor inteiro e `Tip`subárvores esquerda e direita, e , que termina a árvore.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

No código anterior, `resultSumTree` tem o valor 10. A ilustração a seguir `myTree`mostra a estrutura da árvore para .

![Diagrama que mostra a estrutura da árvore para myTree.](../media/discriminated-unions/tree-structure-mytree.png)

Sindicatos discriminados funcionam bem se os nós na árvore são heterogêneos. No código a seguir, o tipo `Expression` representa a árvore de sintaxe abstrata de uma expressão em uma linguagem de programação simples que suporta a adição e multiplicação de números e variáveis. Alguns dos casos sindicais não são recursivos e representam números (`Number`) ou variáveis (`Variable`). Outros casos são recursivos,`Add` e `Multiply`representam operações (e), onde os operands também são expressões. A `Evaluate` função usa uma expressão de correspondência para processar recursivamente a árvore de sintaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Quando este código é executado, `result` o valor de é 5.

## <a name="members"></a>Membros

É possível definir membros em sindicatos discriminados. O exemplo a seguir mostra como definir uma propriedade e implementar uma interface:

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a>Atributos comuns

Os seguintes atributos são comumente vistos em sindicatos discriminados:

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>Confira também

- [Referência de idioma F#](index.md)
