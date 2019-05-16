---
title: Interfaces
description: Saiba como F# Interfaces especificam conjuntos de membros relacionados que implementam a outras classes.
ms.date: 05/16/2016
ms.openlocfilehash: 5b57769af6c05b83b3a112635033abf4efaca772
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645373"
---
# <a name="interfaces"></a>Interfaces

*Interfaces* especificar conjuntos de membros relacionados que implementam a outras classes.

## <a name="syntax"></a>Sintaxe

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>Comentários

Declarações de interface se parecer com declarações de classe, exceto que não há membros são implementados. Em vez disso, todos os membros são abstratos, conforme indicado pela palavra-chave `abstract`. Você não fornecer um corpo de método para métodos abstratos. No entanto, você pode fornecer uma implementação padrão, incluindo também uma definição separada do membro como um método junto com o `default` palavra-chave. Isso é equivalente a criar um método virtual em uma classe base em outras linguagens .NET. Tal método virtual pode ser substituído nas classes que implementam a interface.

A acessibilidade padrão para interfaces é `public`.

Você pode, opcionalmente, nomeie cada parâmetro de método normal usando o F# sintaxe:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

No acima `ISprintable` exemplo, o `Print` método tem um único parâmetro do tipo `string` com o nome `format`.

Há duas maneiras de implementar interfaces: usando expressões de objeto e usando tipos de classe. Em ambos os casos, a expressão de tipo ou objeto de classe fornece corpos de método para métodos abstratos da interface. As implementações são específicas para cada tipo que implementa a interface. Portanto, os métodos de interface em tipos diferentes podem ser diferentes uns dos outros.

As palavras-chave `interface` e `end`, que marca o início e fim da definição, são opcionais, quando você usa a sintaxe leve. Se você não usar essas palavras-chave, o compilador tentará inferir se o tipo é uma classe ou uma interface, analisando as construções que você usa. Se você define um membro ou usar outra sintaxe de classe, o tipo é interpretado como uma classe.

O estilo de codificação do .NET deve iniciar todas as interfaces com uma letra maiuscula `I`.

## <a name="implementing-interfaces-by-using-class-types"></a>Implementando Interfaces usando tipos de classe

Você pode implementar uma ou mais interfaces em um tipo de classe usando o `interface` palavra-chave, o nome da interface e o `with` palavra-chave, seguido pelas definições de membro de interface, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Implementações de interface são herdadas, portanto a quaisquer classes derivadas não precisará reimplementá-los.

## <a name="calling-interface-methods"></a>Chamando métodos de Interface

Métodos de interface podem ser chamados apenas por meio da interface, não por meio de qualquer objeto do tipo que implementa a interface. Portanto, talvez você precise upcast para o tipo de interface usando o `:>` operador ou o `upcast` operador para chamar esses métodos.

Para chamar o método de interface quando você tem um objeto do tipo `SomeClass`, você deve upcast o objeto para o tipo de interface, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Uma alternativa é declarar um método no objeto que upcasts e chama o método de interface, como no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a>Implementando Interfaces usando expressões de objeto

Expressões de objeto fornecem uma maneira curta para implementar uma interface. Eles são úteis quando você não precisa criar um tipo nomeado, e você deseja apenas um objeto que dá suporte a métodos de interface, sem quaisquer métodos adicionais. Uma expressão de objeto é ilustrada no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a>Herança da interface

Interfaces podem herdar de uma ou mais interfaces base.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Expressões de Objeto](object-expressions.md)
- [Classes](classes.md)
