---
title: . (Acesso de membro) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: fdcd026d245b3f6d6ecaccc0f828f3d77fd6ce1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764626"
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
 O operador ponto (.) pode ser usado para extrair campos de um registro, semelhante a extrair propriedades de um complexo ou tipo de objeto. Por exemplo, se n do nome de tipo é um membro de tipo Person e p é uma instância de tipo Person, p.n é uma expressão de acesso de membro válido que gera um valor de tipo de nome.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
