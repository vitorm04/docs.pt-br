---
title: Operador &gt;&gt;= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: aebc92ffb007db7b4950313874ebc2bf3c40615f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239440"
---
# <a name="gtgt-operator-c-reference"></a>Operador &gt;&gt;= (Referência de C#)
O operador de atribuição de deslocamento para a direita.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão da forma  
  
```csharp  
x >>= y  
```  
  
 é avaliada como  
  
```csharp  
x = x >> y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador >>](../../../csharp/language-reference/operators/right-shift-operator.md) desloca `x` para a direita em um valor especificado pelo `y`.  
  
 O operador >>= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador >>](../../../csharp/language-reference/operators/right-shift-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
