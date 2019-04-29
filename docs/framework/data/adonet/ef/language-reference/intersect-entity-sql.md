---
title: INTERSECÇÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 85b0abb03161b2df0cfc4ddf6cafc92fb7de9d95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780374"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="ae1a0-102">INTERSECÇÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ae1a0-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="ae1a0-103">Retorna uma coleção de todos os valores diferentes que são retornados pelas expressões de consulta nos lados esquerdo e direito do operando INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="ae1a0-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="ae1a0-104">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.</span><span class="sxs-lookup"><span data-stu-id="ae1a0-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae1a0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae1a0-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae1a0-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae1a0-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ae1a0-107">Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="ae1a0-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae1a0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ae1a0-108">Return Value</span></span>  
 <span data-ttu-id="ae1a0-109">Uma coleção de mesmos tipos ou uma base comum ou um tipo derivado como `expression`.</span><span class="sxs-lookup"><span data-stu-id="ae1a0-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae1a0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae1a0-110">Remarks</span></span>  
 <span data-ttu-id="ae1a0-111">INTERSECT é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ae1a0-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ae1a0-112">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="ae1a0-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ae1a0-113">Para obter informações de precedência para a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] conjunto de operadores, consulte [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ae1a0-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae1a0-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae1a0-114">Example</span></span>  
 <span data-ttu-id="ae1a0-115">A seguinte consulta SQL Entity usa o operador de CRUZAMENTO para retornar uma coleção de todos os valores diferentes que são retornados por expressões de consulta à esquerda e por lados direitos de operando de CRUZAMENTO.</span><span class="sxs-lookup"><span data-stu-id="ae1a0-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="ae1a0-116">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ae1a0-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ae1a0-117">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ae1a0-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ae1a0-118">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ae1a0-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ae1a0-119">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="ae1a0-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="ae1a0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae1a0-120">See also</span></span>

- [<span data-ttu-id="ae1a0-121">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ae1a0-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
