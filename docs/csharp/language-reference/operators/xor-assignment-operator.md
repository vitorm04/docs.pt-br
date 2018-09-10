---
title: Operador ^= (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: d6546f23ffb6dee792339a7e3863bf58ae668d58
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857226"
---
# <a name="-operator-c-reference"></a>Operador ^= (Referência de C#)
O operador de atribuição OR exclusivo.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão da forma  
  
```csharp  
x ^= y  
```  
  
 é avaliada como  
  
```csharp  
x = x ^ y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador ^](../../../csharp/language-reference/operators/xor-operator.md) realiza uma operação OR exclusiva bit a bit em operandos integrais e OR exclusiva lógica em operandos [bool](../../../csharp/language-reference/keywords/bool.md).  
  
 O operador ^= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador ^](../../../csharp/language-reference/operators/xor-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
