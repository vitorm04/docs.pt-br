---
title: as (Referência de C#)
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: ce3163f7d957df96a5c0304adc0b3083d8e20104
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122599"
---
# <a name="as-c-reference"></a>as (Referência de C#)
Você pode usar o operador `as` para realizar determinados tipos de conversões entre tipos de referência compatíveis ou [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md). O código a seguir mostra um exemplo.  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

Como mostrado no exemplo, você precisa comparar o resultado da expressão `as` com `null` para verificar se uma conversão foi bem-sucedida. A partir do C# 7.0, você pode usar a expressão [is](is.md) para testar se uma conversão foi bem-sucedida e, condicionalmente, atribuir uma variável quando a conversão for bem-sucedida. Em muitos cenários, é mais conciso do que usar o operador `as`. Para saber mais, confira a seção [Padrão de tipo](is.md#type) do artigo [operador `is`](is.md).
  
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
