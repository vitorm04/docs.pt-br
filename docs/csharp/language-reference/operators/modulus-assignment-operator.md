---
title: "Operador %= (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
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
ms.openlocfilehash: 48484a0593102c92304803e5c0697501b0e26e0e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>Operador %= (Referência de C#)
Operador de atribuição restante.  
  
## <a name="remarks"></a>Comentários  
 Uma expressão que usa o operador de atribuição `%=`, como  
  
```  
x %= y  
```  
  
 equivale a  
  
```  
x = x % y  
```  
  
 exceto que `x` é avaliado apenas uma vez. O [operador %](../../../csharp/language-reference/operators/modulus-operator.md) é predefinido para tipos numéricos a fim de calcular o restante após a divisão.  
  
 O operador `%=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador %](../../../csharp/language-reference/operators/modulus-operator.md) (consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)

