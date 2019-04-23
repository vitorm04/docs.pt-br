---
title: EXCETO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 32b5148e43a38e5cf8dcce0ae16260d7a6b6a018
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341212"
---
# <a name="except-entity-sql"></a><span data-ttu-id="72931-102">EXCETO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="72931-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="72931-103">Retorna uma coleção de todos os valores distintos da expressão de consulta para a esquerda do operando EXCEPT que também não são retornados da expressão de consulta à direita do operando EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="72931-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="72931-104">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `expression`.</span><span class="sxs-lookup"><span data-stu-id="72931-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72931-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72931-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="72931-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="72931-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="72931-107">Qualquer expressão de consulta válida que retornar uma coleção para comparar com a coleção retornada de outra expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="72931-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72931-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="72931-108">Return Value</span></span>  
 <span data-ttu-id="72931-109">Uma coleção de mesmos tipos ou uma base comum ou um tipo derivado como `expression`.</span><span class="sxs-lookup"><span data-stu-id="72931-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72931-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="72931-110">Remarks</span></span>  
 <span data-ttu-id="72931-111">EXCETO é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="72931-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="72931-112">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="72931-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="72931-113">A tabela a seguir mostra a precedência de operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="72931-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="72931-114">Precedência</span><span class="sxs-lookup"><span data-stu-id="72931-114">Precedence</span></span>|<span data-ttu-id="72931-115">Operadores</span><span class="sxs-lookup"><span data-stu-id="72931-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="72931-116">O mais alto</span><span class="sxs-lookup"><span data-stu-id="72931-116">Highest</span></span>|<span data-ttu-id="72931-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="72931-117">INTERSECT</span></span>|  
||<span data-ttu-id="72931-118">UNION</span><span class="sxs-lookup"><span data-stu-id="72931-118">UNION</span></span><br /><br /> <span data-ttu-id="72931-119">TODOS UNION</span><span class="sxs-lookup"><span data-stu-id="72931-119">UNION ALL</span></span>|  
||<span data-ttu-id="72931-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="72931-120">EXCEPT</span></span>|  
|<span data-ttu-id="72931-121">O menor</span><span class="sxs-lookup"><span data-stu-id="72931-121">Lowest</span></span>|<span data-ttu-id="72931-122">EXISTE</span><span class="sxs-lookup"><span data-stu-id="72931-122">EXISTS</span></span><br /><br /> <span data-ttu-id="72931-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="72931-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="72931-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="72931-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="72931-125">SET</span><span class="sxs-lookup"><span data-stu-id="72931-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="72931-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72931-126">Example</span></span>  
 <span data-ttu-id="72931-127">A seguinte consulta SQL Entity usa A QUE operador NOT SER para retornar uma coleção de todos os valores diferentes de duas expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="72931-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="72931-128">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="72931-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="72931-129">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="72931-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="72931-130">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="72931-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="72931-131">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="72931-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="72931-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72931-132">See also</span></span>

- [<span data-ttu-id="72931-133">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="72931-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
