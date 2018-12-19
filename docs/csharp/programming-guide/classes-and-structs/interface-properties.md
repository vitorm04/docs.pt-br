---
title: Propriedades de interface – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: c51064f9bb5e834648e0086fd8d28f9c0bd84b61
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241581"
---
# <a name="interface-properties-c-programming-guide"></a>Propriedades de interface (Guia de Programação em C#)
As propriedades podem ser declaradas em uma [interface](../../../csharp/language-reference/keywords/interface.md). Este é um exemplo de um acessador de propriedade de interface:  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 O acessador de uma propriedade de interface não tem um corpo. Portanto, a finalidade dos acessadores é indicar se a propriedade é leitura/gravação, somente leitura ou somente gravação.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a interface `IEmployee` tem uma propriedade de leitura/gravação, `Name` e uma propriedade somente leitura, `Counter`. A classe `Employee` implementa a interface `IEmployee` e usa essas duas propriedades. O programa lê o nome de um novo funcionário e o número atual de funcionários e exibe o nome do funcionário e o número do funcionário computado.  
  
 Seria possível usar o nome totalmente qualificado da propriedade, que referencia a interface na qual o membro é declarado. Por exemplo:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 Isso é denominado [Implementação explícita da interface](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md). Por exemplo, se a classe `Employee` estiver implementando duas interfaces `ICitizen` e `IEmployee` e as duas interfaces tiverem a propriedade `Name`, será necessária a implementação explícita de membro da interface. Ou seja, a seguinte declaração de propriedade:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 implementa a propriedade `Name` na interface `IEmployee`, enquanto a seguinte declaração:  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 implementa a propriedade `Name` na interface `ICitizen`.  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Saída de Exemplo  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Usando propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
- [Comparação entre propriedades e indexadores](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
- [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
- [Interfaces](../../../csharp/programming-guide/interfaces/index.md)
