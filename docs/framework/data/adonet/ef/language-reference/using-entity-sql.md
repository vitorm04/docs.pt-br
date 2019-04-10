---
title: USANDO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: e14b7857a65898683939647c872c48d0b3fe458a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297857"
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
  
1. Siga o procedimento em [como: Executar uma consulta que retorna resultados PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Consulte também

- [Namespaces](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
