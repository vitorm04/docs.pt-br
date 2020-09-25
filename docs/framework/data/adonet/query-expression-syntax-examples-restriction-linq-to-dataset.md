---
title: 'Exemplos de sintaxe da expressão de consulta: Restrição (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 92ffc3a36137281688ee3918828df111ac6707e9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172756"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="9eb40-102">Exemplos de sintaxe da expressão de consulta: Restrição (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9eb40-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>

<span data-ttu-id="9eb40-103">Os exemplos neste tópico demonstram como usar o método de <xref:System.Linq.Enumerable.Where%2A> para ver <xref:System.Data.DataSet> usando a sintaxe da expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="9eb40-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="9eb40-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="9eb40-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="9eb40-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9eb40-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9eb40-106">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="9eb40-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 <span data-ttu-id="9eb40-107">Para obter mais informações, consulte [como: criar um projeto de LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9eb40-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="9eb40-108">Where</span><span class="sxs-lookup"><span data-stu-id="9eb40-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="9eb40-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eb40-109">Example</span></span>  

 <span data-ttu-id="9eb40-110">Este exemplo retorna todos os pedidos online.</span><span class="sxs-lookup"><span data-stu-id="9eb40-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a><span data-ttu-id="9eb40-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eb40-111">Example</span></span>  

 <span data-ttu-id="9eb40-112">Este exemplo retorna os pedidos onde a quantidade de pedido é maior que 2 e menor que 6.</span><span class="sxs-lookup"><span data-stu-id="9eb40-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a><span data-ttu-id="9eb40-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eb40-113">Example</span></span>  

 <span data-ttu-id="9eb40-114">Este exemplo retorna todos os produtos colorido vermelho.</span><span class="sxs-lookup"><span data-stu-id="9eb40-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a><span data-ttu-id="9eb40-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eb40-115">Example</span></span>  

 <span data-ttu-id="9eb40-116">Este exemplo usa o método de <xref:System.Linq.Enumerable.Where%2A> para localizar os pedidos que foram feitas depois do 1º de dezembro de 2002 e usam o método de <xref:System.Data.DataRow.GetChildRows%2A> para obter detalhes para cada pedido.</span><span class="sxs-lookup"><span data-stu-id="9eb40-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="9eb40-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="9eb40-117">See also</span></span>

- [<span data-ttu-id="9eb40-118">Carregando dados em um DataSet</span><span class="sxs-lookup"><span data-stu-id="9eb40-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="9eb40-119">LINQ para exemplos de DataSet</span><span class="sxs-lookup"><span data-stu-id="9eb40-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="9eb40-120">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="9eb40-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9eb40-121">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9eb40-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
