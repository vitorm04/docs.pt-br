---
title: USANDO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 89306c8b4c317ebaba0d964869c4fe9e1028631a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762332"
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
