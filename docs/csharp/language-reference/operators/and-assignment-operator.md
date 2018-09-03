---
title: '&amp;Operador = (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: f3a6fe20ca89a90b5a64118d73fb39e9a364d1e9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406729"
---
# <a name="amp-operator-c-reference"></a>&amp;Operador = (Referência de C#)
O operador de atribuição AND.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `&=`, como  
  
```csharp  
x &= y  
```  
  
 equivale a  
  
```csharp  
x = x & y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador &](../../../csharp/language-reference/operators/and-operator.md) executa uma operação AND lógica bit a bit em operandos integrais e AND lógica em operandos `bool`.  
  
 O operador `&=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador &](../../../csharp/language-reference/operators/and-operator.md) binário (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
