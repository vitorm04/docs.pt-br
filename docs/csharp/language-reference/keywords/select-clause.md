---
title: Cláusula select – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: f1bfbeccaf6c3916a591f6447760fa01c3f8a3b6
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422359"
---
# <a name="select-clause-c-reference"></a>Cláusula select (Referência de C#)

Em uma expressão de consulta, a cláusula `select` especifica o tipo de valores que serão produzidos quando a consulta é executada. O resultado é baseado na avaliação de todas as cláusulas anteriores e em quaisquer expressões na cláusula `select` em si. Uma expressão de consulta deve terminar com uma cláusula `select` ou uma cláusula [group](group-clause.md).

O exemplo a seguir mostra uma cláusula `select` simples em uma expressão de consulta.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

O tipo da sequência produzida pela cláusula `select` determina o tipo da variável de consulta `queryHighScores`. No caso mais simples, a cláusula `select` apenas especifica a variável de intervalo. Isso faz com que a sequência retornada contenha elementos do mesmo tipo que a fonte de dados. Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). No entanto, a cláusula `select` também fornece um mecanismo poderoso para transformar (ou *projetar*) dados de origem em novos tipos. Para obter mais informações, consulte [Transformações de dados com LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra todas as diferentes formas que uma cláusula `select` pode tomar. Em cada consulta, observe a relação entre a cláusula `select` e o tipo da *variável de consulta* (`studentQuery1`, `studentQuery2` e assim por diante).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Conforme mostrado em `studentQuery8` no exemplo anterior, às vezes, convém que os elementos da sequência retornada contenham apenas um subconjunto das propriedades dos elementos de origem. Mantendo a sequência retornada a menor possível, é possível reduzir os requisitos de memória e aumentar a velocidade da execução da consulta. É possível fazer isso criando um tipo anônimo na cláusula `select` e usando um inicializador de objeto para inicializá-lo com as propriedades adequadas do elemento de origem. Para obter um exemplo de como fazer isso, consulte [Inicializadores de objeto e coleção](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Comentários

No tempo de compilação, a cláusula `select` é convertida em uma chamada de método para o operador de consulta padrão <xref:System.Linq.Enumerable.Select%2A>.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Palavras-chave de Consulta (LINQ)](query-keywords.md)
- [Cláusula From](from-clause.md)
- [partial (método) (Referência do C#)](partial-method.md)
- [Tipos Anônimos](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ em C#](../../linq/index.md)
- [Introdução a LINQ em C#](/dotnet/csharp/programming-guide/concepts/linq/)
