---
title: ENTÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 8d2d7f9a3a1d6ff9f25db3f19bf8f39781469f9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305618"
---
# <a name="then-entity-sql"></a><span data-ttu-id="0488c-102">ENTÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0488c-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="0488c-103">O resultado de QUANDO cláusula quando avaliar a `true`.</span><span class="sxs-lookup"><span data-stu-id="0488c-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0488c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0488c-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0488c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0488c-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="0488c-106">Qualquer expressão boolean válido.</span><span class="sxs-lookup"><span data-stu-id="0488c-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="0488c-107">Qualquer expressão de consulta válida que retorna uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0488c-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0488c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0488c-108">Remarks</span></span>  
 <span data-ttu-id="0488c-109">Se `when_expression` avalia para o valor `true`, o resultado é `then-expression`correspondente.</span><span class="sxs-lookup"><span data-stu-id="0488c-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="0488c-110">Se nenhum de QUANDO as condições sejam atendidas, `else-expression` é avaliado.</span><span class="sxs-lookup"><span data-stu-id="0488c-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="0488c-111">No entanto, se não há `else-expression`, o resultado é nulo.</span><span class="sxs-lookup"><span data-stu-id="0488c-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="0488c-112">Por exemplo, consulte [caso](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0488c-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0488c-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0488c-113">Example</span></span>  
 <span data-ttu-id="0488c-114">A seguinte consulta SQL Entity usa a expressão de CASOS para avaliar um conjunto de expressões de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0488c-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="0488c-115">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0488c-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0488c-116">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="0488c-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0488c-117">Siga o procedimento em [como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0488c-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="0488c-118">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="0488c-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="0488c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0488c-119">See also</span></span>

- [<span data-ttu-id="0488c-120">CASE</span><span class="sxs-lookup"><span data-stu-id="0488c-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [<span data-ttu-id="0488c-121">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0488c-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
