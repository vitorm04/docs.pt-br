---
title: '>= (Maior ou igual a) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 9e1d7e92097713ebdaf15523a5f99f98ed8be0b3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833741"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="a283e-102">> = (maior ou igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a283e-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="a283e-103">Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que ou igual à expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="a283e-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a283e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a283e-104">Syntax</span></span>  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a283e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a283e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a283e-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="a283e-106">Any valid expression.</span></span> <span data-ttu-id="a283e-107">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="a283e-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a283e-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="a283e-108">Result Types</span></span>  
 <span data-ttu-id="a283e-109">`true` se a expressão esquerda tem um valor maior ou igual à expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a283e-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a283e-110">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a283e-110">Example</span></span>  
 <span data-ttu-id="a283e-111">O Entity SQL consulta a seguir usa > = operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor maior ou igual à expressão direita.</span><span class="sxs-lookup"><span data-stu-id="a283e-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="a283e-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a283e-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a283e-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a283e-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a283e-114">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a283e-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a283e-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a283e-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="a283e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a283e-116">See also</span></span>

- [<span data-ttu-id="a283e-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a283e-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
