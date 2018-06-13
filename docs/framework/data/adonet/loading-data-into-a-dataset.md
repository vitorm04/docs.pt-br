---
title: Carregando dados em um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: c076b19db0acb27b57a31c20d45f619a802ebc88
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767109"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="b123c-102">Carregando dados em um DataSet</span><span class="sxs-lookup"><span data-stu-id="b123c-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="b123c-103">Um objeto <xref:System.Data.DataSet> deve ser populado primeiro para que você possa consultá-lo com o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b123c-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="b123c-104">Há várias maneiras diferentes de popular o <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b123c-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b123c-105">Por exemplo, você pode usar [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] para consultar o banco de dados e carregar os resultados para o <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b123c-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b123c-106">Para obter mais informações, consulte [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="b123c-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="b123c-107">Outra maneira comum de carregar dados em um <xref:System.Data.DataSet> é usar a classe <xref:System.Data.Common.DataAdapter> para recuperar dados do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b123c-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="b123c-108">Isso é ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b123c-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b123c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b123c-109">Example</span></span>  
 <span data-ttu-id="b123c-110">Esse exemplo usa <xref:System.Data.Common.DataAdapter> para consultar o banco de dados AdventureWorks para obter informações sobre as vendas do ano 2002 e carrega os resultados em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b123c-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b123c-111">Depois que o <xref:System.Data.DataSet> foi populado, você pode escrever consultas nele usando o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b123c-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="b123c-112">O `FillDataSet` método neste exemplo é usado em consultas de exemplo [LINQ to DataSet exemplos](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="b123c-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="b123c-113">Para obter mais informações, consulte [consultar conjuntos de dados](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b123c-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="b123c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b123c-114">See Also</span></span>  
 [<span data-ttu-id="b123c-115">Visão geral de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="b123c-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="b123c-116">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="b123c-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="b123c-117">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="b123c-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
