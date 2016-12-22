---
title: "Opera&#231;&#245;es de agrega&#231;&#227;o (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Opera&#231;&#245;es de agrega&#231;&#227;o (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma operação de agregação computa um único valor de uma coleção de valores. Um exemplo de uma operação de agregação está calculando a temperatura média diária de valores de temperatura diária válidos do mês.  
  
 A ilustração a seguir mostra os resultados de duas operações de agregação diferente em uma seqüência de números. A primeira operação de soma os números. A segunda operação retorna o valor máximo na sequência.  
  
 ![Operações de agregação LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ\_Aggregation")  
  
 Os métodos de operador de consulta padrão que executam operações de agregação são listados na seção a seguir.  
  
## Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta c\#|Mais Informações|  
|--------------------|---------------|------------------------------------------|----------------------|  
|Agregado|Executa uma operação de agregação personalizada nos valores de uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=fullName>|  
|Média|Calcula o valor médio de uma coleção de valores.|Não aplicável.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=fullName>|  
|Contagem|Contagens de elementos em uma coleção e, opcionalmente, apenas os elementos que atendem a uma função de predicado.|Não aplicável.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=fullName>|  
|LongCount|Contagens de elementos em uma coleção grande, opcionalmente, apenas os elementos que atendem a uma função de predicado.|Não aplicável.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=fullName>|  
|Máx.|Determina o valor máximo em uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>|  
|Min|Determina o valor mínimo em uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>|  
|Soma|Calcula a soma dos valores em uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=fullName>|  
  
## Consulte também  
 <xref:System.Linq>   
 [Visão geral de operadores de consulta padrão \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Como: calcular valores de coluna em um arquivo CSV \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)   
 [Como: consultar o maior arquivo ou arquivos em uma árvore de diretório \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)   
 [Como: consultar o número Total de Bytes em um conjunto de pastas \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)