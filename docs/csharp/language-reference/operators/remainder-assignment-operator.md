---
title: Operador %= (Referência de C#)
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: aadcb5ef969ff408cc1e738fc0f5b67152fdc78b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171961"
---
# <a name="-operator-c-reference"></a>Operador %= (Referência de C#)
Operador de atribuição restante.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `%=`, como  
  
```csharp  
x %= y  
```  
  
 equivale a  
  
```csharp  
x = x % y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador %](../../../csharp/language-reference/operators/remainder-operator.md) é predefinido para tipos numéricos a fim de calcular o restante após a divisão.  
  
 O operador `%=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador %](../../../csharp/language-reference/operators/remainder-operator.md) (consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
