---
title: Operações de agregação (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2f4234b9f56794b9bfe6c56029ccc9c00ae0642
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="aggregation-operations-visual-basic"></a>Operações de agregação (Visual Basic)
Uma operação de agregação computa um único valor de uma coleção de valores. Um exemplo de uma operação de agregação é o cálculo da temperatura média diária dos valores válidos de temperatura diária de um mês.  
  
 A ilustração a seguir mostra os resultados de duas operações de agregação diferentes em uma sequência de números. A primeira operação soma os números. A segunda operação retorna o valor máximo na sequência.  
  
 ![Operações de agregação LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 Os métodos de operador de consulta padrão que realizam operações de agregação são listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais informações|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Agregado|Executa uma operação de agregação personalizada nos valores de uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Média|Calcula o valor médio de uma coleção de valores.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Contagem|Conta os elementos em uma coleção e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Conta os elementos em uma coleção grande e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Máx.|Determina o valor máximo em uma coleção.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Mín.|Retorna o valor mínimo em uma coleção.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Sum|Calcula a soma dos valores em uma coleção.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemplos de sintaxe de expressão de consulta  
  
### <a name="average"></a>Média  
 O seguinte exemplo de código usa o `Aggregate Into Average` cláusula no Visual Basic para calcular a temperatura média em uma matriz de números que representam temperaturas.  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a>Contagem  
 O seguinte exemplo de código usa o `Aggregate Into Count` cláusula no Visual Basic para contar o número de valores em uma matriz que são maiores que ou igual a 80.  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a>LongCount  
 O seguinte exemplo de código usa o `Aggregate Into LongCount` cláusula para contar o número de valores em uma matriz.  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a>Máx.  
 O seguinte exemplo de código usa o `Aggregate Into Max` cláusula para calcular a temperatura máxima em uma matriz de números que representam temperaturas.  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a>Mín.  
 O seguinte exemplo de código usa o `Aggregate Into Min` cláusula para calcular a temperatura mínimo em uma matriz de números que representam temperaturas.  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a>Sum  
 O seguinte exemplo de código usa o `Aggregate Into Sum` cláusula para calcular a quantidade total de despesas de uma matriz de valores que representam as despesas.  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>  
 [Visão geral de operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Como: computar valores de coluna em um arquivo de texto CSV (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [Como contar, somar ou fazer média de dados](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
 [Como localizar o valor mínimo ou máximo em um resultado de consulta](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
 [Como: consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 [Como: consulta para o número Total de Bytes em um conjunto de pastas (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
