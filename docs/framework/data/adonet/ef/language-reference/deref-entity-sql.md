---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 57f7c61d8e4de2a63708ef6d4437ca53de854af9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116852"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="509d0-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="509d0-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="509d0-103">Desreferencia um valor de referência e gera o resultado dessa desreferência.</span><span class="sxs-lookup"><span data-stu-id="509d0-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="509d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="509d0-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="509d0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="509d0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="509d0-106">Qualquer expressão de consulta válida que retorna uma coleção.</span><span class="sxs-lookup"><span data-stu-id="509d0-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="509d0-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="509d0-107">Return Value</span></span>  
 <span data-ttu-id="509d0-108">O valor de entidade que é referenciada.</span><span class="sxs-lookup"><span data-stu-id="509d0-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="509d0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="509d0-109">Remarks</span></span>  
 <span data-ttu-id="509d0-110">O operador de DEREF desreferencia um valor de referência e gerencia o resultado do desreferencia.</span><span class="sxs-lookup"><span data-stu-id="509d0-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="509d0-111">Por exemplo, se `r` é uma referência de tipo de ref\<T >, `Deref(r)` é uma expressão do tipo `T` que produz a entidade referenciada por `r`.</span><span class="sxs-lookup"><span data-stu-id="509d0-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="509d0-112">Se o valor de referência é zero, ou está oscilando (isto é, o destino de referência não existir), o resultado do operador de DEREF é nulo.</span><span class="sxs-lookup"><span data-stu-id="509d0-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="509d0-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="509d0-113">Example</span></span>  
 <span data-ttu-id="509d0-114">A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador de DEREF para desreferenciar um valor de referência e para gerar o resultado do desreferenciar.</span><span class="sxs-lookup"><span data-stu-id="509d0-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="509d0-115">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="509d0-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="509d0-116">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="509d0-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="509d0-117">Siga o procedimento em [como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="509d0-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="509d0-118">Passe a seguinte consulta como um argumento para o método de ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="509d0-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="509d0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="509d0-119">See also</span></span>

- [<span data-ttu-id="509d0-120">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="509d0-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="509d0-121">REF</span><span class="sxs-lookup"><span data-stu-id="509d0-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="509d0-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="509d0-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="509d0-123">KEY</span><span class="sxs-lookup"><span data-stu-id="509d0-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="509d0-124">Tipos estruturados que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="509d0-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
