---
title: USANDO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: bdab81ed8acae5e757de0a669922dc79d0303ee4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203586"
---
# <a name="using-entity-sql"></a><span data-ttu-id="e348b-102">USANDO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e348b-102">USING (Entity SQL)</span></span>

<span data-ttu-id="e348b-103">Especifica namespaces utilizados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="e348b-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e348b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e348b-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="e348b-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e348b-105">Arguments</span></span>  

 `alias`  
 <span data-ttu-id="e348b-106">Especifica um alias mais curto com o qual qualificar um namespace.</span><span class="sxs-lookup"><span data-stu-id="e348b-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="e348b-107">Qualquer namespace válido.</span><span class="sxs-lookup"><span data-stu-id="e348b-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e348b-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e348b-108">Example</span></span>  

 <span data-ttu-id="e348b-109">A consulta Entity SQL a seguir usa o operador USING para especificar namespaces utilizados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="e348b-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="e348b-110">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="e348b-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e348b-111">Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e348b-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="e348b-112">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="e348b-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="e348b-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="e348b-113">See also</span></span>

- [<span data-ttu-id="e348b-114">Namespaces</span><span class="sxs-lookup"><span data-stu-id="e348b-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="e348b-115">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e348b-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
