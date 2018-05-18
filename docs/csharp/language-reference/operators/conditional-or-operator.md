---
title: Operador || (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: ce0834874f9c5b4c5154a798492600d6ac45a4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
