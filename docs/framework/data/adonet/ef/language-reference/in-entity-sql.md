---
title: EM (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d32e5012b4acbf0ecd6830f549de5dccf79bb38b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="in-entity-sql"></a><span data-ttu-id="deaf6-102">EM (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="deaf6-102">IN (Entity SQL)</span></span>
<span data-ttu-id="deaf6-103">Determina se um valor corresponde a qualquer valor em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="deaf6-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deaf6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="deaf6-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="deaf6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="deaf6-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="deaf6-106">Qualquer expressão válida que retorna o valor para corresponder.</span><span class="sxs-lookup"><span data-stu-id="deaf6-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="deaf6-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="deaf6-107">[ NOT ]</span></span>  
 <span data-ttu-id="deaf6-108">Especifica que o resultado `Boolean` de IN seja negado.</span><span class="sxs-lookup"><span data-stu-id="deaf6-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="deaf6-109">Qualquer expressão válida que retorna a coleção para testar uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="deaf6-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="deaf6-110">Todas as expressões devem ser do mesmo tipo ou de uma base comum ou um tipo derivado que `value`.</span><span class="sxs-lookup"><span data-stu-id="deaf6-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="deaf6-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="deaf6-111">Return Value</span></span>  
 <span data-ttu-id="deaf6-112">`true` se o valor for encontrado na coleção; nulo se o valor for nulo ou a coleção for nula; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="deaf6-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="deaf6-113">Usar NOT IN nega os resultados de IN.</span><span class="sxs-lookup"><span data-stu-id="deaf6-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="deaf6-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="deaf6-114">Example</span></span>  
 <span data-ttu-id="deaf6-115">A seguinte consulta de Entity SQL usa o operador IN para determinar se um valor corresponde a qualquer valor em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="deaf6-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="deaf6-116">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="deaf6-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="deaf6-117">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="deaf6-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="deaf6-118">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="deaf6-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="deaf6-119">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="deaf6-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="deaf6-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="deaf6-120">See Also</span></span>  
 [<span data-ttu-id="deaf6-121">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="deaf6-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
