---
title: LIMITAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: b267e97860a2cb071b857224455f01b73115c72d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760669"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="ba824-102">LIMITAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ba824-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="ba824-103">A paginação física pode ser executada usando a subcláusula LIMIT em uma ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="ba824-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="ba824-104">LIMIT não pode ser usada separadamente da cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="ba824-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba824-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba824-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba824-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ba824-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="ba824-107">O número de itens que serão selecionados.</span><span class="sxs-lookup"><span data-stu-id="ba824-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="ba824-108">Se uma subcláusula de expressão LIMIT estiver presente em uma cláusula ORDER BY, a consulta será classificada de acordo com a especificação de classificação e o número de linhas resultante será restrito pela expressão LIMIT.</span><span class="sxs-lookup"><span data-stu-id="ba824-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="ba824-109">Por exemplo, LIMIT 5 restringirá o conjunto de resultados a 5 instâncias ou linhas.</span><span class="sxs-lookup"><span data-stu-id="ba824-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="ba824-110">LIMIT é funcionalmente equivalente à TOP com a exceção de que a LIMIT requer que a cláusula ORDER BY esteja presente.</span><span class="sxs-lookup"><span data-stu-id="ba824-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="ba824-111">SKIP e LIMIT podem ser usadas independentemente junto com a cláusula ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="ba824-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba824-112">Uma consulta Entity SQL será considerada inválida se o modificador TOP e a subcláusula SKIP estiverem presentes na mesma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="ba824-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="ba824-113">A consulta deve ser reescrita alterando a expressão TOP para uma expressão LIMIT.</span><span class="sxs-lookup"><span data-stu-id="ba824-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba824-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba824-114">Example</span></span>  
 <span data-ttu-id="ba824-115">A seguinte consulta Entity SQL usa o operador ORDER BY com LIMIT para especificar ordem de classificação usada em objetos retornados em uma instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="ba824-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="ba824-116">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ba824-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ba824-117">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ba824-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ba824-118">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ba824-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ba824-119">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="ba824-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="ba824-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba824-120">See also</span></span>

- [<span data-ttu-id="ba824-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="ba824-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="ba824-122">[Como: Paginar os resultados da consulta](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ba824-122">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="ba824-123">Paginação</span><span class="sxs-lookup"><span data-stu-id="ba824-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="ba824-124">TOP</span><span class="sxs-lookup"><span data-stu-id="ba824-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
