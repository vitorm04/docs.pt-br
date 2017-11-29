---
title: Consultando DataSets (LINQ to DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4f1b1a70025dc81bdf99c636b65c23d373e73a80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="querying-datasets-linq-to-dataset"></a>Consultando DataSets (LINQ to DataSet)
Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta. A formulação de consultas com o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] é semelhante ao uso do [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] em outra fonte de dados habilitada para [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Lembre-se, no entanto, que quando você usar [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas sobre um <xref:System.Data.DataSet> objeto que você está consultando uma enumeração de <xref:System.Data.DataRow> objetos, em vez de uma enumeração de um tipo personalizado. Isso significa que você pode usar qualquer um dos membros a <xref:System.Data.DataRow> classe em seu [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas. Isso permite criar consultas avançadas e complexas.  
  
 Assim como outras implementações do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], você pode criar [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas em duas formas diferentes: sintaxe de consulta com base em método e sintaxe de expressão de consulta. Para obter mais informações sobre essas duas formas, consulte [Introdução a LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Você pode usar a sintaxe de expressão de consulta ou sintaxe de consulta com base em método para executar consultas em tabelas único em uma <xref:System.Data.DataSet>, em relação a várias tabelas em um <xref:System.Data.DataSet>, ou em tabelas em um tipo <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Consultas de tabela única](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em uma única tabela.  
  
 [Consultas de tabela cruzada](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em tabelas cruzadas.  
  
 [Consultando DataSets tipados](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Descreve como consultar objetos <xref:System.Data.DataSet> tipados.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ para exemplos de conjunto de dados](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
