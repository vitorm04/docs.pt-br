---
title: Expressões sem suporte (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: bf20bb92010d5031e973cb1cc004b6b8f13d0091
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234308"
---
# <a name="unsupported-expressions"></a>Não há suporte para expressões

Este tópico descreve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressões que não têm suporte em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Para obter mais informações, consulte [como o Entity SQL difere do Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Predicados quantificados

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] permite compilações de seguinte forma:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)], no entanto, não suporta como compilações. As expressões equivalentes podem ser gravadas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como segue:

```sql
not exists(select 0 from employees as e where sal <= e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>Operador *

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] oferece suporte ao uso do operador * na cláusula SELECT indicar que todas as colunas devem ser projetadas para fora. Isso não é suportado em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Consulte também

[Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[Diferenças entre o Entity SQL e o Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
