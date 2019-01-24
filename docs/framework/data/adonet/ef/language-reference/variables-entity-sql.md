---
title: Variáveis (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: a16c450401eee1021aeef885fba129c943a87fd7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742258"
---
# <a name="variables-entity-sql"></a>Variáveis (Entity SQL)
## <a name="variable"></a>Variável  
 Uma expressão variável é uma referência a uma expressão chamado definida no escopo atual. Uma referência de variável deve ser um válido [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificador, conforme definido na [identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 O exemplo a seguir mostra o uso de uma variável na expressão. `c` na cláusula é a definição da variável. O uso de `c` na cláusula SELECT representa a referência variável.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Consulte também
- [Identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)
- [Parâmetros](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)
- [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
