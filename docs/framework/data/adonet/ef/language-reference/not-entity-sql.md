---
title: '! (NÃO) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0eb9be9ed4cbce45a51d15eea68e9fb1a26f0107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191834"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="bdb6d-103">!</span><span class="sxs-lookup"><span data-stu-id="bdb6d-103">!</span></span> <span data-ttu-id="bdb6d-104">(NÃO) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bdb6d-104">(NOT) (Entity SQL)</span></span>

<span data-ttu-id="bdb6d-105">Nega uma expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="bdb6d-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb6d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdb6d-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="bdb6d-107">Argumentos</span><span class="sxs-lookup"><span data-stu-id="bdb6d-107">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="bdb6d-108">Qualquer expressão válida que retorna um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="bdb6d-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdb6d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdb6d-109">Remarks</span></span>  

 <span data-ttu-id="bdb6d-110">O ponto de exclamação (!) tem a mesma funcionalidade que o operador NOT.</span><span class="sxs-lookup"><span data-stu-id="bdb6d-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdb6d-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bdb6d-111">Example</span></span>  

 <span data-ttu-id="bdb6d-112">A seguinte consulta SQL Entity usa o operador NOT nega uma expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="bdb6d-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="bdb6d-113">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bdb6d-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bdb6d-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="bdb6d-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bdb6d-115">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bdb6d-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bdb6d-116">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="bdb6d-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="bdb6d-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="bdb6d-117">See also</span></span>

- [<span data-ttu-id="bdb6d-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bdb6d-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
