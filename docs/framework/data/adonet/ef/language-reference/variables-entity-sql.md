---
title: Variáveis (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: af6d586a22f14a04bfc7ec339d0aa8e9ba7c66c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180986"
---
# <a name="variables-entity-sql"></a>Variáveis (Entity SQL)

## <a name="variable"></a>Variável  

 Uma expressão variável é uma referência a uma expressão chamado definida no escopo atual. Uma referência de variável deve ser um [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificador válido, conforme definido em [identificadores](identifiers-entity-sql.md).  
  
 O exemplo a seguir mostra o uso de uma variável na expressão. `c` na cláusula é a definição da variável. O uso de `c` na cláusula SELECT representa a referência variável.  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Veja também

- [Identificadores](identifiers-entity-sql.md)
- [Parâmetros](parameters-entity-sql.md)
- [Visão geral da Entity SQL](entity-sql-overview.md)
