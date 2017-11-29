---
title: = (Igual a) (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 12de808403ee6714d2bcfd15da4e67a8596e1ff1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="33afc-102">= (Igual a) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="33afc-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="33afc-103">Compara a igualdade de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="33afc-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33afc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33afc-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="33afc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="33afc-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="33afc-106">Qualquer expressão válida.</span><span class="sxs-lookup"><span data-stu-id="33afc-106">Any valid expression.</span></span> <span data-ttu-id="33afc-107">As duas expressões devem ter os tipos de dados implicitamente conversíveis.</span><span class="sxs-lookup"><span data-stu-id="33afc-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="33afc-108">Tipos de resultado</span><span class="sxs-lookup"><span data-stu-id="33afc-108">Result Types</span></span>  
 <span data-ttu-id="33afc-109">`true` se a expressão esquerda é igual a expressão direita; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="33afc-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33afc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="33afc-110">Remarks</span></span>  
 <span data-ttu-id="33afc-111">O operador == do é equivalente a =.</span><span class="sxs-lookup"><span data-stu-id="33afc-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33afc-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33afc-112">Example</span></span>  
 <span data-ttu-id="33afc-113">A seguinte consulta SQL Entity usa = operador de comparação para comparar a igualdade de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="33afc-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="33afc-114">A consulta é baseada no modelo de vendas AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="33afc-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="33afc-115">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="33afc-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="33afc-116">Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="33afc-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="33afc-117">Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="33afc-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="33afc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33afc-118">See Also</span></span>  
 [<span data-ttu-id="33afc-119">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="33afc-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
