---
title: Funções agregadas (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 113c19078feeca24a0817e52f8eb0d04537b0684
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104917"
---
# <a name="aggregate-functions-entity-sql"></a>Funções agregadas (Entity SQL)
Uma agregação é uma construção de linguagem que condense uma coleção em um escalar como parte de uma operação de grupo. as agregações de[!INCLUDE[esql](../../../../../../includes/esql-md.md)] vêm em duas formas:  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funções de coleção que podem ser usadas em qualquer lugar em uma expressão. Isso inclui usando funções agregadas em projeções e predicados que atuam em coleções. Funções de coleção são o modo preferido para especificar agregados em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
-   O grupo agrega as expressões de consulta que têm um cláusula GROUP BY. Como em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], agregados do grupo aceitam DISTINCT e ALL como modificadores a entrada aggregate.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] primeiro tenta interpretar uma expressão como uma função de coleção e se a expressão é no contexto de uma expressão SELECT ele interpretará como uma agregação de grupo.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] define um operador aggregate especial chamado [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md). Este operador permite que você obtenha uma referência ao conjunto agrupado de entrada. Isso permite uma consultas mais avançados de agrupamento, onde os resultados de cláusula GROUP BY podem ser usados em locais diferentes funções de agregação ou a coleção de grupo.  
  
## <a name="collection-functions"></a>Funções de coleção  
 Funções de coleção operam em coleções e retornam um valor escalar. Por exemplo, se `orders` é uma coleção de qualquer `orders`, você pode calcular a data de enviar a mais recente com a expressão a seguir:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Agregados do grupo  
 Agregados de grupo são calculadas em um resultado de grupo como definidas por cláusula GROUP BY. O cláusula GROUP BY divide dados em grupos. Para cada grupo em resultado, a função agregada é aplicada e uma agregação separada é calculada usando elementos em cada grupo como entradas para o cálculo agregado. Quando um cláusula GROUP BY é usado em uma expressão SELECT, simplesmente agrupamento nomes de expressão, agregados, ou expressões constantes podem estar presente na projeção, em cláusula HAVING ou ORDER BY.  
  
 O exemplo a seguir calcula a média quantidade ordenada para cada produto.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 É possível ter uma agregação do grupo sem um GRUPO explícito pela cláusula SELECT na expressão. Todos os elementos serão tratados como um único grupo, equivalente a exemplos de especificar um agrupamento com base em uma constante.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 As expressões em GRUPO usadas pela cláusula são avaliadas usando o mesmo escopo de resolução que seria visível para a cláusula WHERE expressão.  
  
## <a name="see-also"></a>Consulte também

- [Funções](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
