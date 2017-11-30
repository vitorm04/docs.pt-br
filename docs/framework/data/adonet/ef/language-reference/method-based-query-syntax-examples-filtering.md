---
title: "Exemplos de sintaxe da consulta baseada em método: filtragem"
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
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b81e163a6d326135f8031c6ef43af698d9c706b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="method-based-query-syntax-examples-filtering"></a>Exemplos de sintaxe da consulta baseada em método: filtragem
Os exemplos neste tópico demonstram como usar o `Where` e `Where…Contains` métodos para consultar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) usando a sintaxe de consulta com base em método. Observe que, onde...`Contains` não pode ser usado como parte de um [compilado consulta](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
 O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.  
  
 Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a>Where  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir retorna todos os pedidos online.  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir retorna os pedidos onde a quantidade é maior que 2 e menor que 6.  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir retorna todos os produtos vermelhos.  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir usa o método `Where` para localizar os pedidos que foram feitos depois de 1° de dezembro de 2003 e, em seguida, usa a propriedade de navegação `order.SalesOrderDetail` para obter os detalhes de cada pedido.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a>Where…Contains  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma matriz como parte de uma cláusula `Where…Contains` para localizar todos os produtos que têm um `ProductModelID` que coincide com um valor na matriz.  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
>  Como parte do predicado em uma cláusula `Where…Contains`, você pode usar um <xref:System.Array>, <xref:System.Collections.Generic.List%601> ou uma coleção de qualquer tipo que implemente a interface de <xref:System.Collections.Generic.IEnumerable%601>. Você também pode declarar e inicializar uma coleção em uma consulta LINQ to Entities. Consulte o próximo exemplo para obter mais informações.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir declara e inicializa matrizes em uma cláusula `Where…Contains` para localizar todos os produtos que têm um `ProductModelID` ou um `Size` que coincide com um valor nas matrizes.  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Consultas no LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
