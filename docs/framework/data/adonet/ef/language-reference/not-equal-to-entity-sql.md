---
title: "!= (Não é igual a) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 81643b9a4a1cd49e950010c0023b27108d34180c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="d7be8-102">!= (Não é igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d7be8-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="d7be8-103">Compara duas expressões para determinar se a expressão da esquerda não é igual a expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="d7be8-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="d7be8-104">O operador != (não é igual a) é funcionalmente equivalente ao operador <>.</span><span class="sxs-lookup"><span data-stu-id="d7be8-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7be8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7be8-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7be8-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d7be8-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d7be8-107">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="d7be8-107">Any valid expression.</span></span> <span data-ttu-id="d7be8-108">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="d7be8-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d7be8-109">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="d7be8-109">Result Types</span></span>  
 <span data-ttu-id="d7be8-110">`true` se a expressão da esquerda não for igual à expressão da direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="d7be8-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7be8-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7be8-111">Example</span></span>  
 <span data-ttu-id="d7be8-112">A consulta do Entity SQL usa o operador != para comparar duas expressões para determinar se a expressão da esquerda não é igual à expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="d7be8-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="d7be8-113">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d7be8-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7be8-114">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d7be8-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d7be8-115">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d7be8-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d7be8-116">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="d7be8-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="d7be8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7be8-117">See Also</span></span>  
 [<span data-ttu-id="d7be8-118">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d7be8-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
