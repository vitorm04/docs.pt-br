---
title: '&lt;= (Menor que ou igual a) (Entity SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6b3e6054233074010f46d28e1c5b15d456ae41bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lt-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="91179-102">&lt;= (Menor que ou igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="91179-102">&lt;= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="91179-103">Compara duas expressões para determinar se a expressão da esquerda tem um valor menor que ou igual à expressão da direita.</span><span class="sxs-lookup"><span data-stu-id="91179-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91179-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91179-104">Syntax</span></span>  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="91179-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="91179-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="91179-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="91179-106">Any valid expression.</span></span> <span data-ttu-id="91179-107">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="91179-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="91179-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="91179-108">Result Types</span></span>  
 <span data-ttu-id="91179-109">`true` se a expressão esquerda tem um valor menor ou igual a expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="91179-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91179-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91179-110">Example</span></span>  
 <span data-ttu-id="91179-111">A seguinte consulta SQL Entity usa <= operador de comparação para comparar duas expressões para determinar se a expressão esquerda tem um valor menor ou igual a expressão direita.</span><span class="sxs-lookup"><span data-stu-id="91179-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="91179-112">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="91179-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="91179-113">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="91179-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="91179-114">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="91179-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="91179-115">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="91179-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="91179-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91179-116">See Also</span></span>  
 [<span data-ttu-id="91179-117">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="91179-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
