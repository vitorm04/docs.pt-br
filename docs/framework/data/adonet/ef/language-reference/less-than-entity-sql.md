---
title: < (Menor que) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 1ca1cbdf1282782295b659393e8f54aae3ec5649
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320438"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="d3427-102">\< (Menor que) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d3427-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="d3427-103">Compara duas expressões para determinar se a expressão da esquerda tem um valor menor que a expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="d3427-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3427-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3427-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3427-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d3427-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d3427-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="d3427-106">Any valid expression.</span></span> <span data-ttu-id="d3427-107">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="d3427-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d3427-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="d3427-108">Result Types</span></span>  
 <span data-ttu-id="d3427-109">`true` se a expressão esquerda tem um valor menor do que a expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="d3427-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3427-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3427-110">Example</span></span>  
 <span data-ttu-id="d3427-111">A seguinte consulta SQL Entity usa < o operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor menor que a expressão direita.</span><span class="sxs-lookup"><span data-stu-id="d3427-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="d3427-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d3427-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d3427-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d3427-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d3427-114">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d3427-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d3427-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="d3427-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="d3427-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3427-116">See also</span></span>

- [<span data-ttu-id="d3427-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d3427-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
