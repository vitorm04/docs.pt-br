---
title: Variáveis (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: af6d586a22f14a04bfc7ec339d0aa8e9ba7c66c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180986"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="5e01f-102">Variáveis (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5e01f-102">Variables (Entity SQL)</span></span>

## <a name="variable"></a><span data-ttu-id="5e01f-103">Variável</span><span class="sxs-lookup"><span data-stu-id="5e01f-103">Variable</span></span>  

 <span data-ttu-id="5e01f-104">Uma expressão variável é uma referência a uma expressão chamado definida no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="5e01f-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="5e01f-105">Uma referência de variável deve ser um [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificador válido, conforme definido em [identificadores](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5e01f-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="5e01f-106">O exemplo a seguir mostra o uso de uma variável na expressão.</span><span class="sxs-lookup"><span data-stu-id="5e01f-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="5e01f-107">`c` na cláusula é a definição da variável.</span><span class="sxs-lookup"><span data-stu-id="5e01f-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="5e01f-108">O uso de `c` na cláusula SELECT representa a referência variável.</span><span class="sxs-lookup"><span data-stu-id="5e01f-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e01f-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="5e01f-109">See also</span></span>

- [<span data-ttu-id="5e01f-110">Identificadores</span><span class="sxs-lookup"><span data-stu-id="5e01f-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="5e01f-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5e01f-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="5e01f-112">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5e01f-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
