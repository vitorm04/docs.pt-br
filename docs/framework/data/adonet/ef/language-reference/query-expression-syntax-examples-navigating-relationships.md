---
title: 'Exemplos de sintaxe da expressão de consulta: Navegando em relações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: e4297400bd7e76ca6202748d8f14d478364c1275
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>Exemplos de sintaxe da expressão de consulta: Navegando em relações
Propriedades de navegação no [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] são propriedades do atalho usadas para localizar as entidades nas extremidades de uma associação. As propriedades de navegação permitem que um usuário navegue de uma entidade para outra, ou uma entidade a entidades relacionadas por um conjunto de associações. Este tópico fornece exemplos na sintaxe da expressão de consulta de como navegar em relações entre as propriedades de navegação em consultas de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .  
  
 O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.  
  
 Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o método de <xref:System.Linq.Queryable.Select%2A> para obter todos os IDs de contato e soma total de vencido para cada contato cujo nome é “Zhou”. A propriedade de navegação de `Contact.SalesOrderHeader` é usada para obter a coleção de objetos `SalesOrderHeader` para cada contato. O método de `Sum` usa a propriedade de navegação de `Contact.SalesOrderHeader` para somar o total vencido de todos os pedidos para cada contato.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém todos os pedidos de contatos cujo nome é “Zhou”. A propriedade de navegação de `Contact.SalesOrderHeader` é usada para obter a coleção de objetos `SalesOrderHeader` para cada contato. O nome e os pedidos de contato são retornados em um tipo anônimo.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `SalesOrderHeader.Address` e propriedades de navegação de `SalesOrderHeader.Contact` obtém a coleção de `Address` e `Contact` objetos associado com cada pedido. O primeiro contato, endereço, o número de ordem de venda, e o total vencido para cada pedido a cidade de Seattle são retornados em um tipo anônimo.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir usa o método `Where` para localizar os pedidos que foram feitos depois de 1° de dezembro de 2003 e, em seguida, usa a propriedade de navegação `order.SalesOrderDetail` para obter os detalhes de cada pedido.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Consulte também  
 [Consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
