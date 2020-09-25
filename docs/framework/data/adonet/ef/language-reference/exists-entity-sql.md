---
title: EXISTE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: f08b3ea60a985e56e05e4686cd531f94e0bd4e18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166762"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="6798b-102">EXISTE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6798b-102">EXISTS (Entity SQL)</span></span>

<span data-ttu-id="6798b-103">Determina se uma coleção está vazia.</span><span class="sxs-lookup"><span data-stu-id="6798b-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6798b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6798b-104">Syntax</span></span>  
  
```sql  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="6798b-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="6798b-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="6798b-106">Qualquer expressão válida que retorna uma coleção.</span><span class="sxs-lookup"><span data-stu-id="6798b-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="6798b-107">NOT</span><span class="sxs-lookup"><span data-stu-id="6798b-107">NOT</span></span>  
 <span data-ttu-id="6798b-108">Especifica que o resultado EXISTS seja negado.</span><span class="sxs-lookup"><span data-stu-id="6798b-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6798b-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="6798b-109">Return Value</span></span>  

 <span data-ttu-id="6798b-110">`true` se a coleção é não vazio; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6798b-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6798b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6798b-111">Remarks</span></span>  

 <span data-ttu-id="6798b-112">EXISTS é um dos operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6798b-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="6798b-113">Todos os operadores definidos [!INCLUDE[esql](../../../../../../includes/esql-md.md)] são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="6798b-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="6798b-114">Para obter informações de precedência para os [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operadores de conjunto, consulte [Except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6798b-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6798b-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6798b-115">Example</span></span>  

 <span data-ttu-id="6798b-116">A seguinte consulta SQL Entity usa EXISTE operador para determinar se a coleção está vazia.</span><span class="sxs-lookup"><span data-stu-id="6798b-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="6798b-117">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6798b-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6798b-118">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="6798b-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6798b-119">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6798b-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6798b-120">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="6798b-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXISTS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="6798b-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="6798b-121">See also</span></span>

- [<span data-ttu-id="6798b-122">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6798b-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
