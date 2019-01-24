---
title: Carregando dados em um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 0f50638beb50220d06daef7bbd6002b319a92476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622956"
---
# <a name="loading-data-into-a-dataset"></a>Carregando dados em um DataSet
Um objeto <xref:System.Data.DataSet> deve ser populado primeiro para que você possa consultá-lo com o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Há várias maneiras diferentes de popular o <xref:System.Data.DataSet>. Por exemplo, você pode usar [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] para consultar o banco de dados e carregar os resultados para o <xref:System.Data.DataSet>. Para obter mais informações, consulte [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 Outra maneira comum de carregar dados em um <xref:System.Data.DataSet> é usar a classe <xref:System.Data.Common.DataAdapter> para recuperar dados do banco de dados. Isso é ilustrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 Esse exemplo usa <xref:System.Data.Common.DataAdapter> para consultar o banco de dados AdventureWorks para obter informações sobre as vendas do ano 2002 e carrega os resultados em um <xref:System.Data.DataSet>. Depois que o <xref:System.Data.DataSet> foi populado, você pode escrever consultas nele usando o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. O `FillDataSet` método neste exemplo é usado em consultas de exemplo na [conjunto de dados de exemplos de LINQ to](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md). Para obter mais informações, consulte [consultando DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [Consultando DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Exemplos de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
