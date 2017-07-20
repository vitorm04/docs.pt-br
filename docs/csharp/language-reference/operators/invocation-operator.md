---
title: "Operador () (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
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
ms.openlocfilehash: 159a663ca151a276b3b56f13cf8e997069210d67
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>Operador () (Referência de C#)
Além de serem usados para especificar a ordem das operações em uma expressão, os parênteses são usados para realizar as seguintes tarefas:  
  
1.  Especificar conversões ou conversões de tipo.  
  
     [!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  Invocar métodos ou delegados.  
  
     [!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>Comentários  
 Uma conversão invoca explicitamente o operador de conversão de um tipo para outro. A conversão falhará se nenhum operador de conversão desse tipo estiver definido. Para definir um operador de conversão, consulte [explícita](../../../csharp/language-reference/keywords/explicit.md) e [implícita](../../../csharp/language-reference/keywords/implicit.md).  
  
 O operador `()` não pode ser sobrecarregado.  
  
 Para obter mais informações, consulte [Conversões Cast e Conversões de Tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Uma expressão de conversão pode levar a uma sintaxe ambígua. Por exemplo, a expressão `(x)–y` poderia ser interpretada como uma expressão de conversão (uma conversão de –y para tipo x) ou como uma expressão aditiva combinada com uma expressão entre parênteses, que calcula o valor de x – y.  
  
 Para obter mais informações sobre a invocação de método, consulte [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
