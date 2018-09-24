---
title: as (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: aee80b3262ccd9432d7c311dddec47185b66d05f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46695404"
---
# <a name="as-c-reference"></a>as (Referência de C#)
Você pode usar o operador `as` para realizar determinados tipos de conversões entre tipos de referência compatíveis ou [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md). O código a seguir mostra um exemplo.  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a>Comentários  
 O operador `as` é como uma operação de conversão. No entanto, se a conversão não for possível, `as` retorna `null` em vez de gerar uma exceção. Considere o exemplo a seguir:  
  
```csharp  
expression as type  
```  
  
 O código é equivalente à expressão a seguir, exceto que a variável `expression` é avaliada apenas uma vez.  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 Observe que o operador `as` executa somente conversões de referência, conversões que permitem valor nulo e conversões boxing. O operador `as` não pode realizar outras conversões, como conversões definidas pelo usuário que, em vez disso, devem ser realizadas usando expressões de conversão.  
  
## <a name="example"></a>Exemplo  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [is](../../../csharp/language-reference/keywords/is.md)  
- [Operador ?:](../../../csharp/language-reference/operators/conditional-operator.md)  
- [Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)
