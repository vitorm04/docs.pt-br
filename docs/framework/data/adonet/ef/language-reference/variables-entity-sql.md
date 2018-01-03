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
# <a name="variables-entity-sql"></a>Variáveis (Entity SQL)
## <a name="variable"></a>Variável  
 Uma expressão variável é uma referência a uma expressão chamado definida no escopo atual. Uma referência de variável deve ser um válido [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificador, conforme definido em [identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).  
  
 O exemplo a seguir mostra o uso de uma variável na expressão. `c` na cláusula é a definição da variável. O uso de `c` na cláusula SELECT representa a referência variável.  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Consulte também  
 [Identificadores](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [Parâmetros](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
