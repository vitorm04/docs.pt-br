---
title: '&amp;&amp;(E) (Entidade SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eccad616de287a39c42e986cea84dc22feec7f70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150500"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="636ca-102">&amp;&amp;(E) (Entidade SQL)</span><span class="sxs-lookup"><span data-stu-id="636ca-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="636ca-103">Retorna `true` se as duas expressões são `true`; caso contrário, `false` ou `NULL`.</span><span class="sxs-lookup"><span data-stu-id="636ca-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="636ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="636ca-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="636ca-105">ou</span><span class="sxs-lookup"><span data-stu-id="636ca-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="636ca-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="636ca-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="636ca-107">Qualquer expressão válida que retorna um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="636ca-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="636ca-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="636ca-108">Remarks</span></span>  
 <span data-ttu-id="636ca-109">As ampersands duplas (&&) têm a mesma funcionalidade que o operador AND.</span><span class="sxs-lookup"><span data-stu-id="636ca-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="636ca-110">A tabela a seguir mostra valores e tipos de retorno de entrada possíveis.</span><span class="sxs-lookup"><span data-stu-id="636ca-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="636ca-111">TRUE</span><span class="sxs-lookup"><span data-stu-id="636ca-111">TRUE</span></span>|<span data-ttu-id="636ca-112">FALSE</span><span class="sxs-lookup"><span data-stu-id="636ca-112">FALSE</span></span>|<span data-ttu-id="636ca-113">NULO</span><span class="sxs-lookup"><span data-stu-id="636ca-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="636ca-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="636ca-114">FALSE</span></span>|<span data-ttu-id="636ca-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="636ca-115">FALSE</span></span>|<span data-ttu-id="636ca-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="636ca-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="636ca-117">NULO</span><span class="sxs-lookup"><span data-stu-id="636ca-117">NULL</span></span>|<span data-ttu-id="636ca-118">FALSE</span><span class="sxs-lookup"><span data-stu-id="636ca-118">FALSE</span></span>|<span data-ttu-id="636ca-119">NULO</span><span class="sxs-lookup"><span data-stu-id="636ca-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="636ca-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="636ca-120">Example</span></span>  
 <span data-ttu-id="636ca-121">A seguinte consulta SQL Entity demonstra como usar o operador AND.</span><span class="sxs-lookup"><span data-stu-id="636ca-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="636ca-122">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="636ca-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="636ca-123">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="636ca-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="636ca-124">Siga o procedimento em [Como: Executar uma consulta que retorna resultados do tipo estrutural](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="636ca-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="636ca-125">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="636ca-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="636ca-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="636ca-126">See also</span></span>

- [<span data-ttu-id="636ca-127">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="636ca-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
