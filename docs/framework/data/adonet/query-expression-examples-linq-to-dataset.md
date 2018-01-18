---
title: "Consulte exemplos de expressões (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 01b31debeb71180f4b1c86e6c9e0dfb1251bf807
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="27a5b-102">Consulte exemplos de expressões (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="27a5b-102">Query Expression Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="27a5b-103">Esta seção fornece [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programa que os exemplos na sintaxe da expressão de consulta que usam os operadores de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="27a5b-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="27a5b-104">O <xref:System.Data.DataSet> usado nesses exemplos é populada com o `FillDataSet` método, que é especificado em [carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="27a5b-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="27a5b-105">Para obter mais informações, consulte [visão geral de operadores de consulta padrão](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="27a5b-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27a5b-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="27a5b-106">In This Section</span></span>  
 [<span data-ttu-id="27a5b-107">Projeção</span><span class="sxs-lookup"><span data-stu-id="27a5b-107">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="27a5b-108">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.Select%2A> e de <xref:System.Linq.Enumerable.SelectMany%2A> para ver <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="27a5b-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="27a5b-109">Restrição</span><span class="sxs-lookup"><span data-stu-id="27a5b-109">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="27a5b-110">Os exemplos neste tópico demonstram como usar o método de <xref:System.Linq.Enumerable.Where%2A> para ver <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="27a5b-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="27a5b-111">Particionamento</span><span class="sxs-lookup"><span data-stu-id="27a5b-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="27a5b-112">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.Skip%2A> e de <xref:System.Linq.Enumerable.Take%2A> para ver <xref:System.Data.DataSet> e para dividir os resultados.</span><span class="sxs-lookup"><span data-stu-id="27a5b-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="27a5b-113">Ordenação</span><span class="sxs-lookup"><span data-stu-id="27a5b-113">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="27a5b-114">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, e métodos de <xref:System.Linq.Enumerable.ThenByDescending%2A> para ver <xref:System.Data.DataSet> e para ordenar os resultados.</span><span class="sxs-lookup"><span data-stu-id="27a5b-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="27a5b-115">Operadores de elemento</span><span class="sxs-lookup"><span data-stu-id="27a5b-115">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="27a5b-116">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.First%2A> e de <xref:System.Linq.Enumerable.ElementAt%2A> para obter os elementos de <xref:System.Data.DataRow> de <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="27a5b-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="27a5b-117">Operadores agregados</span><span class="sxs-lookup"><span data-stu-id="27a5b-117">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="27a5b-118">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, e métodos de <xref:System.Linq.Enumerable.Sum%2A> para ver <xref:System.Data.DataSet> e os dados agregados.</span><span class="sxs-lookup"><span data-stu-id="27a5b-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="27a5b-119">Operadores de junção</span><span class="sxs-lookup"><span data-stu-id="27a5b-119">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="27a5b-120">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.GroupJoin%2A> e de <xref:System.Linq.Enumerable.Join%2A> para ver <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="27a5b-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a5b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27a5b-121">See Also</span></span>  
 [<span data-ttu-id="27a5b-122">Exemplos de consulta baseada em método</span><span class="sxs-lookup"><span data-stu-id="27a5b-122">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 [<span data-ttu-id="27a5b-123">Exemplos de operador de conjunto de dados específicos</span><span class="sxs-lookup"><span data-stu-id="27a5b-123">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [<span data-ttu-id="27a5b-124">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="27a5b-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
