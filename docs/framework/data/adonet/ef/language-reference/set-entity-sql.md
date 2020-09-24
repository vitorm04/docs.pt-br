---
title: DEFINIR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 2ac7db5b22ad21eb152788b6c6d6a8e65c1f6a7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169629"
---
# <a name="set-entity-sql"></a><span data-ttu-id="32ec9-102">DEFINIR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="32ec9-102">SET (Entity SQL)</span></span>

<span data-ttu-id="32ec9-103">A expressão SET é usada para converter uma coleção de objetos em um conjunto rendendo uma nova coleção com todos os elementos duplicados removidos.</span><span class="sxs-lookup"><span data-stu-id="32ec9-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ec9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32ec9-104">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="32ec9-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="32ec9-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="32ec9-106">Qualquer expressão de consulta válida que retorna uma coleção.</span><span class="sxs-lookup"><span data-stu-id="32ec9-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32ec9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="32ec9-107">Remarks</span></span>  

 <span data-ttu-id="32ec9-108">A expressão de `SET(c)` é logicamente equivalente à instrução select seguinte:</span><span class="sxs-lookup"><span data-stu-id="32ec9-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="32ec9-109">`SET` é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="32ec9-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="32ec9-110">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="32ec9-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="32ec9-111">Consulte [exceto](except-entity-sql.md) para obter informações de precedência para os [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores de conjunto.</span><span class="sxs-lookup"><span data-stu-id="32ec9-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32ec9-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="32ec9-112">Example</span></span>  

 <span data-ttu-id="32ec9-113">A seguinte consulta SQL Entity usa a expressão SET para converter uma coleção de objetos em um dataset.</span><span class="sxs-lookup"><span data-stu-id="32ec9-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="32ec9-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="32ec9-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="32ec9-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="32ec9-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="32ec9-116">Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="32ec9-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="32ec9-117">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="32ec9-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="32ec9-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="32ec9-118">See also</span></span>

- [<span data-ttu-id="32ec9-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="32ec9-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
