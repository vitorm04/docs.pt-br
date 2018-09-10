---
title: Implementação de interface explícita (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 4296591875d9843d44a81adfd5937532bcd7fe94
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085813"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementação de interface explícita (Guia de Programação em C#)
Caso uma [classe](../../../csharp/language-reference/keywords/class.md) implemente duas interfaces que contêm um membro com a mesma assinatura, logo, implementar esse membro na classe fará com que as duas interfaces usem tal membro como sua implementação. No exemplo a seguir, todas as chamadas para `Paint` invocam o mesmo método.  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 No entanto, se os dois membros de [interface](../../../csharp/language-reference/keywords/interface.md) não executarem a mesma função, isso pode levar a uma implementação incorreta de uma ou ambas as interfaces. É possível implementar um membro de interface explicitamente — criando um membro de classe que seja chamado apenas por meio da interface e seja específico para essa interface. Isso é realizado ao nomear o membro da classe com o nome da interface e um ponto final. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 O membro da classe `IControl.Paint` está disponível somente por meio da interface `IControl` e `ISurface.Paint` está disponível apenas por meio do `ISurface`. Ambas as implementações de método são separadas e nenhuma delas está diretamente disponível na classe. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 A implementação explícita também é utilizada para resolver casos em que duas interfaces declaram membros diferentes com o mesmo nome, como uma propriedade e um método:  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 Para implementar as duas interfaces, é necessário que uma classe use a implementação explícita para a propriedade P, o método P ou ambos, a fim de evitar um erro do compilador. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
- [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
