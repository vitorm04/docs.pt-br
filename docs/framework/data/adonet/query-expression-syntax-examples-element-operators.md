---
title: 'Exemplos de sintaxe de expressão de consulta: Operadores de elemento (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: 663356ec3dc39aa3eb7e858f028fc9a8f7d27db6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644437"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="aac66-102">Exemplos de sintaxe de expressão de consulta: Operadores de elemento (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="aac66-102">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="aac66-103">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.First%2A> e de <xref:System.Linq.Enumerable.ElementAt%2A> para obter os elementos de <xref:System.Data.DataRow> de <xref:System.Data.DataSet> usando a sintaxe da expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="aac66-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="aac66-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="aac66-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="aac66-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="aac66-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="aac66-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="aac66-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="aac66-107">Para obter mais informações, confira [Como: Criar um projeto LINQ to DataSet no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="aac66-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="aac66-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="aac66-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="aac66-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aac66-109">Example</span></span>  
 <span data-ttu-id="aac66-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.ElementAt%2A> para recuperar o quinto endereço onde o == “M4B 1V7” de `PostalCode` .</span><span class="sxs-lookup"><span data-stu-id="aac66-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="aac66-111">Primeiro</span><span class="sxs-lookup"><span data-stu-id="aac66-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="aac66-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aac66-112">Example</span></span>  
 <span data-ttu-id="aac66-113">Este exemplo usa o método de <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro contato cujo nome é “Brooke”.</span><span class="sxs-lookup"><span data-stu-id="aac66-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="aac66-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aac66-114">See also</span></span>

- [<span data-ttu-id="aac66-115">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="aac66-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="aac66-116">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="aac66-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="aac66-117">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="aac66-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="aac66-118">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aac66-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
