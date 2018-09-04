---
title: Composta consultas aninhadas Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 8a0efa672a57a9255af2d90af1725b34be75600e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528150"
---
# <a name="composing-nested-entity-sql-queries"></a>Composta consultas aninhadas Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] é uma linguagem funcional rico. O bloco de construção de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é uma expressão. Ao contrário do SQL convencional, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não está limitado a um conjunto de resultados tabulares: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suporta composto expressões complexas que podem ter literais, parâmetros ou expressões aninhadas. Um valor na expressão pode ser parametrizado ou composto de alguma outra expressão.  
  
## <a name="nested-expressions"></a>Expressões aninhadas  
 Uma expressão aninhada pode ser colocadas em qualquer lugar um valor de tipo que retorna é aceito. Por exemplo:  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Uma consulta aninhada pode ser colocadas em uma cláusula de projeção. Por exemplo:  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 Em [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultas aninhadas devem sempre ser colocado entre parênteses:  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 O exemplo a seguir demonstra como aninhar expressões corretamente em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [como: solicitar a união de duas consultas](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313).  
  
## <a name="nested-queries-in-projection"></a>Consultas aninhadas na projeção  
 Consultas aninhadas na cláusula de projeto podem obter convertido em consultas de produto cartesiano no servidor. Em alguns servidores backend, incluindo o servidor de SLQ, isso pode fazer com que a tabela de TempDB obtenha muito grande, que pode afetar o desempenho do servidor.  
  
 O seguinte é um exemplo de tal consulta:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Ordenando consultas aninhadas  
 Em Entity Framework, uma expressão aninhada pode ser colocadas em qualquer lugar na consulta. Porque Entity SQL permite grande flexibilidade em consultas de escrita, é possível escrever uma consulta que contém a ordem das consultas aninhadas. No entanto, a ordem de uma consulta aninhada não é preservada.  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
