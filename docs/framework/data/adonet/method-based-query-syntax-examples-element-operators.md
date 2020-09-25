---
title: 'Exemplos de sintaxe da consulta com base em método: Operadores de elemento (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: 669c6a34d1179caf4ec40eb8db559bdfdc9fc7f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189273"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="f5042-102">Exemplos de sintaxe da consulta com base em método: Operadores de elemento (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f5042-102">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="f5042-103">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.First%2A> e de <xref:System.Linq.Enumerable.ElementAt%2A> para obter os elementos de <xref:System.Data.DataRow> de <xref:System.Data.DataSet> usando a sintaxe da expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="f5042-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="f5042-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="f5042-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f5042-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f5042-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f5042-106">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="f5042-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 <span data-ttu-id="f5042-107">Para obter mais informações, consulte [como: criar um projeto de LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f5042-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="f5042-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="f5042-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="f5042-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5042-109">Example</span></span>  

 <span data-ttu-id="f5042-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.ElementAt%2A> para recuperar o quinto endereço onde o == “M4B 1V7” de `PostalCode` .</span><span class="sxs-lookup"><span data-stu-id="f5042-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a><span data-ttu-id="f5042-111">Primeiro</span><span class="sxs-lookup"><span data-stu-id="f5042-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="f5042-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5042-112">Example</span></span>  

 <span data-ttu-id="f5042-113">Este exemplo usa o método de <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro contato cujo nome é “Brooke”.</span><span class="sxs-lookup"><span data-stu-id="f5042-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a><span data-ttu-id="f5042-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="f5042-114">See also</span></span>

- [<span data-ttu-id="f5042-115">Carregando dados em um DataSet</span><span class="sxs-lookup"><span data-stu-id="f5042-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="f5042-116">LINQ para exemplos de DataSet</span><span class="sxs-lookup"><span data-stu-id="f5042-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="f5042-117">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="f5042-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f5042-118">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5042-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
