---
title: Operador &gt;&gt;= (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: f2bac6a4320980d80a9b6c2597dcf8dc6f08ac70
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865017"
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
