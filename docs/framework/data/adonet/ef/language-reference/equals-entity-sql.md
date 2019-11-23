---
title: = (Igual a) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 5cdfd35450514a9699a39cf78f64c0fa6b7d5f39
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833846"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="c8328-102">= (Igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c8328-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="c8328-103">Compara a igualdade de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="c8328-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8328-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8328-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8328-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c8328-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c8328-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="c8328-106">Any valid expression.</span></span> <span data-ttu-id="c8328-107">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="c8328-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c8328-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="c8328-108">Result Types</span></span>  
 <span data-ttu-id="c8328-109">`true` se a expressão esquerda é igual à expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="c8328-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8328-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8328-110">Remarks</span></span>  
 <span data-ttu-id="c8328-111">O operador == do é equivalente a =.</span><span class="sxs-lookup"><span data-stu-id="c8328-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8328-112">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c8328-112">Example</span></span>  
 <span data-ttu-id="c8328-113">A seguinte consulta SQL Entity usa = operador de comparação para comparar a igualdade de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="c8328-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="c8328-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c8328-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c8328-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="c8328-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c8328-116">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c8328-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c8328-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="c8328-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="c8328-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8328-118">See also</span></span>

- [<span data-ttu-id="c8328-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c8328-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
