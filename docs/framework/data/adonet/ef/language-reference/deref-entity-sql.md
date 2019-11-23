---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833901"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="2cbd3-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2cbd3-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="2cbd3-103">Desreferencia um valor de referência e gera o resultado dessa desreferência.</span><span class="sxs-lookup"><span data-stu-id="2cbd3-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbd3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cbd3-104">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="2cbd3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2cbd3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2cbd3-106">Qualquer expressão de consulta válida que retorna uma coleção.</span><span class="sxs-lookup"><span data-stu-id="2cbd3-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cbd3-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2cbd3-107">Return Value</span></span>  
 <span data-ttu-id="2cbd3-108">O valor de entidade que é referenciada.</span><span class="sxs-lookup"><span data-stu-id="2cbd3-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cbd3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2cbd3-109">Remarks</span></span>  
 <span data-ttu-id="2cbd3-110">O operador de DEREF desreferencia um valor de referência e gerencia o resultado do desreferencia.</span><span class="sxs-lookup"><span data-stu-id="2cbd3-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="2cbd3-111">Por exemplo, se `r` for uma referência de tipo ref\<T >, `Deref(r)` será uma expressão do tipo `T` que produz a entidade referenciada por `r`.</span><span class="sxs-lookup"><span data-stu-id="2cbd3-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="2cbd3-112">Se o valor de referência é zero, ou está oscilando (isto é, o destino de referência não existir), o resultado do operador de DEREF é nulo.</span><span class="sxs-lookup"><span data-stu-id="2cbd3-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cbd3-113">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2cbd3-113">Example</span></span>  
 <span data-ttu-id="2cbd3-114">A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de DEREF para desreferenciar um valor de referência e para gerar o resultado do desreferenciar.</span><span class="sxs-lookup"><span data-stu-id="2cbd3-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="2cbd3-115">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2cbd3-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2cbd3-116">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2cbd3-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2cbd3-117">Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2cbd3-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2cbd3-118">Passe a seguinte consulta como um argumento para o método de ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="2cbd3-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="2cbd3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cbd3-119">See also</span></span>

- [<span data-ttu-id="2cbd3-120">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2cbd3-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2cbd3-121">REF</span><span class="sxs-lookup"><span data-stu-id="2cbd3-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="2cbd3-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="2cbd3-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="2cbd3-123">KEY</span><span class="sxs-lookup"><span data-stu-id="2cbd3-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="2cbd3-124">Tipos estruturados anulável</span><span class="sxs-lookup"><span data-stu-id="2cbd3-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
