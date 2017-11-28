---
title: "Operador &amp;&amp; (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a>Operador &amp;&amp; (Referência de C#)
O operador AND condicional (`&&`) realiza uma AND lógica de seu operandos `bool`, mas só avalia seu segundo operando se for necessário.  
  
## <a name="remarks"></a>Comentários  
 A operação  
  
```  
x && y  
```  
  
 corresponde à operação  
  
```  
x & y  
```  
  
 exceto se `x` for `false`, `y` não será avaliado, porque o resultado da operação AND será `false`, independentemente do valor de `y`. Isso é conhecido como avaliação de "curto-circuito".  
  
 O operador AND condicional não pode ser sobrecarregado, mas as sobrecargas dos operadores lógicos regulares e dos operadores [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md), também são consideradas sobrecargas dos operadores lógicos condicionais, com algumas restrições.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a expressão condicional na segunda instrução `if` avalia apenas o primeiro operando, porque o operando retorna `false`.  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)
