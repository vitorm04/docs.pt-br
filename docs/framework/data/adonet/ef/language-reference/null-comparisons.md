---
title: Comparações nulas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 697c933daeb3c68fb4ea89a957b639a79a9407f8
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249650"
---
# <a name="null-comparisons"></a>Comparações nulas
Um valor `null` na fonte de dados indica que o valor é desconhecido. Nas consultas LINQ to Entities, você pode verificar se há valores nulos para que certos cálculos ou comparações sejam realizados apenas em linhas que tenham dados válidos ou não nulos. A semântica nula do CLR, no entanto, pode diferir da semântica nula da fonte de dados. A maioria dos bancos de dados usa uma versão da lógica de três valores para manipular comparações nulas. Ou seja, uma comparação com um `true` valor `false`nulo não `unknown`avalia ou, avalia. Geralmente, essa é uma implementação de valores nulos ANSI, mas isso nem sempre acontece.  
  
 Por padrão, no SQL Server, a comparação nulo igual a nulo retorna um valor nulo. No exemplo a seguir, `ShipDate` as linhas em que é nula são excluídas do conjunto de resultados e a declaração Transact-SQL retornaria 0 linhas.  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 Isso é muito diferente de semântica nula do CLR, em que a comparação de null igual a null retorna true.  
  
 A seguinte consulta LINQ é expressa no CLR, mas é executada na fonte de dados. Como não há nenhuma garantia de que a semântica do CLR será respeitada na fonte de dados, o comportamento esperado será indeterminado.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Seletores de chave  
 Um *seletor de teclas* é uma função usada nos operadores de consulta padrão para extrair uma chave de um elemento. Na função do seletor de chave, uma expressão pode ser comparada a uma constante. A semântica nula do CLR será exibida se uma expressão for comparada com uma constante nula ou se duas constantes nulas forem comparadas. As semânticas nulas de armazenamento serão exibidas se duas colunas com valores nulos na fonte de dados forem comparadas. Os seletores de chave são encontrados em muitos operadores de consulta padrão de agrupamento e ordenação, como <xref:System.Linq.Queryable.GroupBy%2A>, e usados para selecionar as chaves que servirão de base para a ordenação ou o agrupamento do resultados da consulta.  
  
## <a name="null-property-on-a-null-object"></a>Propriedade nula em um objeto nulo  
 No Quadro de Entidades, as propriedades de um objeto nulo são nulas. Ao tentar fazer referência à propriedade de um objeto nulo no CLR, você receberá <xref:System.NullReferenceException>. Quando uma consulta LINQ envolver uma propriedade de um objeto nulo, o resultado possivelmente será um comportamento inconsistente.  
  
 Por exemplo, na consulta a seguir, a conversão em `NewProduct` é feita na camada da árvore de comandos, que pode resultar na propriedade `Introduced` que está sendo nula. Se o banco de dados tiver definido comparações nulas, como a comparação <xref:System.DateTime> que é avaliada como true, a linha será incluída.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Passando coleções nulas para funções agregadas  
 Em LINQ para Entidades, quando você `IQueryable` passa uma coleção que suporta uma função agregada, as operações agregadas são realizadas no banco de dados. Talvez haja diferenças nos resultados de uma consulta executada na memória e de uma consulta executada no banco de dados. Com uma consulta de memória, se não houver nenhuma correspondência, a consulta retornará zero. No banco de dados, a mesma consulta retorna `null`. Se `null` um valor for passado para uma função agregada LINQ, uma exceção será lançada. Para aceitar `null` possíveis valores, lance os tipos e as propriedades dos tipos que recebem resultados de consulta para tipos de valoranulados.  
  
## <a name="see-also"></a>Confira também

- [Expressões em consultas LINQ to Entities](expressions-in-linq-to-entities-queries.md)
