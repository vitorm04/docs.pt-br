---
title: = (Igual a) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: bda314208a25426be321ba307be96067b1df2ac8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761393"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="213c3-102">= (Igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="213c3-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="213c3-103">Compara a igualdade de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="213c3-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="213c3-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="213c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="213c3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="213c3-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="213c3-106">Any valid expression.</span></span> <span data-ttu-id="213c3-107">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="213c3-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="213c3-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="213c3-108">Result Types</span></span>  
 <span data-ttu-id="213c3-109">`true` se a expressão esquerda é igual a expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="213c3-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="213c3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="213c3-110">Remarks</span></span>  
 <span data-ttu-id="213c3-111">O operador == do é equivalente a =.</span><span class="sxs-lookup"><span data-stu-id="213c3-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="213c3-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="213c3-112">Example</span></span>  
 <span data-ttu-id="213c3-113">A seguinte consulta SQL Entity usa = operador de comparação para comparar a igualdade de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="213c3-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="213c3-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="213c3-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="213c3-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="213c3-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="213c3-116">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="213c3-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="213c3-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="213c3-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="213c3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="213c3-118">See Also</span></span>  
 [<span data-ttu-id="213c3-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="213c3-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
