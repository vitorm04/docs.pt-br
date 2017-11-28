---
title: ORDENAR POR (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b805d4437ffd8d3d56a7cdc599bdda797a763d13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="order-by-entity-sql"></a>ORDENAR POR (Entity SQL)
Especifica a ordem de classificação usado em objetos retornados em uma instrução SELECT.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a>Arguments  
 `order_by_expression`  
 Qualquer expressão de consulta válida especificando uma propriedade para classificar. Várias expressões de tipo podem ser especificadas. A sequência das expressões de tipo na cláusula ORDER BY define a organização do conjunto de resultados classificada.  
  
 ORDENE {} collation_name  
 Especifica que a cláusula ORDER BY operação deve ser executado de acordo com o agrupamento especificado em `collation_name`. COLLATE é aplicável somente para expressões de cadeia de caracteres.  
  
 ASC  
 Especifica que os valores na propriedade especificada devem ser classificados na ordem crescente, o valor menor para o maior valor. Esse é o padrão.  
  
 DESC  
 Especifica que os valores na propriedade especificada devem ser classificados em ordem decrescente, o valor o maior o valor menor.  
  
 LIMIT `n`  
 Somente o primeiro item de `n` serão selecionados.  
  
 SKIP `n`  
 Ignora os primeiros itens de `n` .  
  
## <a name="remarks"></a>Comentários  
 A cláusula ORDER BY é aplicado logicamente o resultado da cláusula SELECT. A cláusula ORDER BY pode referenciar itens na lista select usando seu alias. A cláusula ORDER BY também pode referenciar outros variáveis que são atualmente em- escopo. No entanto, se a cláusula SELECT foi especificada com um modificador DISTINCT, a cláusula ORDER BY pode apenas referenciar alias de cláusula SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Cada expressão na cláusula ORDER BY deve avaliar a qualquer tipo que pode ser comparado para desigualdade ordenada (menor que ou maior do que, e assim por diante). Esses tipos são geralmente primitivos escalares como números, cadeias de caracteres, e datas. RowTypes de tipos comparáveis também é comparado ordem.  
  
 Se seu código itera através de um conjunto ordenado, exceto para uma projeção de nível superior, a saída não é garantida para ter sua ordem preservada.  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Para ter uma operação UNION, UNION ALL, EXCEPT, ou INTERSECT ordenada, use o padrão a seguir:  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Palavras-chave restritas  
 As seguintes palavras chave devem ser colocados entre aspas quando usado em uma cláusula de `ORDER BY` :  
  
-   CROSS  
  
-   FULL  
  
-   KEY  
  
-   LEFT  
  
-   ORDER  
  
-   OUTER  
  
-   RIGHT  
  
-   ROW  
  
-   VALUE  
  
## <a name="ordering-nested-queries"></a>Ordenando consultas aninhadas  
 Em Entity Framework, uma expressão aninhada pode ser colocada em qualquer lugar na consulta; a ordem de uma consulta aninhada não é preservada.  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a>Exemplo  
 A seguinte consulta de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usa o operador cláusula ORDER pelo especificar ordem de classificação usado em objetos retornados em uma instrução SELECT. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1.  Siga o procedimento [como: executar uma consulta que retorna resultados de StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passe a consulta a seguir como um argumento para o método `ExecuteStructuralTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a>Consulte também  
 [Expressões de Consulta](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [IGNORAR](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [LIMITE](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [INÍCIO](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
