---
title: 'Exemplos de sintaxe da consulta com base em método: Adição (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 8bfcd8ae5d81c0d04ca7a43e6d5b25a492266605
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189338"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a><span data-ttu-id="7ebca-102">Exemplos de sintaxe da consulta com base em método: Adição (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7ebca-102">Method-Based Query Syntax Examples: Join (LINQ to DataSet)</span></span>

<span data-ttu-id="7ebca-103">A junção é uma operação importante em consultas que usam fontes de dados de destino que não têm nenhuma relação navegável entre si, como, por exemplo, as tabelas do banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="7ebca-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="7ebca-104">Uma junção de duas fontes de dados é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7ebca-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="7ebca-105">Para obter mais informações, consulte Visão geral [dos operadores de consulta Standard (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ou [padrão de operadores de consulta (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7ebca-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="7ebca-106">Os exemplos neste tópico demonstram como usar o método de <xref:System.Linq.Enumerable.Join%2A> para ver <xref:System.Data.DataSet> usando a sintaxe da consulta de método.</span><span class="sxs-lookup"><span data-stu-id="7ebca-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> method to query a <xref:System.Data.DataSet> using the method query syntax.</span></span>  
  
 <span data-ttu-id="7ebca-107">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="7ebca-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7ebca-108">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7ebca-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7ebca-109">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="7ebca-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7ebca-110">Para obter mais informações, consulte [como: criar um projeto de LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7ebca-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="join"></a><span data-ttu-id="7ebca-111">Join</span><span class="sxs-lookup"><span data-stu-id="7ebca-111">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="7ebca-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ebca-112">Example</span></span>  

 <span data-ttu-id="7ebca-113">Este exemplo reproduz uma união sobre as tabelas de `Contact` e de `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="7ebca-113">This example performs a join over the `Contact` and `SalesOrderHeader` tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="7ebca-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ebca-114">Example</span></span>  

 <span data-ttu-id="7ebca-115">Este exemplo reproduz uma união sobre as tabelas de `Contact` e de `SalesOrderHeader` , agrupamento os resultados pela identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="7ebca-115">This example performs a join over the `Contact` and `SalesOrderHeader` tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7ebca-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="7ebca-116">See also</span></span>

- [<span data-ttu-id="7ebca-117">Carregando dados em um DataSet</span><span class="sxs-lookup"><span data-stu-id="7ebca-117">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="7ebca-118">LINQ para exemplos de DataSet</span><span class="sxs-lookup"><span data-stu-id="7ebca-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="7ebca-119">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="7ebca-119">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7ebca-120">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ebca-120">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7ebca-121">Exemplos de junção</span><span class="sxs-lookup"><span data-stu-id="7ebca-121">Join Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187357)
- [<span data-ttu-id="7ebca-122">Exemplos de conjuntos de conjunto</span><span class="sxs-lookup"><span data-stu-id="7ebca-122">Dataset Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=187358)
