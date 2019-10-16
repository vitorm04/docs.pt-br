---
title: Variáveis (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bb8e6ebe81dacc7ec0f45fdde65b9c18cfd76789
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319196"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="21626-102">Variáveis (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="21626-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="21626-103">Variável</span><span class="sxs-lookup"><span data-stu-id="21626-103">Variable</span></span>  
 <span data-ttu-id="21626-104">Uma expressão variável é uma referência a uma expressão chamado definida no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="21626-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="21626-105">Uma referência de variável deve ser um identificador [!INCLUDE[esql](../../../../../../includes/esql-md.md)] válido, conforme definido em [identificadores](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="21626-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="21626-106">O exemplo a seguir mostra o uso de uma variável na expressão.</span><span class="sxs-lookup"><span data-stu-id="21626-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="21626-107">`c` na cláusula é a definição da variável.</span><span class="sxs-lookup"><span data-stu-id="21626-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="21626-108">O uso de `c` na cláusula SELECT representa a referência variável.</span><span class="sxs-lookup"><span data-stu-id="21626-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="21626-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21626-109">See also</span></span>

- [<span data-ttu-id="21626-110">Identificadores</span><span class="sxs-lookup"><span data-stu-id="21626-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="21626-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21626-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="21626-112">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="21626-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
