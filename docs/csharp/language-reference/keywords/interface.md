---
title: "interface (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- interface_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84759153ebfc77ba6d39e1b3c47a00a083f267c0
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="interface-c-reference"></a>interface (Referência de C#)
Uma interface contém apenas as assinaturas de [métodos](../../../csharp/programming-guide/classes-and-structs/methods.md), [propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), [eventos](../../../csharp/programming-guide/events/index.md) ou [indexadores](../../../csharp/programming-guide/indexers/index.md). Uma classe ou struct que implementa a interface deve implementar os membros da interface que estão especificados na definição de interface. No exemplo a seguir, a classe `ImplementationClass` deve implementar um método chamado `SampleMethod` que não tem parâmetros e retorna `void`.  
  
 Para obter mais informações e exemplos, consulte [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 Uma interface pode ser um membro de um namespace ou de uma classe e pode conter assinaturas dos seguintes membros:  
  
-   [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Indexadores](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Eventos](../../../csharp/language-reference/keywords/event.md)  
  
 Uma interface pode herdar de uma ou mais interfaces base.  
  
 Quando uma lista de tipos base contém uma classe base e interfaces, a classe base deve vir em primeiro na lista.  
  
 Uma classe que implementa uma interface pode implementar membros dessa interface explicitamente. Um membro implementado explicitamente não pode ser acessado por meio de uma instância da classe, mas apenas por meio de uma instância da interface.  
  
 Para obter mais detalhes e exemplos de código sobre a implementação explícita da interface, consulte [Implementação explícita da interface](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra a implementação da interface. Neste exemplo, a interface contém a declaração de propriedade e a classe contém a implementação. Qualquer instância de uma classe que implementa `IPoint` tem propriedades de inteiro `x` e `y`.  
  
 [!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos de Referência](../../../csharp/language-reference/keywords/reference-types.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)   
 [Usando propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [Usando indexadores](../../../csharp/programming-guide/indexers/using-indexers.md)   
 [class](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)
