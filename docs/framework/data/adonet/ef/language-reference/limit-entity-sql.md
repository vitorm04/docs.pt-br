---
title: LIMITAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: e637218bb3db69d4b09fd734b939fd30f50ed806
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961882"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="5fe09-102">LIMITAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5fe09-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="5fe09-103">A paginação física pode ser executada usando a subcláusula LIMIT em uma ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="5fe09-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="5fe09-104">LIMIT não pode ser usada separadamente da cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="5fe09-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe09-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fe09-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5fe09-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="5fe09-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="5fe09-107">O número de itens que serão selecionados.</span><span class="sxs-lookup"><span data-stu-id="5fe09-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="5fe09-108">Se uma subcláusula de expressão LIMIT estiver presente em uma cláusula ORDER BY, a consulta será classificada de acordo com a especificação de classificação e o número de linhas resultante será restrito pela expressão LIMIT.</span><span class="sxs-lookup"><span data-stu-id="5fe09-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="5fe09-109">Por exemplo, LIMIT 5 restringirá o conjunto de resultados a 5 instâncias ou linhas.</span><span class="sxs-lookup"><span data-stu-id="5fe09-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="5fe09-110">LIMIT é funcionalmente equivalente à TOP com a exceção de que a LIMIT requer que a cláusula ORDER BY esteja presente.</span><span class="sxs-lookup"><span data-stu-id="5fe09-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="5fe09-111">SKIP e LIMIT podem ser usadas independentemente junto com a cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="5fe09-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fe09-112">Uma consulta Entity SQL será considerada inválida se o modificador TOP e a subcláusula SKIP estiverem presentes na mesma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="5fe09-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="5fe09-113">A consulta deve ser reescrita alterando a expressão TOP para uma expressão LIMIT.</span><span class="sxs-lookup"><span data-stu-id="5fe09-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fe09-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fe09-114">Example</span></span>  
 <span data-ttu-id="5fe09-115">A seguinte consulta Entity SQL usa o operador ORDER BY com LIMIT para especificar ordem de classificação usada em objetos retornados em uma instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="5fe09-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="5fe09-116">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5fe09-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5fe09-117">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="5fe09-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5fe09-118">Siga o procedimento em [como: Executar uma consulta que retorna resultados](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)de estruturaistype.</span><span class="sxs-lookup"><span data-stu-id="5fe09-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5fe09-119">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="5fe09-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="5fe09-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fe09-120">See also</span></span>

- [<span data-ttu-id="5fe09-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="5fe09-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="5fe09-122">[Como: Página por meio de resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5fe09-122">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="5fe09-123">Paginação</span><span class="sxs-lookup"><span data-stu-id="5fe09-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="5fe09-124">TOP</span><span class="sxs-lookup"><span data-stu-id="5fe09-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
