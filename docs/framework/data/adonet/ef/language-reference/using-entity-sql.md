---
title: USANDO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: bdab81ed8acae5e757de0a669922dc79d0303ee4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203586"
---
# <a name="using-entity-sql"></a>USANDO (Entity SQL)

Especifica namespaces utilizados em uma expressão de consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Argumentos  

 `alias`  
 Especifica um alias mais curto com o qual qualificar um namespace.  
  
 `namespace`  
 Qualquer namespace válido.  
  
## <a name="example"></a>Exemplo  

 A consulta Entity SQL a seguir usa o operador USING para especificar namespaces utilizados em uma expressão de consulta. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como executar uma consulta que retorna os resultados de primitivatype](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Veja também

- [Namespaces](namespaces-entity-sql.md)
- [Referência de Entity SQL](entity-sql-reference.md)
