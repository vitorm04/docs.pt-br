---
title: CASO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 79544f4180313a008669c56c4f2740c889043c6d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251249"
---
# <a name="case-entity-sql"></a><span data-ttu-id="b6977-102">CASO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b6977-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="b6977-103">Avalia um conjunto de expressões de `Boolean` para determinar o resultado.</span><span class="sxs-lookup"><span data-stu-id="b6977-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6977-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6977-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6977-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b6977-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="b6977-106">É um espaço reservado que indica que várias QUANDO as cláusulas de `Boolean_expression` ENTÃO `result_expression` podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="b6977-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="b6977-107">ENTÃO `result_expression`</span><span class="sxs-lookup"><span data-stu-id="b6977-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="b6977-108">A expressão é retornada quando `Boolean_expression` avalia a `true`.</span><span class="sxs-lookup"><span data-stu-id="b6977-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="b6977-109">`result expression` é qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="b6977-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="b6977-110">`else_result_expression`OUTRO</span><span class="sxs-lookup"><span data-stu-id="b6977-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="b6977-111">A expressão é retornada se qualquer operação de comparação avalia a `true`.</span><span class="sxs-lookup"><span data-stu-id="b6977-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="b6977-112">Se esse argumento é omitido e nenhuma operação de comparação avalia a `true`, os CASOS retornam o zero.</span><span class="sxs-lookup"><span data-stu-id="b6977-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="b6977-113">`else_result_expression` é qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="b6977-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="b6977-114">Os tipos de dados de `else_result_expression` e qualquer `result_expression` devem ser os mesmos ou devem ser uma conversão implícita.</span><span class="sxs-lookup"><span data-stu-id="b6977-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="b6977-115">QUANDO `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="b6977-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="b6977-116">A expressão é avaliada de `Boolean` quando o formato pesquisada de CASOS é usado.</span><span class="sxs-lookup"><span data-stu-id="b6977-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="b6977-117">`Boolean_expression` é qualquer expressão válida de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b6977-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6977-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b6977-118">Return Value</span></span>  
 <span data-ttu-id="b6977-119">Retorna o tipo mais alto de precedência de conjunto de tipos em `result_expression` e `else_result_expression`opcional.</span><span class="sxs-lookup"><span data-stu-id="b6977-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6977-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6977-120">Remarks</span></span>  
 <span data-ttu-id="b6977-121">A [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão CASE é semelhante à expressão de caso Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b6977-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="b6977-122">Você usa a expressão dos casos para fazer uma série de teste condicional para determinar qual expressão renderá o resultado apropriado.</span><span class="sxs-lookup"><span data-stu-id="b6977-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="b6977-123">Este formulário da expressão dos casos se aplica a uma série de uma ou mais expressões de `Boolean` para determinar a expressão resultante correta.</span><span class="sxs-lookup"><span data-stu-id="b6977-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="b6977-124">A função de CASOS avaliar `Boolean_expression` para o QUANDO cada cláusula na ordem especificada, e retornar `result_expression` de primeiro `Boolean_expression` que avalia para `true`.</span><span class="sxs-lookup"><span data-stu-id="b6977-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="b6977-125">As expressões restantes não são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="b6977-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="b6977-126">Se nenhum `Boolean_expression` avalia a `true`, o mecanismo de base de dados retorna `else_result_expression` se uma cláusula OUTRA for especificada, ou um valor nulo se nenhuma cláusula OUTRA é especificado.</span><span class="sxs-lookup"><span data-stu-id="b6977-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="b6977-127">Uma declaração de CASOS não pode retornar um multiset.</span><span class="sxs-lookup"><span data-stu-id="b6977-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6977-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6977-128">Example</span></span>  
 <span data-ttu-id="b6977-129">A seguinte consulta SQL Entity usa a expressão de CASOS para avaliar um conjunto de expressões de `Boolean` para determinar o resultado.</span><span class="sxs-lookup"><span data-stu-id="b6977-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="b6977-130">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b6977-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b6977-131">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="b6977-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b6977-132">Siga o procedimento em [como: Executar uma consulta que retorna os resultados](../how-to-execute-a-query-that-returns-primitivetype-results.md)de primitivatype.</span><span class="sxs-lookup"><span data-stu-id="b6977-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="b6977-133">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="b6977-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="b6977-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6977-134">See also</span></span>

- [<span data-ttu-id="b6977-135">THEN</span><span class="sxs-lookup"><span data-stu-id="b6977-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="b6977-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="b6977-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="b6977-137">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b6977-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
