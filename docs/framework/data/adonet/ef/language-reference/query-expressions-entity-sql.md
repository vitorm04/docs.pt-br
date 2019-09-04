---
title: Consulte expressões (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 4428286890f41573a02daf31a4593d0c8f9ad34b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249270"
---
# <a name="query-expressions-entity-sql"></a>Consulte expressões (Entity SQL)
Uma expressão de consulta combina muitos diferentes operadores de consulta em uma única sintaxe. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]fornece vários tipos de expressões, incluindo as seguintes: [literais](literals-entity-sql.md), [parâmetros](parameters-entity-sql.md), [variáveis](variables-entity-sql.md), operadores, [funções](functions-entity-sql.md), operadores de conjunto e assim por diante. Para obter mais informações, consulte [referência de Entity SQL](entity-sql-reference.md).  
  
## <a name="clauses"></a>Cláusulas  
 Uma expressão de consulta é composta de uma série de cláusulas que operações sucessivas aplicam a uma coleção de objetos. Elas se baseiam nas mesmas cláusulas encontradas em uma instrução SQL SELECT padrão: [Selecione](select-entity-sql.md), [de](from-entity-sql.md), [onde](where-entity-sql.md), [Agrupar por](group-by-entity-sql.md), [tendo](having-entity-sql.md)e [ordenar por](order-by-entity-sql.md).  
  
## <a name="scope"></a>Escopo  
 Nomes definidos na cláusula são apresentados no escopo por ordem de aparência, da esquerda para a direita. Na lista JOIN, as expressões podem referir-se nomes definidos anteriormente na lista. As propriedades públicas dos elementos identificados na cláusula FROM não são adicionadas ao escopo FROM: Eles devem ser sempre referenciados por meio do nome qualificado por alias. Normalmente, todas as partes da expressão selecionar são considerados dentro do escopo.  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
