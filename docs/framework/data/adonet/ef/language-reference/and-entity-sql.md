---
title: '&amp;&amp; (AND) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 6ee7987f2801a35fb9669472ce7b237e684f64e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579661"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="32317-102">&amp;&amp; (AND) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="32317-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="32317-103">Retorna `true` se as duas expressões são `true`; caso contrário, `false` ou `NULL`.</span><span class="sxs-lookup"><span data-stu-id="32317-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32317-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32317-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="32317-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="32317-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="32317-106">Qualquer expressão válida que retorna um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="32317-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32317-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="32317-107">Remarks</span></span>  
 <span data-ttu-id="32317-108">Os E comercial duplas (&&) têm a mesma funcionalidade que o operador AND.</span><span class="sxs-lookup"><span data-stu-id="32317-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="32317-109">A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.</span><span class="sxs-lookup"><span data-stu-id="32317-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="32317-110">TRUE</span><span class="sxs-lookup"><span data-stu-id="32317-110">TRUE</span></span>|<span data-ttu-id="32317-111">FALSE</span><span class="sxs-lookup"><span data-stu-id="32317-111">FALSE</span></span>|<span data-ttu-id="32317-112">NULL</span><span class="sxs-lookup"><span data-stu-id="32317-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="32317-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="32317-113">FALSE</span></span>|<span data-ttu-id="32317-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="32317-114">FALSE</span></span>|<span data-ttu-id="32317-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="32317-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="32317-116">NULL</span><span class="sxs-lookup"><span data-stu-id="32317-116">NULL</span></span>|<span data-ttu-id="32317-117">FALSE</span><span class="sxs-lookup"><span data-stu-id="32317-117">FALSE</span></span>|<span data-ttu-id="32317-118">NULL</span><span class="sxs-lookup"><span data-stu-id="32317-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="32317-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="32317-119">Example</span></span>  
 <span data-ttu-id="32317-120">A seguinte consulta SQL Entity demonstra como usar o operador AND.</span><span class="sxs-lookup"><span data-stu-id="32317-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="32317-121">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="32317-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="32317-122">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="32317-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="32317-123">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="32317-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="32317-124">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="32317-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="32317-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32317-125">See also</span></span>
- [<span data-ttu-id="32317-126">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="32317-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
