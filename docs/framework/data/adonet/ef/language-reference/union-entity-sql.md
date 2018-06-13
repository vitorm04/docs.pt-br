---
title: UNIÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 52a7a332166250e8fa8084986fd0d89da6fdf42d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764873"
---
# <a name="union-entity-sql"></a><span data-ttu-id="6d513-102">UNIÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6d513-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="6d513-103">Combina os resultados de duas ou mais consultas em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="6d513-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d513-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d513-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d513-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6d513-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6d513-106">Qualquer expressão de consulta válida que retorna uma coleção para combinar com a coleção todas as expressões deve ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.</span><span class="sxs-lookup"><span data-stu-id="6d513-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="6d513-107">UNION</span><span class="sxs-lookup"><span data-stu-id="6d513-107">UNION</span></span>  
 <span data-ttu-id="6d513-108">Especifica que as várias coleções devem ser combinadas e retornado como uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="6d513-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="6d513-109">ALL</span><span class="sxs-lookup"><span data-stu-id="6d513-109">ALL</span></span>  
 <span data-ttu-id="6d513-110">Especifica que as várias coleções devem ser combinadas e retornado como uma única coleção, incluir duplica.</span><span class="sxs-lookup"><span data-stu-id="6d513-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="6d513-111">Se não especificado, as duplicatas são removidas da coleção de resultado.</span><span class="sxs-lookup"><span data-stu-id="6d513-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d513-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6d513-112">Return Value</span></span>  
 <span data-ttu-id="6d513-113">Uma coleção de mesmos tipos ou uma base comum ou um tipo derivado como `expression`.</span><span class="sxs-lookup"><span data-stu-id="6d513-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d513-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d513-114">Remarks</span></span>  
 <span data-ttu-id="6d513-115">UNION é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6d513-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="6d513-116">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="6d513-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="6d513-117">Para obter informações de precedência para o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores de conjunto, consulte [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6d513-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d513-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d513-118">Example</span></span>  
 <span data-ttu-id="6d513-119">A seguinte consulta SQL Entity usa o UNION ALL operador para combinar os resultados das duas consultas em uma única coleção.</span><span class="sxs-lookup"><span data-stu-id="6d513-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="6d513-120">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6d513-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6d513-121">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="6d513-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6d513-122">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6d513-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6d513-123">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="6d513-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="6d513-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d513-124">See Also</span></span>  
 [<span data-ttu-id="6d513-125">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6d513-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
