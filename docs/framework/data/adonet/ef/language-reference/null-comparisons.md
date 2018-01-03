---
title: "Comparações nulas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b29caeed4bf60a5a7ad723ffd46520a89a5bd87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="null-comparisons"></a>Comparações nulas
Um valor `null` na fonte de dados indica que o valor é desconhecido. Nas consultas do [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], você pode procurar valores nulos de modo que determinados cálculos ou comparações só sejam executados nas linhas que têm dados válidos ou não nulos. A semântica nula do CLR, no entanto, pode diferir da semântica nula da fonte de dados. A maioria dos bancos de dados usa uma versão da lógica de três valores para manipular comparações nulas. Ou seja, uma comparação com um valor nulo não é avaliada como `true` ou `false`, ele será avaliado como `unknown`. Geralmente, essa é uma implementação de valores nulos ANSI, mas isso nem sempre acontece.  
  
 Por padrão, no SQL Server, a comparação nulo igual a nulo retorna um valor nulo. No exemplo a seguir, as linhas em que `ShipDate` é null serão excluídas do conjunto de resultados, e a instrução [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] retornará 0 linhas.  
  
```  
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
 Um *seletor de chave* é uma função usada em operadores de consulta padrão para extrair uma chave de um elemento. Na função do seletor de chave, uma expressão pode ser comparada a uma constante. A semântica nula do CLR será exibida se uma expressão for comparada com uma constante nula ou se duas constantes nulas forem comparadas. As semânticas nulas de armazenamento serão exibidas se duas colunas com valores nulos na fonte de dados forem comparadas. Os seletores de chave são encontrados em muitos operadores de consulta padrão de agrupamento e ordenação, como <xref:System.Linq.Queryable.GroupBy%2A>, e usados para selecionar as chaves que servirão de base para a ordenação ou o agrupamento do resultados da consulta.  
  
## <a name="null-property-on-a-null-object"></a>Propriedade nula em um objeto nulo  
 No [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], as propriedades de um objeto nulo são nulas. Ao tentar fazer referência à propriedade de um objeto nulo no CLR, você receberá <xref:System.NullReferenceException>. Quando uma consulta LINQ envolver uma propriedade de um objeto nulo, o resultado possivelmente será um comportamento inconsistente.  
  
 Por exemplo, na consulta a seguir, a conversão em `NewProduct` é feita na camada da árvore de comandos, que pode resultar na propriedade `Introduced` que está sendo nula. Se o banco de dados tiver definido comparações nulas, como a comparação <xref:System.DateTime> que é avaliada como true, a linha será incluída.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Passando coleções nulas para funções agregadas  
 Em [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], quando você passar uma coleção que dá suporte a `IQueryable` para uma função de agregação, operações de agregação são executadas no banco de dados. Pode haver diferenças nos resultados de uma consulta que foi executada na memória e uma consulta que foi executada no banco de dados. Com uma consulta na memória, se não houver nenhuma correspondência, a consulta retorna zero. No banco de dados, a mesma consulta retorna `null`. Se um `null` valor é passado para uma função de agregação LINQ, uma exceção será lançada. Para aceitar possível `null` valores, converter os tipos e as propriedades dos tipos de recebem os resultados de consulta para tipos anuláveis.  
  
## <a name="see-also"></a>Consulte também  
 [Expressões em consultas LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
