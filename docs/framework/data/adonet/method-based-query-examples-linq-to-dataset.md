---
title: "Exemplos de consulta com base em método (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 313364f71c463a320816bb92113f3b720146fe25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-examples-linq-to-dataset"></a><span data-ttu-id="fe58c-102">Exemplos de consulta com base em método (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="fe58c-102">Method-Based Query Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="fe58c-103">Esta seção fornece [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programa que os exemplos na sintaxe da consulta com base em método que usam os operadores de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="fe58c-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in method-based query syntax that use the standard query operators.</span></span> <span data-ttu-id="fe58c-104">O <xref:System.Data.DataSet> usado nesses exemplos é populada com o `FillDataSet` método, que é especificado em [carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="fe58c-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="fe58c-105">Para obter mais informações, consulte [visão geral de operadores de consulta padrão](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="fe58c-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe58c-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="fe58c-106">In This Section</span></span>  
 [<span data-ttu-id="fe58c-107">Projeção</span><span class="sxs-lookup"><span data-stu-id="fe58c-107">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 <span data-ttu-id="fe58c-108">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.Select%2A> e de <xref:System.Linq.Enumerable.SelectMany%2A> para ver <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="fe58c-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="fe58c-109">Particionamento</span><span class="sxs-lookup"><span data-stu-id="fe58c-109">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 <span data-ttu-id="fe58c-110">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.Skip%2A> e de <xref:System.Linq.Enumerable.Take%2A> para ver <xref:System.Data.DataSet> e para dividir os resultados.</span><span class="sxs-lookup"><span data-stu-id="fe58c-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="fe58c-111">Ordenação</span><span class="sxs-lookup"><span data-stu-id="fe58c-111">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="fe58c-112">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, e métodos de <xref:System.Linq.Enumerable.ThenByDescending%2A> para ver <xref:System.Data.DataSet> e para ordenar os resultados.</span><span class="sxs-lookup"><span data-stu-id="fe58c-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="fe58c-113">Operadores de conjunto</span><span class="sxs-lookup"><span data-stu-id="fe58c-113">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 <span data-ttu-id="fe58c-114">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, e operadores de <xref:System.Linq.Enumerable.Union%2A> para executar operações valor de comparação com base em conjuntos de linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="fe58c-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.</span></span>  
  
 [<span data-ttu-id="fe58c-115">Operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="fe58c-115">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 <span data-ttu-id="fe58c-116">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, e métodos de <xref:System.Linq.Enumerable.ToList%2A> para executar imediatamente uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="fe58c-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 [<span data-ttu-id="fe58c-117">Operadores de elemento</span><span class="sxs-lookup"><span data-stu-id="fe58c-117">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 <span data-ttu-id="fe58c-118">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.First%2A> e de <xref:System.Linq.Enumerable.ElementAt%2A> para obter os elementos de <xref:System.Data.DataRow> de <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="fe58c-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="fe58c-119">Operadores agregados</span><span class="sxs-lookup"><span data-stu-id="fe58c-119">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="fe58c-120">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, e métodos de <xref:System.Linq.Enumerable.Sum%2A> para ver <xref:System.Data.DataSet> e os dados agregados.</span><span class="sxs-lookup"><span data-stu-id="fe58c-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="fe58c-121">Join</span><span class="sxs-lookup"><span data-stu-id="fe58c-121">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 <span data-ttu-id="fe58c-122">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.GroupJoin%2A> e de <xref:System.Linq.Enumerable.Join%2A> para ver <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="fe58c-122">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe58c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe58c-123">See Also</span></span>  
 [<span data-ttu-id="fe58c-124">Exemplos de expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="fe58c-124">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 [<span data-ttu-id="fe58c-125">Exemplos de operador de conjunto de dados específicos</span><span class="sxs-lookup"><span data-stu-id="fe58c-125">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [<span data-ttu-id="fe58c-126">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="fe58c-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
