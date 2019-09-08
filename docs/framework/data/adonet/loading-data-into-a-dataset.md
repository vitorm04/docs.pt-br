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
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="e430c-102">Carregando dados em um DataSet</span><span class="sxs-lookup"><span data-stu-id="e430c-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="e430c-103">Um <xref:System.Data.DataSet> objeto deve ser preenchido primeiro antes que você possa consultá-lo com LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="e430c-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="e430c-104">Há várias maneiras diferentes de popular o <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e430c-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e430c-105">Por exemplo, você pode usar [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] o para consultar o banco de dados e carregar os <xref:System.Data.DataSet>resultados no.</span><span class="sxs-lookup"><span data-stu-id="e430c-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e430c-106">Para obter mais informações, consulte [LINQ to SQL](./sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="e430c-106">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="e430c-107">Outra maneira comum de carregar dados em um <xref:System.Data.DataSet> é usar a classe <xref:System.Data.Common.DataAdapter> para recuperar dados do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e430c-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="e430c-108">Isso é ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e430c-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e430c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e430c-109">Example</span></span>  
 <span data-ttu-id="e430c-110">Esse exemplo usa <xref:System.Data.Common.DataAdapter> para consultar o banco de dados AdventureWorks para obter informações sobre as vendas do ano 2002 e carrega os resultados em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e430c-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e430c-111">Depois que <xref:System.Data.DataSet> o tiver sido preenchido, você poderá escrever consultas nele usando LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="e430c-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="e430c-112">O `FillDataSet` método neste exemplo é usado nas consultas de exemplo em [LINQ to DataSet exemplos](linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="e430c-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="e430c-113">Para obter mais informações, consulte [consultando conjuntos](querying-datasets-linq-to-dataset.md)de dados.</span><span class="sxs-lookup"><span data-stu-id="e430c-113">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="e430c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e430c-114">See also</span></span>

- [<span data-ttu-id="e430c-115">Visão geral de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e430c-115">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="e430c-116">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="e430c-116">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="e430c-117">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e430c-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
