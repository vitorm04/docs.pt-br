---
title: USANDO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 9495e5daf88326c5a682172d835c3349fe79e571
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248755"
---
# <a name="using-entity-sql"></a><span data-ttu-id="2cc3c-102">USANDO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2cc3c-102">USING (Entity SQL)</span></span>
<span data-ttu-id="2cc3c-103">Especifica namespaces utilizados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cc3c-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="2cc3c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2cc3c-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="2cc3c-106">Especifica um alias mais curto com o qual qualificar um namespace.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="2cc3c-107">Qualquer namespace válido.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cc3c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cc3c-108">Example</span></span>  
 <span data-ttu-id="2cc3c-109">A consulta Entity SQL a seguir usa o operador USING para especificar namespaces utilizados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="2cc3c-110">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="2cc3c-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2cc3c-111">Siga o procedimento em [como: Executar uma consulta que retorna os resultados](../how-to-execute-a-query-that-returns-primitivetype-results.md)de primitivatype.</span><span class="sxs-lookup"><span data-stu-id="2cc3c-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2cc3c-112">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="2cc3c-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cc3c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cc3c-113">See also</span></span>

- [<span data-ttu-id="2cc3c-114">Namespaces</span><span class="sxs-lookup"><span data-stu-id="2cc3c-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="2cc3c-115">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2cc3c-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
