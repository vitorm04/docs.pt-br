---
title: 'Operador ?: (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 68e7daac63a5f7d9bd1f48adfdee973bd695a13e
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457210"
---
# <a name="-operator-c-reference"></a>Operador ?: (Referência de C#)
O operador condicional (`?:`), comumente conhecido como o operador condicional ternário, retorna um de dois valores dependendo do valor de uma expressão booliana. Esta é a sintaxe do operador condicional.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Comentários  
 A `condition` deve ser avaliada como `true` ou `false`. Se `condition` for `true`, `first_expression` será avaliada e se tornará o resultado. Se `condition` for `false`, `second_expression` será avaliada e se tornará o resultado. Somente uma das duas expressões será avaliada.  
  
 O tipo da `first_expression` e `second_expression` devem ser iguais ou uma conversão implícita deve existir de um tipo para outro.  
  
 Você pode expressar cálculos que podem, de outra forma, exigir uma construção `if-else` mais concisamente ao usar o operador condicional. Por exemplo, o código a seguir usa primeiro uma instrução `if` e, em seguida, um operador condicional para classificar um inteiro como positivo ou negativo.  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 O operador condicional é associativo direito. A expressão `a ? b : c ? d : e` é avaliada como `a ? b : (c ? d : e)`, não como `(a ? b : c) ? d : e`.  
  
 O operador condicional não pode ser sobrecarregado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Operadores do C#](../../../csharp/language-reference/operators/index.md)  
 [if-else](../../../csharp/language-reference/keywords/if-else.md)  
 [Operadores ?. e ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [Operador ??](../../../csharp/language-reference/operators/null-coalescing-operator.md)
