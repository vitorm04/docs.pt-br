---
title: '&amp;&amp;E (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 02e404b73e5a9a9c3963e2d2b58ab7592afabc13
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251308"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="b0258-102">&amp;&amp;E (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b0258-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="b0258-103">Retorna `true` se as duas expressões são `true`; caso contrário, `false` ou `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b0258-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0258-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0258-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b0258-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b0258-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="b0258-106">Qualquer expressão válida que retorna um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="b0258-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0258-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0258-107">Remarks</span></span>  
 <span data-ttu-id="b0258-108">O e comercial duplo (& &) têm a mesma funcionalidade que o operador AND.</span><span class="sxs-lookup"><span data-stu-id="b0258-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="b0258-109">A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.</span><span class="sxs-lookup"><span data-stu-id="b0258-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="b0258-110">TRUE</span><span class="sxs-lookup"><span data-stu-id="b0258-110">TRUE</span></span>|<span data-ttu-id="b0258-111">FALSE</span><span class="sxs-lookup"><span data-stu-id="b0258-111">FALSE</span></span>|<span data-ttu-id="b0258-112">NULL</span><span class="sxs-lookup"><span data-stu-id="b0258-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="b0258-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="b0258-113">FALSE</span></span>|<span data-ttu-id="b0258-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="b0258-114">FALSE</span></span>|<span data-ttu-id="b0258-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="b0258-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="b0258-116">NULL</span><span class="sxs-lookup"><span data-stu-id="b0258-116">NULL</span></span>|<span data-ttu-id="b0258-117">FALSE</span><span class="sxs-lookup"><span data-stu-id="b0258-117">FALSE</span></span>|<span data-ttu-id="b0258-118">NULL</span><span class="sxs-lookup"><span data-stu-id="b0258-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b0258-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0258-119">Example</span></span>  
 <span data-ttu-id="b0258-120">A seguinte consulta SQL Entity demonstra como usar o operador AND.</span><span class="sxs-lookup"><span data-stu-id="b0258-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="b0258-121">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b0258-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b0258-122">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="b0258-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b0258-123">Siga o procedimento em [como: Executar uma consulta que retorna resultados](../how-to-execute-a-query-that-returns-structuraltype-results.md)de estruturaistype.</span><span class="sxs-lookup"><span data-stu-id="b0258-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b0258-124">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="b0258-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="b0258-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0258-125">See also</span></span>

- [<span data-ttu-id="b0258-126">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0258-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
