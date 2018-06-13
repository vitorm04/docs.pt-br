---
title: TOPO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 25afda64aafcd5a97dee7ad4cee25b152ef55907
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764652"
---
# <a name="top-entity-sql"></a><span data-ttu-id="d408e-102">TOPO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d408e-102">TOP (Entity SQL)</span></span>
<span data-ttu-id="d408e-103">A cláusula SELECT pode ter uma cláusula as subjanelas TOP opcional após o modificador opcional de ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="d408e-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="d408e-104">A cláusula subpropriedades TOP especifica que apenas definir primeiro as linhas será retornado do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="d408e-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d408e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d408e-105">Syntax</span></span>  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d408e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d408e-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="d408e-107">A expressão numérica que especifica o número de linhas a serem retornadas.</span><span class="sxs-lookup"><span data-stu-id="d408e-107">The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="d408e-108">`n` pode ser um único literal numérico ou um único parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d408e-108">`n` could be a single numeric literal or a single parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d408e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d408e-109">Remarks</span></span>  
 <span data-ttu-id="d408e-110">A expressão TOP deve ser um único literal numérico ou um único parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d408e-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="d408e-111">Se um literal constante é usado, o tipo literal deve ser implicitamente promotable a Edm.Int64 (byte, int16 ou int32, int64 ou qualquer tipo de provedor que o mapeamento para um tipo que é promotable a Edm.Int64) e seu valor deve ser maior ou igual a zero.</span><span class="sxs-lookup"><span data-stu-id="d408e-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="d408e-112">Se não uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="d408e-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="d408e-113">Se um parâmetro é usado como uma expressão, o tipo de parâmetro deve também ser implicitamente promotable a Edm.Int64, mas não haverá validação do valor do parâmetro real durante a compilação porque valores de parâmetro são delimitados tarde.</span><span class="sxs-lookup"><span data-stu-id="d408e-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>  
  
 <span data-ttu-id="d408e-114">A seguir está um exemplo da expressão de TOP da constante:</span><span class="sxs-lookup"><span data-stu-id="d408e-114">The following is an example of constant TOP expression:</span></span>  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="d408e-115">O seguinte é um exemplo de expressão TOP parametrized:</span><span class="sxs-lookup"><span data-stu-id="d408e-115">The following is an example of parametrized TOP expression:</span></span>  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="d408e-116">A TOP é não determinística a menos que a consulta é classificada.</span><span class="sxs-lookup"><span data-stu-id="d408e-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="d408e-117">Se você precisar de um resultado determinístico, use o [ignorar](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) e [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) subcláusulas no [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="d408e-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="d408e-118">A TOP e os SKIP/LIMIT são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="d408e-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d408e-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d408e-119">Example</span></span>  
 <span data-ttu-id="d408e-120">A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa a TOP para especificar a uma linha superior a ser retornado do resultado da consulta.</span><span class="sxs-lookup"><span data-stu-id="d408e-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="d408e-121">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d408e-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d408e-122">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d408e-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d408e-123">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d408e-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d408e-124">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="d408e-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a><span data-ttu-id="d408e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d408e-125">See Also</span></span>  
 [<span data-ttu-id="d408e-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="d408e-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="d408e-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="d408e-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="d408e-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="d408e-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="d408e-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="d408e-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="d408e-130">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d408e-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
