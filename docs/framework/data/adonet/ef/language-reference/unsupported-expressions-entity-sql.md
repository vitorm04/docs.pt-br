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
# <a name="unsupported-expressions"></a>Expressões sem suporte

Este tópico descreve as expressões de Transact-SQL que não têm suporte no [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Para obter mais informações, consulte [como Entity SQL difere do Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Predicados determinados

Transact-SQL permite que as construções da seguinte forma:

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

Transact-SQL suporta o uso do * operador na cláusula SELECT para indicar que todas as colunas devem ser projetadas. Isso não é suportado em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Consulte também

- [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Diferenças entre o Entity SQL e o Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
