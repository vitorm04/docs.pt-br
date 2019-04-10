---
title: EM (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: d88f79dbfcd27f0ca0d1e26815d7d2bbee731bcf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331267"
---
# <a name="in-entity-sql"></a><span data-ttu-id="0d316-102">EM (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0d316-102">IN (Entity SQL)</span></span>
<span data-ttu-id="0d316-103">Determina se um valor corresponde a qualquer valor em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0d316-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d316-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d316-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0d316-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0d316-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="0d316-106">Qualquer expressão válida que retorna o valor para corresponder.</span><span class="sxs-lookup"><span data-stu-id="0d316-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="0d316-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="0d316-107">[ NOT ]</span></span>  
 <span data-ttu-id="0d316-108">Especifica que o resultado `Boolean` de IN seja negado.</span><span class="sxs-lookup"><span data-stu-id="0d316-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="0d316-109">Qualquer expressão válida que retorna a coleção para testar uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="0d316-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="0d316-110">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `value`.</span><span class="sxs-lookup"><span data-stu-id="0d316-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d316-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0d316-111">Return Value</span></span>  
 `true` <span data-ttu-id="0d316-112">Se o valor for encontrado na coleção; NULL se o valor for nulo ou a coleção é nula. Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0d316-112">if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="0d316-113">Usar NOT IN nega os resultados de IN.</span><span class="sxs-lookup"><span data-stu-id="0d316-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d316-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d316-114">Example</span></span>  
 <span data-ttu-id="0d316-115">A seguinte consulta de Entity SQL usa o operador IN para determinar se um valor corresponde a qualquer valor em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0d316-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="0d316-116">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0d316-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0d316-117">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="0d316-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0d316-118">Siga o procedimento em [como: Executar uma consulta que retorna resultados Structuraltype](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0d316-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0d316-119">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="0d316-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="0d316-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d316-120">See also</span></span>

- [<span data-ttu-id="0d316-121">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0d316-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
