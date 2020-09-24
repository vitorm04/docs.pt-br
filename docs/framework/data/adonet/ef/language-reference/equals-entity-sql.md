---
title: = (Igual a) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 31299670d9f47ed7672b980a3415b8d214463b8e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148081"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="f3297-102">= (Igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f3297-102">= (Equals) (Entity SQL)</span></span>

<span data-ttu-id="f3297-103">Compara a igualdade de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="f3297-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3297-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3297-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3297-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f3297-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="f3297-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="f3297-106">Any valid expression.</span></span> <span data-ttu-id="f3297-107">Ambas as expressões devem ter tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="f3297-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f3297-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="f3297-108">Result Types</span></span>  

 <span data-ttu-id="f3297-109">`true` se a expressão esquerda é igual a expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f3297-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3297-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3297-110">Remarks</span></span>  

 <span data-ttu-id="f3297-111">O operador == do é equivalente a =.</span><span class="sxs-lookup"><span data-stu-id="f3297-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3297-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3297-112">Example</span></span>  

 <span data-ttu-id="f3297-113">A seguinte consulta SQL Entity usa = operador de comparação para comparar a igualdade de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="f3297-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="f3297-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f3297-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f3297-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="f3297-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f3297-116">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f3297-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f3297-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="f3297-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="f3297-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f3297-118">See also</span></span>

- [<span data-ttu-id="f3297-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f3297-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
