---
title: "Variáveis (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fff24c4572fab483c701a93167c0f229d5111d61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="variables-entity-sql"></a><span data-ttu-id="ed754-102">Variáveis (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ed754-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="ed754-103">Variável</span><span class="sxs-lookup"><span data-stu-id="ed754-103">Variable</span></span>  
 <span data-ttu-id="ed754-104">Uma expressão variável é uma referência a uma expressão chamado definida no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="ed754-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="ed754-105">Uma referência de variável deve ser um válido [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificador, conforme definido em [identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ed754-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="ed754-106">O exemplo a seguir mostra o uso de uma variável na expressão.</span><span class="sxs-lookup"><span data-stu-id="ed754-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="ed754-107">`c` na cláusula é a definição da variável.</span><span class="sxs-lookup"><span data-stu-id="ed754-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="ed754-108">O uso de `c` na cláusula SELECT representa a referência variável.</span><span class="sxs-lookup"><span data-stu-id="ed754-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed754-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed754-109">See Also</span></span>  
 [<span data-ttu-id="ed754-110">Identificadores</span><span class="sxs-lookup"><span data-stu-id="ed754-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="ed754-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed754-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="ed754-112">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ed754-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
