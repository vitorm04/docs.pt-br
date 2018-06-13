---
title: Consulte expressões (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: d721f54486845847ec86253356e7a605f882722b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763547"
---
# <a name="query-expressions-entity-sql"></a>Consulte expressões (Entity SQL)
Uma expressão de consulta combina muitos diferentes operadores de consulta em uma única sintaxe. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece vários tipos de expressões, incluindo o seguinte: [literais](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parâmetros](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variáveis](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operadores, [funções](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), operadores de conjunto e assim por diante. Para obter mais informações, consulte [referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Cláusulas  
 Uma expressão de consulta é composta de uma série de cláusulas que operações sucessivas aplicam a uma coleção de objetos. Eles se baseiam nas mesmas cláusulas encontradas no padrão de uma instrução select SQL: [selecione](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [onde](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [Ter](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), e [ORDENAR por](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Escopo  
 Nomes definidos na cláusula são apresentados no escopo por ordem de aparência, da esquerda para a direita. Na lista JOIN, as expressões podem referir-se nomes definidos anteriormente na lista. As propriedades públicas de elementos identificadas na cláusula não são adicionadas ao escopo: Sempre devem ser referenciados com o nome qualificado alias-. Normalmente, todas as partes da expressão selecionar são considerados dentro do escopo.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
