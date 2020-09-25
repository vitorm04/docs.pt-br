---
title: . (Acesso de membro) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 82cd2f17b2b5ea484a8202b50619047b428fe94a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192146"
---
# <a name="-member-access-entity-sql"></a>. (Acesso de membro) (Entity SQL)

O operador de ponto (.) é o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operador de acesso de membro. Você usa o operador de acesso de membro para produzir o valor de uma propriedade ou um campo de uma instância do tipo estrutural de modelo conceitual.  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a>Argumentos  

 `expression`  
 Uma instância de um tipo estrutural de modelo conceitual.  
  
 `identifier`  
 Uma propriedade ou um campo que pertençam a uma instância do objeto.  
  
## <a name="remarks"></a>Comentários  

 O operador ponto (.) pode ser usado para extrair campos de um registro, semelhante a extrair propriedades de um complexo ou tipo de objeto. Por exemplo, se n do tipo name for um membro do tipo Person, e p for uma instância do tipo Person, p. n será uma expressão de acesso de membro legal que produz um valor do tipo Name.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Veja também

- [Referência de Entity SQL](entity-sql-reference.md)
