---
title: . (Acesso de membro) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: e2874e5bff8d8c34f700a81bf52c6729df49aca5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626654"
---
# <a name="-member-access-entity-sql"></a>. (Acesso de membro) (Entity SQL)
O operador ponto (.) é o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operador de acesso de membro. Você usa o operador de acesso de membro para produzir o valor de uma propriedade ou um campo de uma instância do tipo estrutural de modelo conceitual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Uma instância de um tipo estrutural de modelo conceitual.  
  
 `identifier`  
 Uma propriedade ou um campo que pertençam a uma instância do objeto.  
  
## <a name="remarks"></a>Comentários  
 O operador ponto (.) pode ser usado para extrair campos de um registro, semelhante a extrair propriedades de um complexo ou tipo de objeto. Por exemplo, se n do nome do tipo é um membro do tipo Person e p é uma instância do tipo Person, p.n é uma expressão de acesso de membro legal que gera um valor do nome do tipo.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Consulte também
- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
