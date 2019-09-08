---
title: 'Exemplos de sintaxe de consulta baseada em método: Junção (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: ba6e33f98e063aab946db27b97106272c5adef63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783665"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="1951c-102">Exemplos de sintaxe de consulta baseada em método: Junção (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="1951c-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>
<span data-ttu-id="1951c-103">A junção é uma operação importante em consultas que usam fontes de dados de destino que não têm nenhuma relação navegável entre si, como, por exemplo, as tabelas do banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="1951c-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="1951c-104">Uma junção de duas fontes de dados é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="1951c-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="1951c-105">Para obter mais informações, consulte Visão geral [dos operadoresC#de consulta Standard ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ou [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1951c-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="1951c-106">Os exemplos neste tópico demonstram como usar o método de <xref:System.Linq.Enumerable.Join%2A> para ver <xref:System.Data.DataSet> usando a sintaxe da consulta de método.</span><span class="sxs-lookup"><span data-stu-id="1951c-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="1951c-107">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="1951c-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="1951c-108">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1951c-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1951c-109">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="1951c-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="1951c-110">Para obter mais informações, confira [Como: Crie um projeto LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1951c-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="1951c-111">Join</span><span class="sxs-lookup"><span data-stu-id="1951c-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="1951c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1951c-112">Example</span></span>  
 <span data-ttu-id="1951c-113">Este exemplo reproduz uma união sobre as tabelas de `Contact` e de `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="1951c-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="1951c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1951c-114">Example</span></span>  
 <span data-ttu-id="1951c-115">Este exemplo reproduz uma união sobre as tabelas de `Contact` e de `SalesOrderHeader` , agrupamento os resultados pela identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="1951c-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1951c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1951c-116">See also</span></span>

- [<span data-ttu-id="1951c-117">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="1951c-117">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="1951c-118">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1951c-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="1951c-119">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="1951c-119">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="1951c-120">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1951c-120">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="1951c-121">Exemplos de junção</span><span class="sxs-lookup"><span data-stu-id="1951c-121">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)
- [<span data-ttu-id="1951c-122">Exemplos de conjuntos de conjunto</span><span class="sxs-lookup"><span data-stu-id="1951c-122">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
