---
title: '!= (Não é igual a) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: bebe85072f5a2cf6a133b88c6d3f5c97299aa63f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191769"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="15d32-102">!= (Não é igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="15d32-102">!= (Not Equal To) (Entity SQL)</span></span>

<span data-ttu-id="15d32-103">Compara duas expressões para determinar se a expressão da esquerda não é igual a expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="15d32-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="15d32-104">O operador! = (diferente de) é funcionalmente equivalente ao operador de <> .</span><span class="sxs-lookup"><span data-stu-id="15d32-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d32-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15d32-105">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="15d32-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="15d32-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="15d32-107">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="15d32-107">Any valid expression.</span></span> <span data-ttu-id="15d32-108">Ambas as expressões devem ter tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="15d32-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="15d32-109">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="15d32-109">Result Types</span></span>  

 <span data-ttu-id="15d32-110">`true` se a expressão da esquerda não for igual à expressão da direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="15d32-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15d32-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15d32-111">Example</span></span>  

 <span data-ttu-id="15d32-112">A consulta do Entity SQL usa o operador != para comparar duas expressões para determinar se a expressão da esquerda não é igual à expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="15d32-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="15d32-113">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="15d32-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="15d32-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="15d32-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="15d32-115">Siga o procedimento em [como executar uma consulta que retorna resultados de estruturaistype](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="15d32-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="15d32-116">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="15d32-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="15d32-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="15d32-117">See also</span></span>

- [<span data-ttu-id="15d32-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="15d32-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
