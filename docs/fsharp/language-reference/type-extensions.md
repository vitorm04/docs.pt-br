---
title: Extensões de tipo (F#)
description: 'Saiba como extensões de tipo de F # permitem que você adiciona novos membros a um tipo de objeto definida anteriormente.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 3399778799fbf0f8eee56e332135656150918a60
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="type-extensions"></a>Extensões de tipo

Extensões de tipo permitem que você adicionar novos membros a um tipo de objeto definida anteriormente.

## <a name="syntax"></a>Sintaxe

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a>Comentários
Há duas formas de extensões de tipo que tem o comportamento e sintaxe ligeiramente diferente. Um *extensões intrínsecas* é uma extensão que aparece no mesmo namespace ou módulo, no mesmo arquivo de origem e no mesmo assembly (DLL ou arquivo executável) como o tipo que está sendo estendido. Um *extensão opcional* é uma extensão que aparece fora do módulo, namespace ou assembly do tipo que está sendo estendido original. Extensões intrínsecas aparecem no tipo quando o tipo é examinado por reflexão, mas não extensões opcionais. Extensões opcionais devem estar em módulos e são somente no escopo quando o módulo que contém a extensão está aberto.

Na sintaxe anterior, *typename* representa o tipo que está sendo estendido. Pode ser estendido a qualquer tipo que possa ser acessado, mas o nome do tipo deve ser um nome de tipo real, não é uma abreviação de tipo. Você pode definir vários membros na extensão de um tipo. O *identificador Self* representa a instância do objeto que está sendo invocado, assim como membros comuns.

O `end` palavra-chave é opcional em sintaxe leve.

Membros definidos em extensões de tipo podem ser usados exatamente como outros membros em um tipo de classe. Como outros membros, podem ser estáticos ou membros de instância. Esses métodos também são conhecidos como *métodos de extensão*; propriedades são conhecidas como *propriedades de extensão*, e assim por diante. Membros de extensão opcional são compilados para membros estáticos para o qual a instância do objeto é passada implicitamente como o primeiro parâmetro. No entanto, eles atuam como se fossem membros de instância ou membros estáticos de acordo com como elas são declaradas. Membros de extensão implícitas são incluídos como membros do tipo e podem ser usados sem restrição.

Métodos de extensão não podem ser métodos virtuais ou abstratos. Ele podem sobrecarregar outros métodos de mesmo nome, mas o compilador dá preferência a métodos de extensão não no caso de uma chamada ambígua.

Se várias extensões de tipo intrínseco existirem para um tipo, todos os membros devem ser exclusivos. Para as extensões de tipo opcionais, membros de extensões de tipo diferente para o mesmo tipo podem ter os mesmos nomes. Erros de ambiguidade ocorrer somente se o código de cliente abre dois escopos diferentes que definem os mesmos nomes de membro.

No exemplo a seguir, um tipo em um módulo tem uma extensão de tipo intrínseco. Para o código do cliente fora do módulo, a extensão do tipo aparece como um membro regular do tipo em todos os aspectos.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

Você pode usar extensões de tipo intrínseco para separar a definição de um tipo em seções. Isso pode ser útil no gerenciamento de definições de tipo grande, por exemplo, para manter o código gerado pelo compilador e o código criado separada ou agrupar código criado por pessoas diferentes ou associado a uma funcionalidade diferente.

No exemplo a seguir, uma extensão de tipo opcionais estende o `System.Int32` tipo com um método de extensão `FromString` que chama o membro estático `Parse`. O `testFromString` método demonstra que o novo membro é chamado, assim como qualquer membro de instância.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

O novo membro de instância será exibida como qualquer outro método do `Int32` tipo do IntelliSense, mas somente quando o módulo que contém a extensão está aberto ou não no escopo.

## <a name="generic-extension-methods"></a>Métodos de extensão genérico
Antes de F # 3.1, o compilador F # não suporta o uso de c#-estilo de métodos de extensão com um tipo de função do F # como o parâmetro "this", tipo de matriz, tipo de tupla ou uma variável de tipo genérico. 3.1 F # suporta o uso desses membros de extensão.

Por exemplo, no código F # 3.1, você pode usar métodos de extensão com assinaturas que são semelhantes à seguinte sintaxe no c#:

```csharp
static member Method<T>(this T input, T other)
```

Essa abordagem é particularmente útil quando o parâmetro de tipo genérico é restrito. Além disso, você pode declarar membros de extensão como esta no código F # e definir um conjunto de métodos de extensão adicional, semanticamente avançado. Em F #, você geralmente definir membros de extensão como mostra o exemplo a seguir:

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

No entanto, para um tipo genérico, a variável de tipo pode não ser restritos. Agora você pode declarar um c#-membro de extensão de estilo em F # para contornar essa limitação. Quando você combinar esse tipo de declaração com o recurso de linha de F #, você pode apresentar algoritmos genéricos como membros de extensão.

Considere a declaração a seguir:

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Usando esta declaração, você pode escrever código que se parece com o exemplo a seguir.

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

Nesse código, o mesmo código de aritmético genérico é aplicado às listas de dois tipos sem sobrecarga, definindo um membro único de extensão.


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Membros](members/index.md)
