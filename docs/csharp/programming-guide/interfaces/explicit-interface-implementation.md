---
title: Implementação de interface explícita – Guia de Programação em C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167667"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementação de interface explícita (Guia de Programação em C#)

Caso uma [classe](../../language-reference/keywords/class.md) implemente duas interfaces que contêm um membro com a mesma assinatura, logo, implementar esse membro na classe fará com que as duas interfaces usem tal membro como sua implementação. No exemplo a seguir, todas as chamadas para `Paint` invocam o mesmo método. Esta primeira amostra define os tipos:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

A seguinte amostra chama os métodos:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Quando dois membros da interface não executam a mesma função, isso leva a uma implementação incorreta de uma ou ambas as interfaces. É possível implementar um membro de interface explicitamente — criando um membro de classe que é chamado apenas através da interface e é específico para essa interface. Nomeie o membro da classe com o nome da interface e um período. Por exemplo: 

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

O membro da classe `IControl.Paint` está disponível somente por meio da interface `IControl` e `ISurface.Paint` está disponível apenas por meio do `ISurface`. Ambas as implementações do método são separadas, e nenhuma delas está disponível diretamente na classe. Por exemplo: 

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

A implementação explícita também é usada para resolver casos em que duas interfaces declaram membros diferentes com o mesmo nome, como uma propriedade e um método. Para implementar ambas as interfaces, uma classe deve `P`usar a `P`implementação explícita para a propriedade, ou para o método, ou ambos, para evitar um erro do compilador. Por exemplo: 

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Começando com [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), você pode definir uma implementação para membros declarados em uma interface. Se uma classe herdar uma implementação de método a partir de uma interface, esse método só será acessível através de uma referência do tipo de interface. O membro herdado não aparece como parte da interface pública. A amostra a seguir define uma implementação padrão para um método de interface:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

A seguinte amostra invoca a implementação padrão:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Qualquer classe que `IControl` implemente a interface `Paint` pode substituir o método padrão, seja como um método público, ou como uma implementação de interface explícita.

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Classes e structs](../classes-and-structs/index.md)
- [Interfaces](./index.md)
- [Herança](../classes-and-structs/inheritance.md)
