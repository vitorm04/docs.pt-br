---
title: USANDO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 0bcd4a2140a04fa0ecbfa7eee450ed029f278286
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319215"
---
# <a name="using-entity-sql"></a><span data-ttu-id="4cd0e-102">USANDO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4cd0e-102">USING (Entity SQL)</span></span>
<span data-ttu-id="4cd0e-103">Especifica namespaces utilizados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="4cd0e-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4cd0e-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="4cd0e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4cd0e-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="4cd0e-106">Especifica um alias mais curto com o qual qualificar um namespace.</span><span class="sxs-lookup"><span data-stu-id="4cd0e-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="4cd0e-107">Qualquer namespace válido.</span><span class="sxs-lookup"><span data-stu-id="4cd0e-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cd0e-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4cd0e-108">Example</span></span>  
 <span data-ttu-id="4cd0e-109">A consulta Entity SQL a seguir usa o operador USING para especificar namespaces utilizados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="4cd0e-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="4cd0e-110">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="4cd0e-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4cd0e-111">Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4cd0e-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="4cd0e-112">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="4cd0e-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cd0e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4cd0e-113">See also</span></span>

- [<span data-ttu-id="4cd0e-114">Namespaces</span><span class="sxs-lookup"><span data-stu-id="4cd0e-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="4cd0e-115">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4cd0e-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
