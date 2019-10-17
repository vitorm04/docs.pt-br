---
title: INTERSECÇÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: dc7338d176302b8683d541ab0dc715dd8d149c6f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319766"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="1294c-102">INTERSECÇÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1294c-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="1294c-103">Retorna uma coleção de todos os valores diferentes que são retornados pelas expressões de consulta nos lados esquerdo e direito do operando INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="1294c-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="1294c-104">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.</span><span class="sxs-lookup"><span data-stu-id="1294c-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1294c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1294c-105">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1294c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="1294c-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1294c-107">Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="1294c-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1294c-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1294c-108">Return Value</span></span>  
 <span data-ttu-id="1294c-109">Uma coleção de mesmos tipos ou uma base comum ou um tipo derivado como `expression`.</span><span class="sxs-lookup"><span data-stu-id="1294c-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1294c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1294c-110">Remarks</span></span>  
 <span data-ttu-id="1294c-111">INTERSECT é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1294c-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1294c-112">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="1294c-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1294c-113">Para obter informações de precedência para os operadores de conjunto [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consulte [Except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1294c-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1294c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1294c-114">Example</span></span>  
 <span data-ttu-id="1294c-115">A seguinte consulta SQL Entity usa o operador de CRUZAMENTO para retornar uma coleção de todos os valores diferentes que são retornados por expressões de consulta à esquerda e por lados direitos de operando de CRUZAMENTO.</span><span class="sxs-lookup"><span data-stu-id="1294c-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="1294c-116">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1294c-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1294c-117">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="1294c-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1294c-118">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1294c-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1294c-119">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="1294c-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="1294c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1294c-120">See also</span></span>

- [<span data-ttu-id="1294c-121">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1294c-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
