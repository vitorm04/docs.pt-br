---
title: EXCETO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: c4df8c2b72ee60a425c98c64a13a1e2d43d4506e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833858"
---
# <a name="except-entity-sql"></a><span data-ttu-id="a8e82-102">EXCETO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a8e82-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="a8e82-103">Retorna uma coleção de todos os valores distintos da expressão de consulta para a esquerda do operando EXCEPT que também não são retornados da expressão de consulta à direita do operando EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="a8e82-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="a8e82-104">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.</span><span class="sxs-lookup"><span data-stu-id="a8e82-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e82-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8e82-105">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a8e82-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="a8e82-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a8e82-107">Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="a8e82-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8e82-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a8e82-108">Return Value</span></span>  
 <span data-ttu-id="a8e82-109">Uma coleção de mesmos tipos ou uma base comum ou um tipo derivado como `expression`.</span><span class="sxs-lookup"><span data-stu-id="a8e82-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8e82-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8e82-110">Remarks</span></span>  
 <span data-ttu-id="a8e82-111">EXCETO é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a8e82-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="a8e82-112">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="a8e82-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="a8e82-113">A tabela a seguir mostra a precedência de operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a8e82-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="a8e82-114">Precedência</span><span class="sxs-lookup"><span data-stu-id="a8e82-114">Precedence</span></span>|<span data-ttu-id="a8e82-115">Operadores</span><span class="sxs-lookup"><span data-stu-id="a8e82-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="a8e82-116">O mais alto</span><span class="sxs-lookup"><span data-stu-id="a8e82-116">Highest</span></span>|<span data-ttu-id="a8e82-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="a8e82-117">INTERSECT</span></span>|  
||<span data-ttu-id="a8e82-118">UNION</span><span class="sxs-lookup"><span data-stu-id="a8e82-118">UNION</span></span><br /><br /> <span data-ttu-id="a8e82-119">TODOS UNION</span><span class="sxs-lookup"><span data-stu-id="a8e82-119">UNION ALL</span></span>|  
||<span data-ttu-id="a8e82-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="a8e82-120">EXCEPT</span></span>|  
|<span data-ttu-id="a8e82-121">O menor</span><span class="sxs-lookup"><span data-stu-id="a8e82-121">Lowest</span></span>|<span data-ttu-id="a8e82-122">EXISTE</span><span class="sxs-lookup"><span data-stu-id="a8e82-122">EXISTS</span></span><br /><br /> <span data-ttu-id="a8e82-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="a8e82-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="a8e82-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="a8e82-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="a8e82-125">SET</span><span class="sxs-lookup"><span data-stu-id="a8e82-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a8e82-126">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a8e82-126">Example</span></span>  
 <span data-ttu-id="a8e82-127">A seguinte consulta SQL Entity usa A QUE operador NOT SER para retornar uma coleção de todos os valores diferentes de duas expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="a8e82-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="a8e82-128">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a8e82-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a8e82-129">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a8e82-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a8e82-130">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a8e82-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a8e82-131">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a8e82-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="a8e82-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8e82-132">See also</span></span>

- [<span data-ttu-id="a8e82-133">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a8e82-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
