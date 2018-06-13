---
title: Cláusula orderby (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 1fd0036e8bd3c838fe92ca27635cd7638d59ef1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268043"
---
# <a name="orderby-clause-c-reference"></a>Cláusula orderby (Referência de C#)
Em uma expressão de consulta, a cláusula `orderby` faz com que a sequência ou subsequência (grupo) retornada seja classificada em ordem crescente ou decrescente. Várias chaves podem ser especificadas para executar uma ou mais operações de classificação secundárias. A classificação é executada pelo comparador padrão para o tipo do elemento. A ordem de classificação crescente é padrão. Também é possível especificar um comparador personalizado. No entanto, está disponível somente por meio da sintaxe baseada em método. Para obter mais informações, consulte [Classificando dados](../../programming-guide/concepts/linq/sorting-data.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a primeira consulta classifica as palavras em ordem alfabética começando em A e a segunda consulta classifica as mesmas palavras em ordem decrescente. (A palavra-chave `ascending` é o valor de classificação padrão e pode ser omitida.)  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa uma classificação primária pelos sobrenomes dos alunos e, em seguida, uma classificação secundária pelos seus nomes.  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a>Comentários  
 Em tempo de compilação, a cláusula `orderby` é convertida em uma chamada para o método <xref:System.Linq.Enumerable.OrderBy%2A>. Várias chaves na cláusula `orderby` são traduzidas para chamadas de método <xref:System.Linq.Enumerable.ThenBy%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Palavras-chave de Consulta (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md)  
 [Introdução a LINQ em C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
