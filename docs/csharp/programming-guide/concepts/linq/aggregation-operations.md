---
title: "Operações de agregação (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3bb029d2b7f9115d1c68db2844127329d34fe2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="aggregation-operations-c"></a>Operações de agregação (C#)
Uma operação de agregação computa um único valor de uma coleção de valores. Um exemplo de uma operação de agregação é o cálculo da temperatura média diária dos valores válidos de temperatura diária de um mês.  
  
 A ilustração a seguir mostra os resultados de duas operações de agregação diferentes em uma sequência de números. A primeira operação soma os números. A segunda operação retorna o valor máximo na sequência.  
  
 ![Operações de agregação LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 Os métodos de operador de consulta padrão que realizam operações de agregação são listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Agregado|Executa uma operação de agregação personalizada nos valores de uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Média|Calcula o valor médio de uma coleção de valores.|Não aplicável.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Contagem|Conta os elementos em uma coleção e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.|Não aplicável.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Conta os elementos em uma coleção grande e, opcionalmente, apenas os elementos que satisfazem a uma função de predicado.|Não aplicável.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Máx.|Determina o valor máximo em uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Mín.|Retorna o valor mínimo em uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Sum|Calcula a soma dos valores em uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>  
 [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Como computar valores de coluna em um arquivo de texto CSV (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 [Como consultar o maior arquivo ou arquivos em uma árvore de diretório (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 [Como consultar o número total de bytes em um conjunto de pastas (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
