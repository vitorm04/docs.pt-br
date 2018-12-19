---
title: Operador () – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 57c23dbd6ee95597514dba92e7217bdcc3e38f24
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236447"
---
# <a name="-operator-c-reference"></a>Operador () (Referência de C#)
Além de serem usados para especificar a ordem das operações em uma expressão, os parênteses são usados para realizar as seguintes tarefas:  
  
1.  Especificar conversões ou conversões de tipo.  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  Invocar métodos ou delegados.  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>Comentários  
 Uma conversão invoca explicitamente o operador de conversão de um tipo para outro. A conversão falhará se nenhum operador de conversão desse tipo estiver definido. Para definir um operador de conversão, consulte [explícita](../../../csharp/language-reference/keywords/explicit.md) e [implícita](../../../csharp/language-reference/keywords/implicit.md).  
  
 O operador `()` não pode ser sobrecarregado.  
  
 Para obter mais informações, consulte [Conversões e conversões de Tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Para obter mais informações sobre a invocação de método, consulte [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
