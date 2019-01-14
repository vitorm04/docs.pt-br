---
title: Cláusula where – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 182de6ebf9d22da644f1d19566e8cab0052e8521
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221681"
---
# <a name="where-clause-c-reference"></a>Cláusula where (Referência de C#)

A cláusula `where` é usada em uma expressão de consulta para especificar quais elementos da fonte de dados serão retornados na expressão de consulta. Aplica-se uma condição booliana (*predicate*) para cada elemento de origem (referenciado pela variável de intervalo) e retorna aqueles para os quais a condição especificada for verdadeira. Uma única expressão de consulta pode conter várias cláusulas `where` e uma única cláusula pode conter várias subexpressões de predicado.

## <a name="example"></a>Exemplo

No exemplo a seguir, a cláusula `where` filtra todos os números, exceto aqueles que são menores que cinco. Se você remover a cláusula `where`, todos os números da fonte de dados serão retornados. A expressão `num < 5` é o predicado aplicado a cada elemento.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Exemplo

Dentro de uma única cláusula `where`, você pode especificar tantos predicados quanto necessário usando os operadores [&&](../operators/conditional-and-operator.md) e [&#124;&#124;](../operators/conditional-or-operator.md). No exemplo a seguir, a consulta especifica dois predicados para selecionar apenas os números pares que são menores que cinco.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Exemplo

Uma cláusula `where` pode conter um ou mais métodos que retornam valores boolianos. No exemplo a seguir, a cláusula `where` usa um método para determinar se o valor atual da variável de intervalo é par ou ímpar.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Comentários

A cláusula `where` é um mecanismo de filtragem. Ela pode ser posicionada em quase qualquer lugar em uma expressão de consulta, exceto que ela não pode ser a primeira ou a última cláusula. A cláusula `where` pode aparecer antes ou depois de uma cláusula [group](group-clause.md) dependendo se você tiver que filtrar os elementos de origem antes ou depois de eles serem agrupados.

Se um predicado especificado não for válido para os elementos na fonte de dados, o resultado será um erro em tempo de compilação. Essa é uma vantagem da verificação de tipo forte fornecida pelo [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].

Em tempo de compilação, a palavra-chave `where` é convertida em uma chamada para o método de operador de consulta padrão <xref:System.Linq.Enumerable.Where%2A>.

## <a name="see-also"></a>Consulte também

- [Palavras-chave de Consulta (LINQ)](query-keywords.md)
- [Cláusula From](from-clause.md)
- [Cláusula select](select-clause.md)
- [Filtrando Dados](../../programming-guide/concepts/linq/filtering-data.md)
- [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [Introdução a LINQ em C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)