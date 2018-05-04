---
title: Definições de tipo (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7abbe5dfed005a10955a385cadf12725a9450512
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="type-definitions-entity-sql"></a>Definições de tipo (Entity SQL)
Uma definição de tipo é usada na instrução de declaração de uma função in-line de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="remarks"></a>Comentários  
 A instrução de declaração para uma função embutida consiste de [função](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) palavra-chave seguida pelo identificador que representa o nome da função (por exemplo, "MyAvg") seguido por uma lista de definições de parâmetro entre parênteses (para exemplo, "devido a Collection(Decimal)").  
  
 A lista de definição de parâmetro consiste de zero ou mais definições de parâmetro. Cada definição de parâmetro consiste em um identificador (o nome do parâmetro para a função, por exemplo, a dívidas “”) seguido por uma definição de tipo (por exemplo, “coleção (decimal) ").  
  
 Definições de tipo podem ser qualquer:  
  
-   O tipo identificador (por exemplo, “Int32” ou “AdventureWorks.Order”).  
  
-   A palavra-chave `COLLECTION` seguido por outra definição de tipo no parêntese (por exemplo, “coleção (AdventureWorks.Order) ").  
  
-   A LINHA seguida por uma lista de definições de propriedade no parêntese (por exemplo, “linha de palavras-chave (x) AdventureWorks.Order "). Definições de propriedade tem um formato como "`identifier type_definition`, `identifier type_definition`,...".  
  
-   A referência seguido pelo tipo identificador no parêntese (por exemplo, “referência de palavras-chave (AdventureWorks.Order) "). O operador de definição de tipo de referência requer um tipo de entidade como o argumento. Você não pode especificar um tipo primitivo como o argumento.  
  
 Você também pode aninhar definições de tipo (por exemplo, “coleção (linha (referência de AdventureWorks.Order (x))").  
  
 As opções de definição de tipo são:  
  
-   `IdentifierName supported_type`, ou  
  
-   COLEÇÃO de`IdentifierName` (`type_definition`), ou  
  
-   LINHA de`IdentifierName` (`property_definition`), ou  
  
-   referência de`IdentifierName` (`supported_entity_type`)  
  
 A opção de definição de propriedade é `IdentifierName type_definition`.  
  
 Os tipos suportados são alguns tipos no namespace atual. Esses incluem a primitiva e os tipos de entidade.  
  
 Os tipos de entidade suporte a apenas tipos de entidade no namespace atual. Não incluem tipos primitivos.  
  
## <a name="examples"></a>Exemplos  
 A seguir está um exemplo de uma definição de tipo simples.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 A seguir está um exemplo de uma definição de tipo de COLEÇÃO.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 A seguir está um exemplo de uma definição de tipo de LINHA.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 A seguir está um exemplo de uma definição de tipo de LINHA.  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
