---
title: ONDE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 1907b8786622d3c8019c75916f997c830cc07cfb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180953"
---
# <a name="where-entity-sql"></a>ONDE (Entity SQL)

A cláusula WHERE é aplicada diretamente após a cláusula [from](from-entity-sql.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Argumentos  

 `expression`  
 Um tipo booleano.  
  
## <a name="remarks"></a>Comentários  

 A cláusula WHERE tem a mesma semântica, conforme descrito para Transact-SQL. Restringe os objetos gerados pela expressão de consulta limitando os elementos das coleções de fonte àquelas que passam a condição.  
  
```sql  
select c from cs as c where e  
```  
  
 A expressão `e` deve ter o tipo booleano.  
  
 A cláusula WHERE é aplicada diretamente após a cláusula e antes de qualquer agrupamento, ordenação, ou projeção ocorre. Todos os nomes de elementos definidos na cláusula são visíveis para a expressão de uma cláusula WHERE.  
  
## <a name="see-also"></a>Veja também

- [Referência de Entity SQL](entity-sql-reference.md)
- [Expressões de consulta](query-expressions-entity-sql.md)
