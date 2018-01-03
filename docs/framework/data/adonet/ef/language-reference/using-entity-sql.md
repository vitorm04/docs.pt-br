---
title: USANDO (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cc69dba9e70bb6bcc870b1cb92e98cb656cad98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-entity-sql"></a>USANDO (Entity SQL)
Especifica namespaces utilizados em uma expressão de consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Especifica um alias mais curto com o qual qualificar um namespace.  
  
 `namespace`  
 Qualquer namespace válido.  
  
## <a name="example"></a>Exemplo  
 A consulta Entity SQL a seguir usa o operador USING para especificar namespaces utilizados em uma expressão de consulta. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Consulte também  
 [Namespaces](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
