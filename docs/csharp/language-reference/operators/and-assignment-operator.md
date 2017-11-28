---
title: "&amp;Operador = (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a>&amp;Operador = (Referência de C#)
O operador de atribuição AND.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `&=`, como  
  
```  
x &= y  
```  
  
 equivale a  
  
```  
x = x & y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador &](../../../csharp/language-reference/operators/and-operator.md) executa uma operação AND lógica bit a bit em operandos integrais e AND lógica em operandos `bool`.  
  
 O operador `&=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador &](../../../csharp/language-reference/operators/and-operator.md) binário (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
