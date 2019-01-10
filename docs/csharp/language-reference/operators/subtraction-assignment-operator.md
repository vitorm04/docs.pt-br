---
title: Operador -= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: dc3cedafc57e1c6ec9bc34ca4e2c2aa9c604848c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239573"
---
# <a name="--operator-c-reference"></a>Operador -= (Referência de C#)
O operador de atribuição de subtração.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `-=`, como  
  
```csharp  
x -= y  
```  
  
 equivale a  
  
```csharp  
x = x - y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O significado do [operador –](../../../csharp/language-reference/operators/subtraction-operator.md) depende dos tipos do `x` e `y` (subtração para operandos numéricos, remoção de delegado para operandos de delegado e assim por diante).  
  
 O operador `-=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [- operador](../../../csharp/language-reference/operators/subtraction-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
 O operador -= também é usado em C# para cancelar a assinatura de um evento. Confira mais informações em [Como: realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
