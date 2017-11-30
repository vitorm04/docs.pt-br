---
title: Interfaces (F#)
description: 'Saiba como Interfaces de F # especificar conjuntos de membros relacionados que implementam de outras classes.'
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a082459-17d4-45cf-9153-0b7550a154ec
ms.openlocfilehash: d7c95e5f5cc0bc6c7f6393af990427ac491c5b79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a>Interfaces

*Interfaces* especificar conjuntos de membros relacionados que implementam de outras classes.

## <a name="syntax"></a>Sintaxe

```fsharp
// Interface declaration:
[ attributes ]
type interface-name =
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
Declarações de interface parecida com declarações de classe, exceto que os membros não são implementados. Em vez disso, todos os membros são abstratos, conforme indicado pela palavra-chave `abstract`. Você não fornecer um corpo de método para métodos abstratos. No entanto, você pode fornecer uma implementação padrão, incluindo também uma definição separada do membro como um método junto com o `default` palavra-chave. Isso é equivalente à criação de um método virtual em uma classe base em outras linguagens .NET. Esse é um método virtual pode ser substituído nas classes que implementam a interface.

Você pode, opcionalmente, nomeie cada parâmetro de método usando a sintaxe normal do F #:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

Em acima `ISprintable` exemplo, o `Print` método tem um único parâmetro do tipo `string` com o nome `format`.

Há duas maneiras de implementar interfaces: usando expressões de objeto e usando tipos de classe. Em ambos os casos, a expressão de tipo ou objeto de classe fornece corpos de métodos abstratos da interface. Implementações são específicas para cada tipo que implementa a interface. Portanto, os métodos de interface em tipos diferentes podem ser diferentes uns dos outros.

As palavras-chave `interface` e `end`, que marca o início e fim da definição, são opcionais quando você usa a sintaxe leve. Se você não usa essas palavras-chave, o compilador tenta inferir se o tipo é uma classe ou uma interface, analisando as construções que você usa. Se você define um membro ou use outra sintaxe de classe, o tipo é interpretado como uma classe.

O estilo de codificação de .NET é começar a todas as interfaces com uma letra maiuscula `I`.


## <a name="implementing-interfaces-by-using-class-types"></a>Implementando Interfaces usando tipos de classe
Você pode implementar uma ou mais interfaces em um tipo de classe usando o `interface` palavra-chave, o nome da interface e o `with` palavra-chave, seguido de definições de membro de interface, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

Implementações de interface são herdadas, não é necessário que todas as classes derivadas reimplementá-los.


## <a name="calling-interface-methods"></a>Chamando métodos de Interface
Métodos de interface podem ser chamados somente por meio da interface, não por meio de qualquer objeto do tipo que implementa a interface. Portanto, talvez você precise elevação para o tipo de interface usando o `:>` operador ou a `upcast` operador para chamar esses métodos.

Para chamar o método de interface quando você tiver um objeto do tipo `SomeClass`, você deve upcast o objeto para o tipo de interface, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

Uma alternativa é para declarar um método no objeto que upcasts e chama o método de interface, como no exemplo a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a>Implementando Interfaces usando expressões de objeto
Expressões de objeto fornecem uma maneira curta para implementar uma interface. Eles são úteis quando você não precisa criar um tipo nomeado, e você quiser apenas um objeto que oferece suporte os métodos de interface, sem qualquer métodos adicionais. Uma expressão de objeto é ilustrada no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a>Herança de interface
Interfaces podem herdar de uma ou mais interfaces base.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Expressões de Objeto](object-expressions.md)

[Classes](classes.md)
