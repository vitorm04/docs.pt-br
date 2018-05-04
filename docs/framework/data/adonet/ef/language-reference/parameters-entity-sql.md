---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: c8bdb54e52b4c0d189f3bff72bdb24785c1a9c27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="parameters-entity-sql"></a>Parâmetros (Entity SQL)
Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host. Cada parâmetro tem um nome e um tipo. Nomes de parâmetro são definidos em expressões de consulta com o em (@) símbolo como um prefixo. Isso remove a ambiguidade dos-los de nomes de propriedades ou outros nomes que são definidos na consulta.  
  
 O host linguagem que associa API fornece APIs para parâmetros de associação.  
  
## <a name="example"></a>Exemplo  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
