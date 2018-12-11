---
title: SOBREPÕE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: f0c5d79b437ff06603ea10404357aa0b3270bc53
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150765"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="8a9fd-102">SOBREPÕE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8a9fd-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="8a9fd-103">Determina se duas coleções têm elementos comuns.</span><span class="sxs-lookup"><span data-stu-id="8a9fd-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a9fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a9fd-104">Syntax</span></span>  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8a9fd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8a9fd-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8a9fd-106">Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="8a9fd-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="8a9fd-107">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.</span><span class="sxs-lookup"><span data-stu-id="8a9fd-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a9fd-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8a9fd-108">Return Value</span></span>  
 <span data-ttu-id="8a9fd-109">`true` se as duas coleções possuem elementos comuns; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="8a9fd-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a9fd-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a9fd-110">Remarks</span></span>  
 <span data-ttu-id="8a9fd-111">OVERLAPS fornecem funcional equivalente ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="8a9fd-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="8a9fd-112">As OVERLAPS são um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8a9fd-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="8a9fd-113">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="8a9fd-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="8a9fd-114">Para obter informações de precedência para a [!INCLUDE[esql](../../../../../../includes/esql-md.md)] conjunto de operadores, consulte [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8a9fd-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a9fd-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a9fd-115">Example</span></span>  
 <span data-ttu-id="8a9fd-116">A seguinte consulta SQL Entity usa as OVERLAPS que o operador determina se duas coleções possuem um valor comum.</span><span class="sxs-lookup"><span data-stu-id="8a9fd-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="8a9fd-117">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8a9fd-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8a9fd-118">Para compilar e executar isso, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="8a9fd-118">To compile and run this, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8a9fd-119">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8a9fd-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8a9fd-120">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="8a9fd-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="8a9fd-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a9fd-121">See Also</span></span>  
 [<span data-ttu-id="8a9fd-122">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8a9fd-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
