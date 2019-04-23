---
title: Remoto vs. Execução de local
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 02d0417bc05f8585dc469d365089c8123d395f64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164509"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="74405-102">Remoto vs. Execução de local</span><span class="sxs-lookup"><span data-stu-id="74405-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="74405-103">Você pode decidir executando remotamente (isto é, o mecanismo de base de dados executa a consulta na base de dados) ou localmente suas consultas ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executa a consulta em um cache local).</span><span class="sxs-lookup"><span data-stu-id="74405-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="74405-104">Execução remoto</span><span class="sxs-lookup"><span data-stu-id="74405-104">Remote Execution</span></span>  
 <span data-ttu-id="74405-105">Considere a consulta a seguir:</span><span class="sxs-lookup"><span data-stu-id="74405-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="74405-106">Se seu base de dados tem milhares de linhas de pedidos, você não deseja recuperá-los todos para processar um subconjunto pequeno.</span><span class="sxs-lookup"><span data-stu-id="74405-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="74405-107">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a classe de <xref:System.Data.Linq.EntitySet%601> implementa a interface de <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="74405-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="74405-108">Essa abordagem certifique-se de que essas consultas podem ser executadas remotamente.</span><span class="sxs-lookup"><span data-stu-id="74405-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="74405-109">Dois benefícios principais fluem dessa técnica:</span><span class="sxs-lookup"><span data-stu-id="74405-109">Two major benefits flow from this technique:</span></span>  
  
-   <span data-ttu-id="74405-110">Os dados desnecessários não são recuperados.</span><span class="sxs-lookup"><span data-stu-id="74405-110">Unnecessary data is not retrieved.</span></span>  
  
-   <span data-ttu-id="74405-111">Uma consulta executada pelo mecanismo de base de dados geralmente é mais eficiente devido aos índices de base de dados.</span><span class="sxs-lookup"><span data-stu-id="74405-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="74405-112">Execução de local</span><span class="sxs-lookup"><span data-stu-id="74405-112">Local Execution</span></span>  
 <span data-ttu-id="74405-113">Em outras situações, convém ter o conjunto completo de entidades relacionadas no cache local.</span><span class="sxs-lookup"><span data-stu-id="74405-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="74405-114">Essa finalidade, <xref:System.Data.Linq.EntitySet%601> fornece o método de <xref:System.Data.Linq.EntitySet%601.Load%2A> para carregar explicitamente todos os membros de <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="74405-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="74405-115">Se <xref:System.Data.Linq.EntitySet%601> é carregado já, consultas subsequentes são executadas localmente.</span><span class="sxs-lookup"><span data-stu-id="74405-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="74405-116">Essa abordagem ajuda em duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="74405-116">This approach helps in two ways:</span></span>  
  
-   <span data-ttu-id="74405-117">Se o conjunto completo deve ser usado localmente ou várias vezes, você pode evitar consultas e remotos latências associados.</span><span class="sxs-lookup"><span data-stu-id="74405-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
-   <span data-ttu-id="74405-118">A entidade pode ser serializada como uma entidade completo.</span><span class="sxs-lookup"><span data-stu-id="74405-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="74405-119">O fragmento de código a seguir ilustra como execução local pode ser obtida:</span><span class="sxs-lookup"><span data-stu-id="74405-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="74405-120">Comparação</span><span class="sxs-lookup"><span data-stu-id="74405-120">Comparison</span></span>  
 <span data-ttu-id="74405-121">Esses dois recursos fornecem uma combinação eficiente de opções: execução remoto para grandes coleções e execução local para coleções pequenas ou onde a coleção completa é necessária.</span><span class="sxs-lookup"><span data-stu-id="74405-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="74405-122">Você implementa a execução remoto com <xref:System.Linq.IQueryable>, e a execução local com uma coleção de memória de <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="74405-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="74405-123">Para forçar a execução local (ou seja, <xref:System.Collections.Generic.IEnumerable%601>), consulte [converter um tipo em um IEnumerable genérico](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="74405-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="74405-124">Consultas em conjuntos não ordenada</span><span class="sxs-lookup"><span data-stu-id="74405-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="74405-125">Observe a diferença importante entre uma coleção de locais que implementa <xref:System.Collections.Generic.List%601> e uma coleção que oferece consultas remotos executados em *desordenados conjuntos* em um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="74405-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="74405-126">os métodos de<xref:System.Collections.Generic.List%601> como aqueles que usam valores de índice requerem a semântica da lista, que normalmente não pode ser obtida com uma consulta remoto com um conjunto não ordenada.</span><span class="sxs-lookup"><span data-stu-id="74405-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="74405-127">Por esse motivo, esses métodos carregam implicitamente <xref:System.Data.Linq.EntitySet%601> para permitir a execução local.</span><span class="sxs-lookup"><span data-stu-id="74405-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74405-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74405-128">See also</span></span>

- [<span data-ttu-id="74405-129">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="74405-129">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
