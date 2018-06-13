---
title: '! (NÃO) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 17bc89e6e97b037db035a6f65cd0ec82b840c308
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762056"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="65b54-103">!</span><span class="sxs-lookup"><span data-stu-id="65b54-103">!</span></span> <span data-ttu-id="65b54-104">(NÃO) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="65b54-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="65b54-105">Nega uma expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="65b54-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b54-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65b54-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="65b54-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="65b54-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="65b54-108">Qualquer expressão válida que retorna um valor booleano.</span><span class="sxs-lookup"><span data-stu-id="65b54-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65b54-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="65b54-109">Remarks</span></span>  
 <span data-ttu-id="65b54-110">O ponto de exclamação (!) tem a mesma funcionalidade que o operador NOT.</span><span class="sxs-lookup"><span data-stu-id="65b54-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65b54-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="65b54-111">Example</span></span>  
 <span data-ttu-id="65b54-112">A seguinte consulta SQL Entity usa o operador NOT nega uma expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="65b54-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="65b54-113">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="65b54-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="65b54-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="65b54-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="65b54-115">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="65b54-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="65b54-116">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="65b54-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="65b54-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65b54-117">See Also</span></span>  
 [<span data-ttu-id="65b54-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="65b54-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
