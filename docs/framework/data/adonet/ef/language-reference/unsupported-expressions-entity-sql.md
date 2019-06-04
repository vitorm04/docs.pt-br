---
title: Expressões sem suporte (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: af0e00f470584883b6a65b63f2650c1c359b404c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489864"
---
# <a name="unsupported-expressions"></a><span data-ttu-id="1e603-102">Expressões sem suporte</span><span class="sxs-lookup"><span data-stu-id="1e603-102">Unsupported expressions</span></span>

<span data-ttu-id="1e603-103">Este tópico descreve as expressões de Transact-SQL que não têm suporte no [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e603-103">This topic describes Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="1e603-104">Para obter mais informações, consulte [como Entity SQL difere do Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1e603-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="1e603-105">Predicados determinados</span><span class="sxs-lookup"><span data-stu-id="1e603-105">Quantified predicates</span></span>

<span data-ttu-id="1e603-106">Transact-SQL permite que as construções da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1e603-106">Transact-SQL allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1e603-107">, no entanto, não suporta como compilações.</span><span class="sxs-lookup"><span data-stu-id="1e603-107">, however, does not support such constructs.</span></span> <span data-ttu-id="1e603-108">As expressões equivalentes podem ser gravadas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como segue:</span><span class="sxs-lookup"><span data-stu-id="1e603-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="1e603-109">Operador \*</span><span class="sxs-lookup"><span data-stu-id="1e603-109">\* operator</span></span>

<span data-ttu-id="1e603-110">Transact-SQL suporta o uso do \* operador na cláusula SELECT para indicar que todas as colunas devem ser projetadas. Isso não é suportado em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e603-110">Transact-SQL supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="1e603-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e603-111">See also</span></span>

- [<span data-ttu-id="1e603-112">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1e603-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="1e603-113">Diferenças entre o Entity SQL e o Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1e603-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
