---
title: '>= (Maior que ou igual a) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: b5a8a834c325cca38e2c106ca3f8ee829dd699b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034145"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="a77f5-102">> = (maior que ou igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a77f5-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="a77f5-103">Compara duas expressões para determinar se a expressão da esquerda tem um valor maior que ou igual à expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="a77f5-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a77f5-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a77f5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a77f5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a77f5-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="a77f5-106">Any valid expression.</span></span> <span data-ttu-id="a77f5-107">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="a77f5-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a77f5-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="a77f5-108">Result Types</span></span>  
 <span data-ttu-id="a77f5-109">`true` se a expressão esquerda tem um valor maior ou igual a expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a77f5-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a77f5-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a77f5-110">Example</span></span>  
 <span data-ttu-id="a77f5-111">A seguinte consulta SQL Entity usa > = operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor maior que ou igual à expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="a77f5-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="a77f5-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a77f5-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a77f5-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a77f5-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a77f5-114">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a77f5-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a77f5-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a77f5-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="a77f5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a77f5-116">See also</span></span>

- [<span data-ttu-id="a77f5-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a77f5-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
