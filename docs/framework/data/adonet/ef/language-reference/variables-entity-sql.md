---
title: Variáveis (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149811"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="5219a-102">Variáveis (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5219a-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="5219a-103">Variável</span><span class="sxs-lookup"><span data-stu-id="5219a-103">Variable</span></span>  
 <span data-ttu-id="5219a-104">Uma expressão variável é uma referência a uma expressão chamado definida no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="5219a-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="5219a-105">Uma referência variável deve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ser um identificador válido, conforme definido [em Identificadores](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5219a-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="5219a-106">O exemplo a seguir mostra o uso de uma variável na expressão.</span><span class="sxs-lookup"><span data-stu-id="5219a-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="5219a-107">`c` na cláusula é a definição da variável.</span><span class="sxs-lookup"><span data-stu-id="5219a-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="5219a-108">O uso de `c` na cláusula SELECT representa a referência variável.</span><span class="sxs-lookup"><span data-stu-id="5219a-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="5219a-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="5219a-109">See also</span></span>

- [<span data-ttu-id="5219a-110">Identificadores</span><span class="sxs-lookup"><span data-stu-id="5219a-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="5219a-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5219a-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="5219a-112">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5219a-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
