---
title: "Expressões sem suporte (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c18c726a962d9a29a3dace1ebd5c2073637bb4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="unsupported-expressions-entity-sql"></a><span data-ttu-id="4ce85-102">Expressões sem suporte (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4ce85-102">Unsupported Expressions (Entity SQL)</span></span>
<span data-ttu-id="4ce85-103">Este tópico descreve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressões que não têm suporte em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce85-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="4ce85-104">Para obter mais informações, consulte [como o Entity SQL difere do Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4ce85-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>  
  
## <a name="quantified-predicates"></a><span data-ttu-id="4ce85-105">Predicados determinados</span><span class="sxs-lookup"><span data-stu-id="4ce85-105">Quantified Predicates</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="4ce85-106"> permite compilações de seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4ce85-106"> allows constructs of the following form:</span></span>  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="4ce85-107">, no entanto, não suporta como compilações.</span><span class="sxs-lookup"><span data-stu-id="4ce85-107">, however, does not support such constructs.</span></span> <span data-ttu-id="4ce85-108">As expressões equivalentes podem ser gravadas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como segue:</span><span class="sxs-lookup"><span data-stu-id="4ce85-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## <a name="-operator"></a><span data-ttu-id="4ce85-109">Operador *</span><span class="sxs-lookup"><span data-stu-id="4ce85-109">* Operator</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="4ce85-110"> oferece suporte ao uso do operador * na cláusula SELECT indicar que todas as colunas devem ser projetadas para fora. Isso não é suportado em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ce85-110"> supports the use of the * operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce85-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ce85-111">See Also</span></span>  
 [<span data-ttu-id="4ce85-112">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4ce85-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="4ce85-113">Como o Entity SQL difere do Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4ce85-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
