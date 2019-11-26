---
title: Operações de conjunto
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: fe9d910415f30fe672dc702f719fdefdb9c0b3d1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350611"
---
# <a name="set-operations-visual-basic"></a>Set Operations (Visual Basic)

As operações de conjunto na LINQ referem-se a operações de consulta que geram um conjunto de resultados baseado na presença ou ausência de elementos equivalentes dentro da mesma ou de coleções (ou conjuntos) separadas.

Os métodos de operador de consulta padrão que executam operações de conjunto estão listados na seção a seguir.

## <a name="methods"></a>Métodos

|Nome do método|Descrição|Visual Basic Query Expression Syntax|Mais informações|
|-----------------|-----------------|------------------------------------------|----------------------|
|Distinct|Remove os valores duplicados de uma coleção.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|Exceto|Retorna a diferença de conjunto, que significa os elementos de uma coleção que não aparecem em uma segunda coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|Interseção|Retorna a interseção de conjunto, o que significa os elementos que aparecem em cada uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|União|Retorna a união de conjunto, o que significa os elementos únicos que aparecem em qualquer uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a>Comparação de operações de conjuntos

### <a name="distinct"></a>Distinct

A ilustração a seguir mostra o comportamento do método <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> em uma sequência de caracteres. A sequência retornada contém os elementos exclusivos da sequência de entrada.

![Gráfico mostrando o comportamento de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a>Exceto

A ilustração a seguir mostra o comportamento de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>. A sequência retornada contém apenas os elementos da primeira sequência de entrada que não estão na segunda sequência de entrada.

![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")

### <a name="intersect"></a>Interseção

A ilustração a seguir mostra o comportamento de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>. A sequência retornada contém os elementos que são comuns a ambas as sequências de entrada.

![Gráfico mostrando a interseção de duas sequências.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a>União

A ilustração a seguir descreve uma operação de união em duas sequências de caracteres. A sequência retornada contém os elementos exclusivos das duas sequências de entrada.

![Gráfico mostrando a união de duas sequências.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a>Exemplo de sintaxe de expressão de consulta

The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a>Consulte também

- <xref:System.Linq>
- [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Cláusula Distinct](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
