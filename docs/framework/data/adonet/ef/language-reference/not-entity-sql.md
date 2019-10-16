---
title: '! (NÃO) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 7755219c5238f78e59332c508643fe2ae1f5096f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319526"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="0f862-103">!</span><span class="sxs-lookup"><span data-stu-id="0f862-103">!</span></span> <span data-ttu-id="0f862-104">(NÃO) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0f862-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="0f862-105">Nega uma expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0f862-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f862-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f862-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
``` 
  
## <a name="arguments"></a><span data-ttu-id="0f862-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f862-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="0f862-108">Qualquer expressão válida que retorna um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="0f862-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f862-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f862-109">Remarks</span></span>  
 <span data-ttu-id="0f862-110">O ponto de exclamação (!) tem a mesma funcionalidade que o operador NOT.</span><span class="sxs-lookup"><span data-stu-id="0f862-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f862-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f862-111">Example</span></span>  
 <span data-ttu-id="0f862-112">A seguinte consulta SQL Entity usa o operador NOT nega uma expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0f862-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="0f862-113">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0f862-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0f862-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="0f862-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0f862-115">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0f862-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0f862-116">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="0f862-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="0f862-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f862-117">See also</span></span>

- [<span data-ttu-id="0f862-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0f862-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
