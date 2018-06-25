---
title: Indexadores em interfaces (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 120b6e72a6ab906437c593d6eb33024d1df8f52b
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207833"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexadores em interfaces (Guia de Programação em C#)
Os indexadores podem ser declarados em uma [interface](../../../csharp/language-reference/keywords/interface.md). Acessadores de indexadores de interface diferem dos acessadores de indexadores de [classe](../../../csharp/language-reference/keywords/class.md) das seguintes maneiras:  
  
-   Os acessadores de interface não usam modificadores.  
  
-   Um acessador de interface não tem um corpo.  
  
 Portanto, a finalidade do acessador é indicar se o indexador é leitura/gravação, somente leitura ou somente gravação.  
  
 Este é um exemplo de um acessador de indexador de interface:  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 A assinatura de um indexador deve ser diferente das assinaturas de todos os outros indexadores declarados na mesma interface.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar indexadores de interface.  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 No exemplo anterior, é possível usar a implementação de membro de interface explícita usando o nome totalmente qualificado do membro de interface. Por exemplo:  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 No entanto, o nome totalmente qualificado só será necessário para evitar ambiguidade quando a classe estiver implementando mais de uma interface com a mesma assinatura do indexador. Por exemplo, se uma classe `Employee` estiver implementando dois interfaces, `ICitizen` e `IEmployee`, e as duas interfaces tiverem a mesma assinatura de indexador, a implementação de membro de interface explícita é necessária. Ou seja, a seguinte declaração de indexador:  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 implementa o indexador na interface `IEmployee`, enquanto a seguinte declaração:  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 implementa o indexador na interface `ICitizen`.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)
