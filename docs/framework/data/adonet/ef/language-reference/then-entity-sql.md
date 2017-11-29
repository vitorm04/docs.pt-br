---
title: "ENTÃO (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 99fd941c963ff87203d7b315beb606d40001224d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="then-entity-sql"></a><span data-ttu-id="3e434-102">ENTÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3e434-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="3e434-103">O resultado de QUANDO cláusula quando avaliar a `true`.</span><span class="sxs-lookup"><span data-stu-id="3e434-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e434-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e434-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e434-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3e434-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="3e434-106">Qualquer expressão boolean válido.</span><span class="sxs-lookup"><span data-stu-id="3e434-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="3e434-107">Qualquer expressão de consulta válida que retorna uma coleção.</span><span class="sxs-lookup"><span data-stu-id="3e434-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e434-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e434-108">Remarks</span></span>  
 <span data-ttu-id="3e434-109">Se `when_expression` avalia para o valor `true`, o resultado é `then-expression`correspondente.</span><span class="sxs-lookup"><span data-stu-id="3e434-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="3e434-110">Se nenhum de QUANDO as condições sejam atendidas, `else-expression` é avaliado.</span><span class="sxs-lookup"><span data-stu-id="3e434-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="3e434-111">No entanto, se não há `else-expression`, o resultado é nulo.</span><span class="sxs-lookup"><span data-stu-id="3e434-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="3e434-112">Para obter um exemplo, consulte [caso](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3e434-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e434-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e434-113">Example</span></span>  
 <span data-ttu-id="3e434-114">A seguinte consulta SQL Entity usa a expressão de CASOS para avaliar um conjunto de expressões de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="3e434-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="3e434-115">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3e434-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3e434-116">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="3e434-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3e434-117">Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3e434-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="3e434-118">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="3e434-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="3e434-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e434-119">See Also</span></span>  
 [<span data-ttu-id="3e434-120">CASO</span><span class="sxs-lookup"><span data-stu-id="3e434-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [<span data-ttu-id="3e434-121">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3e434-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
