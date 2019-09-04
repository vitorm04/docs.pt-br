---
title: Expressões sem suporte (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: 956fe117eb0c59392c3999046bc70deaed268ac6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248776"
---
# <a name="unsupported-expressions"></a>Expressões sem suporte

Este tópico descreve as expressões Transact-SQL que não têm suporte [!INCLUDE[esql](../../../../../../includes/esql-md.md)]no. Para obter mais informações, consulte [como Entity SQL difere do Transact-SQL](how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Predicados quantificados

O Transact-SQL permite constructos da seguinte forma:

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

O Transact-SQL dá suporte ao uso do operador * na cláusula SELECT para indicar que todas as colunas devem ser projetadas. Isso não é suportado em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Consulte também

- [Visão geral do Entity SQL](entity-sql-overview.md)
- [Diferenças entre o Entity SQL e o Transact-SQL](how-entity-sql-differs-from-transact-sql.md)
