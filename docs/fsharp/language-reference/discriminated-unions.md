---
title: Uniões discriminadas (F#)
description: 'Aprenda a usar o F # discriminada uniões.'
ms.date: 05/16/2016
ms.openlocfilehash: 617c659e26df52819a98294bcbfa081ab82fed03
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2018
ms.locfileid: "34149069"
---
# <a name="discriminated-unions"></a>Uniões discriminadas

Uniões discriminadas dão suporte para valores que podem ser um de um número de casos nomeados, possivelmente uns com os tipos de valores diferentes. Uniões discriminadas são úteis para dados heterogêneos; dados que podem ter casos especiais, incluindo válido e casos de erro. dados que varia em tipo de uma instância para outra; e como uma alternativa para hierarquias de objeto pequeno. Além disso, recursiva discriminada uniões são usados para representar as estruturas de dados de árvore.

## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a>Comentários
Uniões discriminadas são semelhantes aos tipos de união em outros idiomas, mas há diferenças. Como com um tipo de união em C++ ou um tipo de variante no Visual Basic, os dados armazenados no valor não é fixo; ele pode ser uma das várias opções distintas. Ao contrário de uniões nestes outros idiomas, no entanto, cada uma das opções possíveis é fornecida um *identificador de caso*. Os identificadores de caso são nomes para os vários tipos possíveis de valores que podem ser objetos desse tipo; os valores são opcionais. Se os valores não estiverem presentes, o caso é equivalente a um caso de enumeração. Se valores estiverem presentes, cada valor pode ser um único valor de um tipo especificado ou uma tupla que agrega vários campos dos tipos iguais ou diferentes. Você pode dar um nome de um campo individual, mas o nome é opcional, mesmo se outros campos no mesmo caso são nomeados.

Acessibilidade para uniões discriminadas padrão é `public`.

Por exemplo, considere a seguinte declaração de um tipo de forma.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

O código anterior declara uma união discriminada forma, o que pode ter valores de qualquer um dos três casos: retângulo, círculo e prisma. Cada caso tem um conjunto diferente de campos. O retângulo caso tem duas chamado campos do tipo `float`, que tem a largura de nomes e o comprimento. Caso o círculo tem apenas um campo nomeado, radius. O caso de prisma tem três campos, duas das quais (largura e altura) são campos nomeadas. Campos sem nome são denominados campos anônimos.

Você pode construir objetos fornecendo os valores para os campos nomeados e anônimos de acordo com os exemplos a seguir.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Esse código mostra que você pode usar os campos nomeados na inicialização, ou você pode contar com a ordem dos campos na declaração e assim sucessivamente, forneça os valores para cada campo. A chamada de construtor para `rect` no código anterior usa os campos nomeados, mas a chamada de construtor para `circ` usa a ordenação. Você pode combinar os campos ordenados e campos nomeados, como a construção de `prism`.

O `option` tipo é uma união discriminada simple na biblioteca principal F #. O `option` tipo é declarado da seguinte maneira.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

O código anterior Especifica que o tipo `Option` é uma união discriminada que tem dois casos, `Some` e `None`. O `Some` caso tem um valor associado que consiste em um campo anônimo cujo tipo é representado pelo parâmetro de tipo `'a`. O `None` caso não tem valor associado. Portanto, o `option` tipo Especifica um tipo genérico que tem um valor de algum tipo ou nenhum valor. O tipo `Option` também tem um alias de tipo em minúsculas, `option`, que é mais comumente usados.

Os identificadores de caso podem ser usados como construtores para o tipo de união discriminado. Por exemplo, o código a seguir é usado para criar valores da `option` tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Os identificadores de caso também são usados em expressões de correspondência de padrões. Em uma expressão de correspondência de padrões, os identificadores são fornecidos para os valores associados com os casos individuais. Por exemplo, no código a seguir, `x` é o identificador atribuído o valor que está associado com o `Some` caso do `option` tipo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

No padrão de correspondência de expressões, você pode usar os campos nomeados para especificar as correspondências de união discriminadas. O tipo de forma que foi declarado anteriormente, você pode usar os campos nomeados como mostra o código a seguir para extrair os valores dos campos.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Normalmente, os identificadores de caso podem ser usados sem qualificá-los com o nome da união. Se você quiser que o nome para sempre ser qualificado com o nome da união, você pode aplicar o [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) de atributo na definição de tipo de união.

### <a name="unwrapping-discriminated-unions"></a>Uniões discriminadas descodificar

Em F # discriminada uniões geralmente são usados na modelagem de domínio para um único tipo de encapsulamento. É fácil extrair o valor subjacente por meio de correspondência de padrões também. Você não precisa usar uma expressão de correspondência para um único caso:
```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

O exemplo a seguir demonstra este:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a>Struct discriminada uniões

A partir do F # 4.1, também é possível representar discriminada uniões como estruturas.  Isso é feito com o `[<Struct>]` atributo.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Como esses são os tipos de valor e não tipos de referência, há extra em comparação com a referência de considerações discriminada uniões:

1. Eles são copiados como tipos de valor e tem semântica de tipo de valor.
2. Você não pode usar uma definição de tipo recursivo com uma estrutura multicase Discriminated Union.
3. Você deve fornecer nomes exclusivos de casos de estrutura multicase Discriminated Union.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Usando uniões discriminadas em vez de hierarquias de objeto
Você também pode usar uma união discriminada como uma alternativa mais simples para uma hierarquia de objeto pequeno. Por exemplo, a união discriminada seguinte pode ser usada em vez de um `Shape` classe base que tenha tipos derivados para círculo, quadrado, e assim por diante.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Em vez disso, um método virtual para calcular uma área ou perímetro, como você usaria em uma implementação orientada a objeto, você pode usar a correspondência de padrões a ramificação para fórmulas apropriadas para essas quantidades de computação. No exemplo a seguir, as fórmulas diferentes são usadas para calcular a área, dependendo da forma.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

A saída é a seguinte:

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Usando uniões discriminadas para estruturas de dados de árvore
Uniões discriminadas podem ser recursivos, que significa que a própria união pode ser incluída no tipo de um ou mais casos. Recursiva uniões discriminadas podem ser usados para criar estruturas de árvore, que são usados para expressões de modelo em linguagens de programação. No código a seguir, uma recursiva discriminada union é usado para criar uma estrutura de dados de árvore binária. A união consiste em dois casos, `Node`, que é um nó com um valor inteiro e subárvores esquerdas e direita, e `Tip`, que encerra a árvore.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

No código anterior, `resultSumTree` tem o valor 10. A ilustração a seguir mostra a estrutura de árvore para `myTree`.

![Estrutura de árvore para myTree](../media/TreeStructureDiagram.png)

Uniões discriminadas funcionam bem se os nós de árvore são heterogêneos. No código a seguir, o tipo `Expression` representa a árvore de sintaxe abstrata de uma expressão em uma linguagem de programação simple que oferece suporte à adição e multiplicação de números e variáveis. Alguns dos casos união não são recursivos e representar qualquer um dos números (`Number`) ou variáveis (`Variable`). Outros casos são recursivas e representam operações (`Add` e `Multiply`), onde os operandos também são expressões. O `Evaluate` função usa uma expressão de correspondência para processar recursivamente a árvore de sintaxe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Quando esse código é executado, o valor de `result` é 5.

## <a name="common-attributes"></a>Atributos comuns

Os seguintes atributos são geralmente vistos em uniões discriminadas:

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]` (F # 4.1 e superior)

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)
