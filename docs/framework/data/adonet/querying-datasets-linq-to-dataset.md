---
title: Consultando DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783041"
---
# <a name="querying-datasets-linq-to-dataset"></a>Consultando DataSets (LINQ to DataSet)
Depois que um objeto de <xref:System.Data.DataSet> foi populado com dados, você pode começar a consulta. Formular consultas com LINQ to DataSet é semelhante ao uso [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] de outras [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]fontes de dados habilitadas para outras. No entanto, lembre-se de [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] que, ao <xref:System.Data.DataSet> usar consultas em um objeto, você está <xref:System.Data.DataRow> consultando uma enumeração de objetos, em vez de uma enumeração de um tipo personalizado. Isso significa que você pode usar qualquer um dos membros da <xref:System.Data.DataRow> classe em suas [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas. Isso permite que você crie consultas sofisticadas e complexas.  
  
 Assim como acontece com outras [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]implementações do, você pode criar LINQ to DataSet consultas em duas formas diferentes: sintaxe de expressão de consulta e sintaxe de consulta baseada em método. Você pode usar sintaxe de expressão de consulta ou sintaxe de consulta baseada em método para executar consultas em tabelas <xref:System.Data.DataSet>únicas em um, em relação <xref:System.Data.DataSet>a várias tabelas em uma ou em <xref:System.Data.DataSet>tabelas em um tipo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Consultas de tabela única](single-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em uma única tabela.  
  
 [Consultas de tabela cruzada](cross-table-queries-linq-to-dataset.md)  
 Descreve como executar consultas em tabelas cruzadas.  
  
 [Consultando DataSets tipados](querying-typed-datasets.md)  
 Descreve como consultar objetos <xref:System.Data.DataSet> tipados.  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de LINQ to DataSet](linq-to-dataset-examples.md)
- [Carregar dados para um conjunto de dados](loading-data-into-a-dataset.md)
