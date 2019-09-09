---
title: Variáveis (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248686"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="05280-102">Variáveis (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="05280-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="05280-103">Variável</span><span class="sxs-lookup"><span data-stu-id="05280-103">Variable</span></span>  
 <span data-ttu-id="05280-104">Uma expressão variável é uma referência a uma expressão chamado definida no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="05280-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="05280-105">Uma referência de variável deve ser um [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificador válido, conforme definido em [identificadores](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="05280-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="05280-106">O exemplo a seguir mostra o uso de uma variável na expressão.</span><span class="sxs-lookup"><span data-stu-id="05280-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="05280-107">`c` na cláusula é a definição da variável.</span><span class="sxs-lookup"><span data-stu-id="05280-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="05280-108">O uso de `c` na cláusula SELECT representa a referência variável.</span><span class="sxs-lookup"><span data-stu-id="05280-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="05280-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05280-109">See also</span></span>

- [<span data-ttu-id="05280-110">Identificadores</span><span class="sxs-lookup"><span data-stu-id="05280-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="05280-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05280-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="05280-112">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="05280-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
