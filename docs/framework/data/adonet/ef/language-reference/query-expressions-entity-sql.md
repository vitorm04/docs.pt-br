---
title: Consulte expressões (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 5f89028b9c501dd840f1dc9445418e4757967db8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146907"
---
# <a name="query-expressions-entity-sql"></a>Consulte expressões (Entity SQL)
Uma expressão de consulta combina muitos diferentes operadores de consulta em uma única sintaxe. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece vários tipos de expressões, incluindo o seguinte: [literais](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parâmetros](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variáveis](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operadores, [funções](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), defina operadores e assim por diante. Para obter mais informações, consulte [referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Cláusulas  
 Uma expressão de consulta é composta de uma série de cláusulas que operações sucessivas aplicam a uma coleção de objetos. Eles são baseados nas mesmas cláusulas encontradas no padrão de uma instrução select SQL: [Selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [onde](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), e [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Escopo  
 Nomes definidos na cláusula são apresentados no escopo por ordem de aparência, da esquerda para a direita. Na lista JOIN, as expressões podem referir-se nomes definidos anteriormente na lista. Propriedades públicas dos elementos identificadas na cláusula FROM não são adicionadas ao escopo: Eles sempre devem ser referenciados por meio do nome qualificado alias. Normalmente, todas as partes da expressão selecionar são considerados dentro do escopo.  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
