---
title: "Operador || (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
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
ms.openlocfilehash: 57bcb25b0d453fa59855f40c3189eb4af2bb8b7f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>Operador || (Referência de C#)
O operador condicional OR (`||`) executa um OR lógico de seus operandos `bool`. Se o primeiro operando for avaliado como `true`, o segundo operando não será avaliado. Se o primeiro operando for avaliado como `false`, o segundo operador determinará se a expressão OR como um todo será avaliada como `true` ou `false`.  
  
## <a name="remarks"></a>Comentários  
 A operação  
  
```  
x || y  
```  
  
 corresponde à operação  
  
```  
x | y  
```  
  
 exceto se `x` for `true`, `y` não será avaliado, porque a operação OR será `true`, independentemente do valor de `y`. Esse conceito é conhecido como avaliação de “curto-circuito”.  
  
 O operador condicional OR não pode ser sobrecarregado, mas as sobrecargas dos operadores lógicos regulares e dos operadores [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md), com algumas restrições, também são consideradas sobrecargas dos operadores lógicos condicionais.  
  
## <a name="example"></a>Exemplo  
 Nos exemplos a seguir, a expressão que usa `||` avalia apenas o primeiro operando. A expressão que usa `|` avalia os dois operandos. No segundo exemplo, uma exceção de tempo de execução ocorrerá se ambos os operandos forem avaliados.  
  
 [!code-cs[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)

