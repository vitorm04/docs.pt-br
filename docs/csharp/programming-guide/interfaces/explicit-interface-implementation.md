---
title: "Implementação de Interface Explícita (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3c1ee20ec2984c6471586b3bf7f6d0086a7a5a4d
ms.lasthandoff: 03/13/2017

---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementação de interface explícita (Guia de Programação em C#)
Caso uma [classe](../../../csharp/language-reference/keywords/class.md) implemente duas interfaces que contêm um membro com a mesma assinatura, logo, implementar esse membro na classe fará com que as duas interfaces usem tal membro como sua implementação. No exemplo a seguir, todas as chamadas para `Paint` invocam o mesmo método.  
  
 [!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 No entanto, se os dois membros de [interface](../../../csharp/language-reference/keywords/interface.md) não executarem a mesma função, isso pode levar a uma implementação incorreta de uma ou ambas as interfaces. É possível implementar um membro de interface explicitamente — criando um membro de classe que seja chamado apenas por meio da interface e seja específico para essa interface. Isso é realizado ao nomear o membro da classe com o nome da interface e um ponto final. Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 O membro da classe `IControl.Paint` está disponível somente por meio da interface `IControl` e `ISurface.Paint` está disponível apenas por meio do `ISurface`. Ambas as implementações de método são separadas e nenhuma delas está diretamente disponível na classe. Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 A implementação explícita também é utilizada para resolver casos em que duas interfaces declaram membros diferentes com o mesmo nome, como uma propriedade e um método:  
  
 [!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 Para implementar as duas interfaces, é necessário que uma classe use a implementação explícita para a propriedade P, o método P ou ambos, a fim de evitar um erro do compilador. Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
