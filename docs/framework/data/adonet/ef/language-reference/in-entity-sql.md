---
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: e46db63600b6baa03697615a2f5eb9240f55d15e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833689"
---
# <a name="in-entity-sql"></a><span data-ttu-id="7ffd0-102">IN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7ffd0-102">IN (Entity SQL)</span></span>
<span data-ttu-id="7ffd0-103">Determina se um valor corresponde a qualquer valor em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ffd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ffd0-104">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ffd0-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="7ffd0-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="7ffd0-106">Qualquer expressão válida que retorna o valor para corresponder.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="7ffd0-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="7ffd0-107">[ NOT ]</span></span>  
 <span data-ttu-id="7ffd0-108">Especifica que o resultado `Boolean` de IN seja negado.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="7ffd0-109">Qualquer expressão válida que retorna a coleção para testar uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="7ffd0-110">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `value`.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ffd0-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7ffd0-111">Return Value</span></span>  
 <span data-ttu-id="7ffd0-112">`true` se o valor for encontrado na coleção; nulo se o valor for nulo ou a coleção for nula; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="7ffd0-113">Usar NOT IN nega os resultados de IN.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ffd0-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ffd0-114">Example</span></span>  
 <span data-ttu-id="7ffd0-115">A seguinte consulta de Entity SQL usa o operador IN para determinar se um valor corresponde a qualquer valor em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="7ffd0-116">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7ffd0-117">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="7ffd0-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7ffd0-118">Siga o procedimento em [How para: Executa uma consulta que retorna os resultados de Estruturaistype @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="7ffd0-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7ffd0-119">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="7ffd0-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="7ffd0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ffd0-120">See also</span></span>

- [<span data-ttu-id="7ffd0-121">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7ffd0-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
