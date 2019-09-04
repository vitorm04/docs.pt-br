---
title: Parâmetros (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249582"
---
# <a name="parameters-entity-sql"></a>Parâmetros (Entity SQL)
Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host. Cada parâmetro tem um nome e um tipo. Os nomes de parâmetro são definidos em expressões de consulta com o símbolo arroba (@) como um prefixo. Isso os desambigua dos nomes das propriedades ou de outros nomes definidos na consulta.  
  
 O host linguagem que associa API fornece APIs para parâmetros de associação.  
  
## <a name="example"></a>Exemplo  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
- [Visão geral do Entity SQL](entity-sql-overview.md)
