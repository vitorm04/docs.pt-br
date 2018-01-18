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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d035f8d5616f2eb4c5a4db31857da2be0cd3d930
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
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
