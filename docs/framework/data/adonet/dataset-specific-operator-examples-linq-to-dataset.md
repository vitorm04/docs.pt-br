---
title: Exemplos Conjunto de dados específicos de operador (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 8abcab3bc2e2ee65f7b54581d9144d62cb5d5dd6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759979"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="9a411-102">Exemplos Conjunto de dados específicos de operador (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9a411-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="9a411-103">Os exemplos neste tópico demonstram como usar o método de <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> e a classe de <xref:System.Data.DataRowComparer> .</span><span class="sxs-lookup"><span data-stu-id="9a411-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="9a411-104">O `FillDataSet` método usado nesses exemplos é especificado em [carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="9a411-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="9a411-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9a411-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9a411-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="9a411-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="9a411-107">Para obter mais informações, consulte [como: criar um LINQ to DataSet de projeto no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9a411-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="9a411-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="9a411-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="9a411-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a411-109">Example</span></span>  
 <span data-ttu-id="9a411-110">Este exemplo carrega <xref:System.Data.DataTable> com resultados de consulta usando o método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> .</span><span class="sxs-lookup"><span data-stu-id="9a411-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="9a411-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="9a411-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="9a411-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a411-112">Example</span></span>  
 <span data-ttu-id="9a411-113">Este exemplo compara duas linhas de dados diferentes usando <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="9a411-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="9a411-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a411-114">See Also</span></span>  
 [<span data-ttu-id="9a411-115">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="9a411-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="9a411-116">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9a411-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
