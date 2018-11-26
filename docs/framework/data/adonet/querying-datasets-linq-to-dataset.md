---
title: Consultando DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: ddd92b1a95889b44eba2ec582308bf08358eeea7
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297134"
---
# <a name="querying-datasets-linq-to-dataset"></a>Consultando DataSets (LINQ to DataSet)
Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta. A formulação de consultas com o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] é semelhante ao uso do [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] em outra fonte de dados habilitada para [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Lembre-se, no entanto, que quando você usa [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas em relação a um <xref:System.Data.DataSet> objeto você está consultando uma enumeração de <xref:System.Data.DataRow> objetos, em vez de uma enumeração de um tipo personalizado. Isso significa que você pode usar qualquer um dos membros a <xref:System.Data.DataRow> classe no seu [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas. Isso permite que você crie consultas sofisticadas e complexas.  
  
 Assim como acontece com outras implementações de [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], você pode criar [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas em dois diferentes formulários: sintaxe de expressão consulta e sintaxe de consulta com base em método. Você pode usar a sintaxe de expressão de consulta ou sintaxe de consulta com base em método para executar consultas em tabelas únicas em um <xref:System.Data.DataSet>, em várias tabelas em um <xref:System.Data.DataSet>, ou em tabelas em um tipo <xref:System.Data.DataSet>.  
  
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
