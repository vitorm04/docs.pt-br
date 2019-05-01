---
title: Expressões sem suporte (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: a47ff46ca99a84500bc5dfecc19bb31652e9b4b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034067"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="4ace0-102">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="4ace0-102">Unsupported expressions</span></span>

<span data-ttu-id="4ace0-103">Este tópico descreve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressões que não têm suporte no [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ace0-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="4ace0-104">Para obter mais informações, consulte [como Entity SQL difere do Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4ace0-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="4ace0-105">Predicados determinados</span><span class="sxs-lookup"><span data-stu-id="4ace0-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="4ace0-106">permite compilações de seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4ace0-106">allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="4ace0-107">, no entanto, não suporta como compilações.</span><span class="sxs-lookup"><span data-stu-id="4ace0-107">, however, does not support such constructs.</span></span> <span data-ttu-id="4ace0-108">As expressões equivalentes podem ser gravadas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como segue:</span><span class="sxs-lookup"><span data-stu-id="4ace0-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="4ace0-109">Operador \*</span><span class="sxs-lookup"><span data-stu-id="4ace0-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="4ace0-110">oferece suporte ao uso do operador \* na cláusula SELECT indicar que todas as colunas devem ser projetadas para fora. Isso não é suportado em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ace0-110">supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="4ace0-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ace0-111">See also</span></span>

- [<span data-ttu-id="4ace0-112">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4ace0-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="4ace0-113">Diferenças entre o Entity SQL e o Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4ace0-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
