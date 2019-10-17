---
title: < = (menor ou igual a) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: b3c8fef47b06b9fdd0a1619a9e56d3d916d9dd2d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319644"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="1a970-102">\<= (Menor que ou igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1a970-102">\<= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="1a970-103">Compara duas expressões para determinar se a expressão da esquerda tem um valor menor que ou igual à expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="1a970-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a970-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a970-104">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1a970-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1a970-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1a970-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="1a970-106">Any valid expression.</span></span> <span data-ttu-id="1a970-107">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="1a970-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1a970-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="1a970-108">Result Types</span></span>  
 <span data-ttu-id="1a970-109">`true` se a expressão esquerda tem um valor menor ou igual a expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="1a970-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a970-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1a970-110">Example</span></span>  
 <span data-ttu-id="1a970-111">A consulta Entity SQL a seguir usa < = operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor menor ou igual à expressão direita.</span><span class="sxs-lookup"><span data-stu-id="1a970-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="1a970-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1a970-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1a970-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="1a970-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1a970-114">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1a970-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1a970-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="1a970-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="1a970-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a970-116">See also</span></span>

- [<span data-ttu-id="1a970-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1a970-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
