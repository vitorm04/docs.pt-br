---
title: "Operador /= (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bd9cb025153897c2c9b47a606f0d78d8ea4ad488
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>Operador /= (Referência de C#)
O operador de atribuição de divisão.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `/=`, como  
  
```  
x /= y  
```  
  
 equivale a  
  
```  
x = x / y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador /](../../../csharp/language-reference/operators/division-operator.md) é predefinido para que os tipos numéricos executem divisão.  
  
 O operador `/=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador /](../../../csharp/language-reference/operators/division-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)). Em todos os operadores de atribuição composta, sobrecarregar o operador binário implicitamente sobrecarrega a atribuição composta equivalente.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)

