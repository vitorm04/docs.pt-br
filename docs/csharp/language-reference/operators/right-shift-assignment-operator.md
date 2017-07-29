---
title: "Operador &gt;&gt;= (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 64f387e475681ffc76f113435ba090b40780dda3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="gtgt-operator-c-reference"></a>Operador &gt;&gt;= (Referência de C#)
O operador de atribuição de deslocamento para a direita.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão da forma  
  
```  
x >>= y  
```  
  
 é avaliada como  
  
```  
x = x >> y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador >>](../../../csharp/language-reference/operators/right-shift-operator.md) desloca `x` para a direita em um valor especificado pelo `y`.  
  
 O operador >>= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador >>](../../../csharp/language-reference/operators/right-shift-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)

