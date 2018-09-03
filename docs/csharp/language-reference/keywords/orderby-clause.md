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
ms.openlocfilehash: de649a7e1608e6a653f3280bfd5c4e52a3b661be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43391191"
---
# <a name="orderby-clause-c-reference"></a>Cláusula orderby (Referência de C#)

Em uma expressão de consulta, a cláusula `orderby` faz com que a sequência ou subsequência (grupo) retornada seja classificada em ordem crescente ou decrescente. Várias chaves podem ser especificadas para executar uma ou mais operações de classificação secundárias. A classificação é executada pelo comparador padrão para o tipo do elemento. A ordem de classificação crescente é padrão. Também é possível especificar um comparador personalizado. No entanto, está disponível somente por meio da sintaxe baseada em método. Para obter mais informações, consulte [Classificando dados](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Exemplo

No exemplo a seguir, a primeira consulta classifica as palavras em ordem alfabética começando em A e a segunda consulta classifica as mesmas palavras em ordem decrescente. (A palavra-chave `ascending` é o valor de classificação padrão e pode ser omitida.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Exemplo

O exemplo a seguir executa uma classificação primária pelos sobrenomes dos alunos e, em seguida, uma classificação secundária pelos seus nomes.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Comentários

Em tempo de compilação, a cláusula `orderby` é convertida em uma chamada para o método <xref:System.Linq.Enumerable.OrderBy%2A>. Várias chaves na cláusula `orderby` são traduzidas para chamadas de método <xref:System.Linq.Enumerable.ThenBy%2A>.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Palavras-chave de Consulta (LINQ)](query-keywords.md)
- [LINQ (Consulta Integrada à Linguagem)](../../linq/index.md)
- [Cláusula group](group-clause.md)
- [Introdução a LINQ em C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)