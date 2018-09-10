---
title: Operador |= (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: fe56005ce94656b5e8a075cddfb91dc0da096cf7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194501"
---
# <a name="-operator-c-reference"></a>Operador |= (Referência de C#)
O operador de atribuição OR.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `|=`, como  
  
```csharp  
x |= y  
```  
  
 equivale a  
  
```csharp  
x = x | y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador &#124;](../../../csharp/language-reference/operators/or-operator.md) executa uma operação OR lógica bit a bit em operandos integrais e OR lógica em operandos bool.  
  
 O operador `|=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador &#124;](../../../csharp/language-reference/operators/or-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
