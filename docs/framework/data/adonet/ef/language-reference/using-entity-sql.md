---
title: USANDO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: e14b7857a65898683939647c872c48d0b3fe458a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297857"
---
# <a name="using-entity-sql"></a><span data-ttu-id="a6856-102">USANDO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a6856-102">USING (Entity SQL)</span></span>
<span data-ttu-id="a6856-103">Especifica namespaces utilizados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="a6856-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6856-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6856-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="a6856-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a6856-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="a6856-106">Especifica um alias mais curto com o qual qualificar um namespace.</span><span class="sxs-lookup"><span data-stu-id="a6856-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="a6856-107">Qualquer namespace válido.</span><span class="sxs-lookup"><span data-stu-id="a6856-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6856-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6856-108">Example</span></span>  
 <span data-ttu-id="a6856-109">A consulta Entity SQL a seguir usa o operador USING para especificar namespaces utilizados em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="a6856-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="a6856-110">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a6856-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a6856-111">Siga o procedimento em [como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a6856-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="a6856-112">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a6856-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6856-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6856-113">See also</span></span>

- [<span data-ttu-id="a6856-114">Namespaces</span><span class="sxs-lookup"><span data-stu-id="a6856-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [<span data-ttu-id="a6856-115">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a6856-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
