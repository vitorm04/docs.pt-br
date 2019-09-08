---
title: Carregando dados em um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794948"
---
# <a name="loading-data-into-a-dataset"></a>Carregando dados em um DataSet
Um <xref:System.Data.DataSet> objeto deve ser preenchido primeiro antes que você possa consultá-lo com LINQ to DataSet. Há várias maneiras diferentes de popular o <xref:System.Data.DataSet>. Por exemplo, você pode usar [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] o para consultar o banco de dados e carregar os <xref:System.Data.DataSet>resultados no. Para obter mais informações, consulte [LINQ to SQL](./sql/linq/index.md).  
  
 Outra maneira comum de carregar dados em um <xref:System.Data.DataSet> é usar a classe <xref:System.Data.Common.DataAdapter> para recuperar dados do banco de dados. Isso é ilustrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 Esse exemplo usa <xref:System.Data.Common.DataAdapter> para consultar o banco de dados AdventureWorks para obter informações sobre as vendas do ano 2002 e carrega os resultados em um <xref:System.Data.DataSet>. Depois que <xref:System.Data.DataSet> o tiver sido preenchido, você poderá escrever consultas nele usando LINQ to DataSet. O `FillDataSet` método neste exemplo é usado nas consultas de exemplo em [LINQ to DataSet exemplos](linq-to-dataset-examples.md). Para obter mais informações, consulte [consultando conjuntos](querying-datasets-linq-to-dataset.md)de dados.  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de LINQ to DataSet](linq-to-dataset-overview.md)
- [Consultando DataSets](querying-datasets-linq-to-dataset.md)
- [Exemplos de LINQ to DataSet](linq-to-dataset-examples.md)
