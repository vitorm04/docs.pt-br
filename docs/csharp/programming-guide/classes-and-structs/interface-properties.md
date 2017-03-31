---
title: "Propriedades de interface (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: 13
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
ms.openlocfilehash: 005bb7489e229dbee5a797e55402577aad444602
ms.lasthandoff: 03/13/2017

---
# <a name="interface-properties-c-programming-guide"></a>Propriedades de interface (Guia de Programação em C#)
As propriedades podem ser declaradas em uma [interface](../../../csharp/language-reference/keywords/interface.md). Este é um exemplo de um acessador de indexador de interface:  
  
 [!code-cs[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 O acessador de uma propriedade de interface não tem um corpo. Portanto, a finalidade dos acessadores é indicar se a propriedade é leitura/gravação, somente leitura ou somente gravação.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a interface `IEmployee` tem uma propriedade de leitura/gravação, `Name` e uma propriedade somente leitura, `Counter`. A classe `Employee` implementa a interface `IEmployee` e usa essas duas propriedades. O programa lê o nome de um novo funcionário e o número atual de funcionários e exibe o nome do funcionário e o número do funcionário computado.  
  
 Seria possível usar o nome totalmente qualificado da propriedade, que referencia a interface na qual o membro é declarado. Por exemplo:  
  
 [!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 Isso é denominado [Implementação explícita da interface](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md). Por exemplo, se a classe `Employee` estiver implementando duas interfaces `ICitizen` e `IEmployee` e as duas interfaces tiverem a propriedade `Name`, será necessária a implementação explícita de membro da interface. Ou seja, a seguinte declaração de propriedade:  
  
 [!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 implementa a propriedade `Name` na interface `IEmployee`, enquanto a seguinte declaração:  
  
 [!code-cs[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 implementa a propriedade `Name` na interface `ICitizen`.  
  
 [!code-cs[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Saída de Exemplo  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Usando propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [Comparação entre propriedades e indexadores](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)
