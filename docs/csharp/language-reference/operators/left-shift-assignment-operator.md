---
title: Operador &lt;&lt;= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: f49c6360d6fee3f6d612aee51446545f25cd7d18
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239167"
---
# <a name="ltlt-operator-c-reference"></a>Operador &lt;&lt;= (Referência de C#)
O operador de atribuição de deslocamento para a esquerda.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão da forma  
  
```csharp  
x <<= y  
```  
  
 é avaliada como  
  
```csharp  
x = x << y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador <<](../../../csharp/language-reference/operators/left-shift-operator.md) desloca `x` para a esquerda pelo número de bits especificado pelo `y`.  
  
 O operador `<<=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador <<](../../../csharp/language-reference/operators/left-shift-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
