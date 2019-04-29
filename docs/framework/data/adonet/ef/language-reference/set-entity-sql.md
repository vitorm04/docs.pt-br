---
title: DEFINIR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 4e2a387cf400a881dfd91c61b36ee3ce0f5a4431
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797768"
---
# <a name="set-entity-sql"></a><span data-ttu-id="54e3f-102">DEFINIR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="54e3f-102">SET (Entity SQL)</span></span>
<span data-ttu-id="54e3f-103">A expressão SET é usada para converter uma coleção de objetos em um conjunto rendendo uma nova coleção com todos os elementos duplicados removidos.</span><span class="sxs-lookup"><span data-stu-id="54e3f-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54e3f-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="54e3f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="54e3f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="54e3f-106">Qualquer expressão de consulta válida que retorna uma coleção.</span><span class="sxs-lookup"><span data-stu-id="54e3f-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54e3f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="54e3f-107">Remarks</span></span>  
 <span data-ttu-id="54e3f-108">A expressão de `SET(c)` é logicamente equivalente à instrução select seguinte:</span><span class="sxs-lookup"><span data-stu-id="54e3f-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="54e3f-109">`SET` é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="54e3f-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="54e3f-110">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="54e3f-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="54e3f-111">Ver [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) para obter informações de precedência para a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores definidos.</span><span class="sxs-lookup"><span data-stu-id="54e3f-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54e3f-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54e3f-112">Example</span></span>  
 <span data-ttu-id="54e3f-113">A seguinte consulta SQL Entity usa a expressão SET para converter uma coleção de objetos em um dataset.</span><span class="sxs-lookup"><span data-stu-id="54e3f-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="54e3f-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="54e3f-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="54e3f-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="54e3f-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="54e3f-116">Siga o procedimento em [como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="54e3f-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="54e3f-117">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="54e3f-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="54e3f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54e3f-118">See also</span></span>

- [<span data-ttu-id="54e3f-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="54e3f-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
