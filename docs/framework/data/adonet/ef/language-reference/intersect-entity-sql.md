---
title: INTERSECÇÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: a943de89de37d00cc2a643b443da7ef1fd3380b9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250599"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="dd0b1-102">INTERSECÇÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dd0b1-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="dd0b1-103">Retorna uma coleção de todos os valores diferentes que são retornados pelas expressões de consulta nos lados esquerdo e direito do operando INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="dd0b1-104">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd0b1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd0b1-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="dd0b1-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="dd0b1-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="dd0b1-107">Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd0b1-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dd0b1-108">Return Value</span></span>  
 <span data-ttu-id="dd0b1-109">Uma coleção de mesmos tipos ou uma base comum ou um tipo derivado como `expression`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd0b1-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd0b1-110">Remarks</span></span>  
 <span data-ttu-id="dd0b1-111">INTERSECT é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dd0b1-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="dd0b1-112">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="dd0b1-113">Para obter informações de precedência para os operadores de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] conjunto, consulte [Except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd0b1-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dd0b1-114">Example</span></span>  
 <span data-ttu-id="dd0b1-115">A seguinte consulta SQL Entity usa o operador de CRUZAMENTO para retornar uma coleção de todos os valores diferentes que são retornados por expressões de consulta à esquerda e por lados direitos de operando de CRUZAMENTO.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="dd0b1-116">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dd0b1-117">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="dd0b1-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dd0b1-118">Siga o procedimento em [como: Executar uma consulta que retorna resultados](../how-to-execute-a-query-that-returns-structuraltype-results.md)de estruturaistype.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="dd0b1-119">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="dd0b1-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="dd0b1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd0b1-120">See also</span></span>

- [<span data-ttu-id="dd0b1-121">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="dd0b1-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
