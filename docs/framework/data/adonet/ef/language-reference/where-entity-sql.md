---
title: ONDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 02eeaeb8cfa335e5545b26d3d52b91c4e1614629
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230701"
---
# <a name="where-entity-sql"></a>ONDE (Entity SQL)
A cláusula WHERE é aplicada diretamente após o [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) cláusula.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Um tipo booleano.  
  
## <a name="remarks"></a>Comentários  
 A cláusula WHERE tem a mesma semântica que descrita para [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Restringe os objetos gerados pela expressão de consulta limitando os elementos das coleções de fonte àquelas que passam a condição.  
  
```  
select c from cs as c where e  
```  
  
 A expressão `e` deve ter o tipo booleano.  
  
 A cláusula WHERE é aplicada diretamente após a cláusula e antes de qualquer agrupamento, ordenação, ou projeção ocorre. Todos os nomes de elementos definidos na cláusula são visíveis para a expressão de uma cláusula WHERE.  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Expressões de Consulta](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
