---
title: Exemplos Conjunto de dados específicos de operador (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 4cd99a103fabee3c87036a9933077a3a967f5a13
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173686"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="65583-102">Exemplos Conjunto de dados específicos de operador (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="65583-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="65583-103">Os exemplos neste tópico demonstram como usar o método de <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> e a classe de <xref:System.Data.DataRowComparer> .</span><span class="sxs-lookup"><span data-stu-id="65583-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="65583-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="65583-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="65583-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="65583-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="65583-106">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="65583-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="65583-107">Para obter mais informações, consulte [como: criar um projeto de LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="65583-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="65583-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="65583-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="65583-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65583-109">Example</span></span>  

 <span data-ttu-id="65583-110">Este exemplo carrega <xref:System.Data.DataTable> com resultados de consulta usando o método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> .</span><span class="sxs-lookup"><span data-stu-id="65583-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="65583-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="65583-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="65583-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65583-112">Example</span></span>  

 <span data-ttu-id="65583-113">Este exemplo compara duas linhas de dados diferentes usando <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="65583-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="65583-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="65583-114">See also</span></span>

- [<span data-ttu-id="65583-115">Carregando dados em um DataSet</span><span class="sxs-lookup"><span data-stu-id="65583-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="65583-116">LINQ para exemplos de DataSet</span><span class="sxs-lookup"><span data-stu-id="65583-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
