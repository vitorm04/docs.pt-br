---
title: Elementos Return ou Skip em uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: bedb6df564e4301ec8009992ec0ec5c51de729e0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910818"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="b210b-102">Elementos Return ou Skip em uma sequência</span><span class="sxs-lookup"><span data-stu-id="b210b-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="b210b-103">Use o operador <xref:System.Linq.Queryable.Take%2A> para retornar um número específico de elementos em uma sequência e ignorar o restante.</span><span class="sxs-lookup"><span data-stu-id="b210b-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="b210b-104">Use o operador <xref:System.Linq.Queryable.Skip%2A> para ignorar um número específico de elementos em uma sequência e retornar o restante.</span><span class="sxs-lookup"><span data-stu-id="b210b-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b210b-105"><xref:System.Linq.Enumerable.Take%2A> e <xref:System.Linq.Enumerable.Skip%2A> possuem certas limitações quando são usados em consultas no SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="b210b-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="b210b-106">Para obter mais informações, consulte a entrada "Exceções Skip e Take no SQL Server 2000" em [solução de problemas](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="b210b-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b210b-107">traduz <xref:System.Linq.Queryable.Skip%2A> por meio de uma subconsulta com o SQL `NOT EXISTS` cláusula.</span><span class="sxs-lookup"><span data-stu-id="b210b-107">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="b210b-108">Essa conversão apresenta as seguintes limitações:</span><span class="sxs-lookup"><span data-stu-id="b210b-108">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="b210b-109">O argumento deve ser um conjunto.</span><span class="sxs-lookup"><span data-stu-id="b210b-109">The argument must be a set.</span></span> <span data-ttu-id="b210b-110">Não há suporte para vários conjuntos, mesmo se ordenados.</span><span class="sxs-lookup"><span data-stu-id="b210b-110">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="b210b-111">A consulta gerada pode ser muito mais complexa do que a consulta gerada para a consulta base em que <xref:System.Linq.Queryable.Skip%2A> é aplicado.</span><span class="sxs-lookup"><span data-stu-id="b210b-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="b210b-112">Essa complexidade pode reduzir o desempenho ou até mesmo causar um tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b210b-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b210b-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b210b-113">Example</span></span>  
 <span data-ttu-id="b210b-114">O exemplo a seguir usa `Take` para selecionar os primeiros cinco `Employees` contratados.</span><span class="sxs-lookup"><span data-stu-id="b210b-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="b210b-115">Observe que a coleção é classificada primeiro por `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="b210b-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="b210b-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b210b-116">Example</span></span>  
 <span data-ttu-id="b210b-117">O exemplo a seguir usa <xref:System.Linq.Queryable.Skip%2A> para selecionar todos, exceto os 10 `Products` mais caros.</span><span class="sxs-lookup"><span data-stu-id="b210b-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="b210b-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b210b-118">Example</span></span>  
 <span data-ttu-id="b210b-119">O exemplo a seguir combina os métodos <xref:System.Linq.Queryable.Skip%2A> e <xref:System.Linq.Queryable.Take%2A> para ignorar os primeiros 50 registros e retornar os 10 seguintes.</span><span class="sxs-lookup"><span data-stu-id="b210b-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="b210b-120">As operações <xref:System.Linq.Queryable.Take%2A> e <xref:System.Linq.Queryable.Skip%2A> são bem definidas somente em conjuntos ordenados.</span><span class="sxs-lookup"><span data-stu-id="b210b-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="b210b-121">A semântica de conjuntos não ordenados ou de vários conjuntos é indefinida.</span><span class="sxs-lookup"><span data-stu-id="b210b-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="b210b-122">Devido às limitações de ordenamento no SQL, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tenta mover a ordenação do argumento do operador <xref:System.Linq.Queryable.Take%2A> ou <xref:System.Linq.Queryable.Skip%2A> para o resultado do operador.</span><span class="sxs-lookup"><span data-stu-id="b210b-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b210b-123">A conversão é diferente para [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] e [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b210b-123">Translation is different for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] and [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span> <span data-ttu-id="b210b-124">Se você pretende usar <xref:System.Linq.Queryable.Skip%2A> com uma consulta de qualquer complexidade, use [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b210b-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span>  
  
 <span data-ttu-id="b210b-125">Considere a consulta [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a seguir para [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b210b-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 <span data-ttu-id="b210b-126">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] move a ordenação para o final do código SQL, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b210b-126">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <span data-ttu-id="b210b-127">Quando <xref:System.Linq.Queryable.Take%2A> e <xref:System.Linq.Queryable.Skip%2A> são encadeados juntos, toda a ordenação especificada deve ser consistente.</span><span class="sxs-lookup"><span data-stu-id="b210b-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="b210b-128">Caso contrário, os resultados serão indefinidos.</span><span class="sxs-lookup"><span data-stu-id="b210b-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="b210b-129">Para argumentos integrais constantes e não negativos, baseados na especificação SQL, <xref:System.Linq.Queryable.Take%2A> e <xref:System.Linq.Queryable.Skip%2A> são bem definidos.</span><span class="sxs-lookup"><span data-stu-id="b210b-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b210b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b210b-130">See also</span></span>

- [<span data-ttu-id="b210b-131">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="b210b-131">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="b210b-132">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="b210b-132">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
