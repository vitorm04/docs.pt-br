---
title: Consultando DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 18daed2ee4196a03af818dfbd0e65153ae43a840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="querying-datasets-linq-to-dataset"></a>Consultando DataSets (LINQ to DataSet)
Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta. A formulação de consultas com o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] é semelhante ao uso do [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] em outra fonte de dados habilitada para [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Lembre-se, no entanto, que quando você usar [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas sobre um <xref:System.Data.DataSet> objeto que você está consultando uma enumeração de <xref:System.Data.DataRow> objetos, em vez de uma enumeração de um tipo personalizado. Isso significa que você pode usar qualquer um dos membros a <xref:System.Data.DataRow> classe em seu [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas. Isso permite criar consultas avançadas e complexas.  
  
 Assim como outras implementações do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], você pode criar [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas em duas formas diferentes: sintaxe de consulta com base em método e sintaxe de expressão de consulta. Para obter mais informações sobre essas duas formas, consulte [Introdução a LINQ](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Você pode usar a sintaxe de expressão de consulta ou sintaxe de consulta com base em método para executar consultas em tabelas único em uma <xref:System.Data.DataSet>, em relação a várias tabelas em um <xref:System.Data.DataSet>, ou em tabelas em um tipo <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Consultas de tabela única](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em uma única tabela.  
  
 [Consultas de tabela cruzada](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em tabelas cruzadas.  
  
 [Consultando DataSets tipados](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Descreve como consultar objetos <xref:System.Data.DataSet> tipados.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Carregar dados para um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
