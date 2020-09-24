---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 759452902461e1a460b69774bb33f92bbd532ed0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177508"
---
# <a name="parameters-entity-sql"></a>Parâmetros (Entity SQL)

Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host. Cada parâmetro tem um nome e um tipo. Os nomes de parâmetro são definidos em expressões de consulta com o símbolo arroba (@) como um prefixo. Isso os desambigua dos nomes das propriedades ou de outros nomes definidos na consulta.  
  
 O host linguagem que associa API fornece APIs para parâmetros de associação.  
  
## <a name="example"></a>Exemplo  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a>Confira também

- [Referência de Entity SQL](entity-sql-reference.md)
- [Visão geral da Entity SQL](entity-sql-overview.md)
