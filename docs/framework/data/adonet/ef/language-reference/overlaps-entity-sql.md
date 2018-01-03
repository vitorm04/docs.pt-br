---
title: "SOBREPÕE (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: eb1b495358350bdf2501c56191c2930020930388
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="feb67-102">SOBREPÕE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="feb67-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="feb67-103">Determina se duas coleções têm elementos comuns.</span><span class="sxs-lookup"><span data-stu-id="feb67-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb67-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="feb67-104">Syntax</span></span>  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="feb67-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="feb67-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="feb67-106">Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="feb67-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="feb67-107">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.</span><span class="sxs-lookup"><span data-stu-id="feb67-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="feb67-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="feb67-108">Return Value</span></span>  
 <span data-ttu-id="feb67-109">`true` se as duas coleções possuem elementos comuns; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="feb67-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="feb67-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="feb67-110">Remarks</span></span>  
 <span data-ttu-id="feb67-111">SOBREPOSIÇÕES fornece funcionalmente equivalente à seguinte:</span><span class="sxs-lookup"><span data-stu-id="feb67-111">OVERLAPS provides functionally equivalent tothe following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="feb67-112">As OVERLAPS são um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="feb67-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="feb67-113">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="feb67-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="feb67-114">Para obter informações de precedência para o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores de conjunto, consulte [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="feb67-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="feb67-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="feb67-115">Example</span></span>  
 <span data-ttu-id="feb67-116">A seguinte consulta SQL Entity usa as OVERLAPS que o operador determina se duas coleções possuem um valor comum.</span><span class="sxs-lookup"><span data-stu-id="feb67-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="feb67-117">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="feb67-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="feb67-118">Para compilar e executar isso, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="feb67-118">To compile and run this, follow these steps:</span></span>  
  
1.  <span data-ttu-id="feb67-119">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="feb67-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="feb67-120">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="feb67-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="feb67-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feb67-121">See Also</span></span>  
 [<span data-ttu-id="feb67-122">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="feb67-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
