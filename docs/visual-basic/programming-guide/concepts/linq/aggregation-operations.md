---
title: "Opera&#231;&#245;es de agrega&#231;&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Opera&#231;&#245;es de agrega&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma operação de agregação computa um único valor de uma coleção de valores. Um exemplo de uma operação de agregação está calculando a temperatura média diária de valores de temperatura diária válidos do mês.  
  
 A ilustração a seguir mostra os resultados de duas operações de agregação diferente em uma seqüência de números. A primeira operação de soma os números. A segunda operação retorna o valor máximo na sequência.  
  
 ![Operações de agregação LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ\_Aggregation")  
  
 Os métodos de operador de consulta padrão que executam operações de agregação são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta do Visual Basic|Mais Informações|  
|--------------------|---------------|------------------------------------------------------|----------------------|  
|Agregado|Executa uma operação de agregação personalizada nos valores de uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=fullName>|  
|Média|Calcula o valor médio de uma coleção de valores.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=fullName>|  
|Contagem|Contagens de elementos em uma coleção e, opcionalmente, apenas os elementos que atendem a uma função de predicado.|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=fullName>|  
|LongCount|Contagens de elementos em uma coleção grande, opcionalmente, apenas os elementos que atendem a uma função de predicado.|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=fullName>|  
|Máx.|Determina o valor máximo em uma coleção.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>|  
|Min|Determina o valor mínimo em uma coleção.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>|  
|Soma|Calcula a soma dos valores em uma coleção.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=fullName>|  
  
## Exemplos de sintaxe de expressão de consulta  
  
### Média  
 O seguinte exemplo de código usa o `Aggregate Into Average` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para calcular a temperatura média em uma matriz de números que representam as temperaturas.  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### Contagem  
 O seguinte exemplo de código usa o `Aggregate Into Count` cláusula [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para contar o número de valores em uma matriz maior que ou igual a 80.  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### LongCount  
 O seguinte exemplo de código usa o `Aggregate Into LongCount` cláusula para contar o número de valores em uma matriz.  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### Máx.  
 O seguinte exemplo de código usa o `Aggregate Into Max` cláusula para calcular a temperatura máxima em uma matriz de números que representam as temperaturas.  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### Min  
 O seguinte exemplo de código usa o `Aggregate Into Min` cláusula para calcular a temperatura mínima em uma matriz de números que representam as temperaturas.  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### Soma  
 O seguinte exemplo de código usa o `Aggregate Into Sum` cláusula para calcular o valor total de despesas de uma matriz de valores que representam as despesas.  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Cláusula Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Como: calcular valores de coluna em um arquivo CSV \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)   
 [Como contar, somar ou fazer média de dados](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)   
 [Como localizar o valor mínimo ou máximo em um resultado de consulta](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)   
 [Como: consultar o maior arquivo ou arquivos em uma árvore de diretório \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)   
 [Como: consultar o número Total de Bytes em um conjunto de pastas \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)