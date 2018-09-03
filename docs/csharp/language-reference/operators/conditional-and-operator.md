---
title: Operador &amp;&amp; (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 459b791fde3e4d3940dbd3d916f940e81f365da6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388287"
---
# <a name="ampamp-operator-c-reference"></a>Operador &amp;&amp; (Referência de C#)
O operador AND condicional (`&&`) realiza uma AND lógica de seu operandos `bool`, mas só avalia seu segundo operando se for necessário.  
  
## <a name="remarks"></a>Comentários  
 A operação  
  
```csharp  
x && y  
```  
  
 corresponde à operação  
  
```csharp  
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

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Operadores do C#](../../../csharp/language-reference/operators/index.md)
