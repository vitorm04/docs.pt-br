---
title: "Indexadores em interfaces (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ee54b240956ad9730cfe7e9264e440c758573cf
ms.lasthandoff: 03/13/2017

---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexadores em interfaces (Guia de Programação em C#)
Os indexadores podem ser declarados em uma [interface](../../../csharp/language-reference/keywords/interface.md). Acessadores de indexadores de interface diferem dos acessadores de indexadores de [classe](../../../csharp/language-reference/keywords/class.md) das seguintes maneiras:  
  
-   Os acessadores de interface não usam modificadores.  
  
-   Um acessador de interface não tem um corpo.  
  
 Portanto, a finalidade do acessador é indicar se o indexador é leitura/gravação, somente leitura ou somente gravação.  
  
 Este é um exemplo de um acessador de indexador de interface:  
  
 [!code-cs[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 A assinatura de um indexador deve ser diferente das assinaturas de todos os outros indexadores declarados na mesma interface.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar indexadores de interface.  
  
 [!code-cs[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 No exemplo anterior, é possível usar a implementação de membro de interface explícita usando o nome totalmente qualificado do membro de interface. Por exemplo:  
  
```  
public string ISomeInterface.this   
{   
}   
```  
  
 No entanto, o nome totalmente qualificado só será necessário para evitar ambiguidade quando a classe estiver implementando mais de uma interface com a mesma assinatura do indexador. Por exemplo, se uma classe `Employee` estiver implementando dois interfaces, `ICitizen` e `IEmployee`, e as duas interfaces tiverem a mesma assinatura de indexador, a implementação de membro de interface explícita é necessária. Ou seja, a seguinte declaração de indexador:  
  
```  
public string IEmployee.this   
{   
}   
```  
  
 implementa o indexador na interface `IEmployee`, enquanto a seguinte declaração:  
  
```  
public string ICitizen.this   
{   
}   
```  
  
 implementa o indexador na interface `ICitizen`.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)
