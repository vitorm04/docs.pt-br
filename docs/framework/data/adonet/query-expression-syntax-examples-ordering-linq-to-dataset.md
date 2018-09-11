---
title: 'Exemplos de sintaxe da expressão de consulta: Ordenação (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: 1e3ee4372c1c2173cff0d93dfdf84c96c60130d4
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342112"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a>Exemplos de sintaxe da expressão de consulta: Ordenação (LINQ to DataSet)
Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, e métodos de <xref:System.Linq.Enumerable.ThenByDescending%2A> para ver <xref:System.Data.DataSet> e para ordenar os resultados usando a sintaxe da expressão de consulta.  
  
 O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.  
  
 Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Para obter mais informações, consulte [como: criar um LINQ to DataSet de projeto no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="orderby"></a>OrderBy  
  
### <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> para retornar uma lista de contatos ordenados por sobrenome.  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> para classificar uma lista de contatos pelo comprimento do sobrenome.  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a>OrderByDescending  
  
### <a name="example"></a>Exemplo  
 Este exemplo usa `orderby… descending` (`Order By … Descending`), que é equivalente ao método de <xref:System.Linq.Enumerable.OrderByDescending%2A> , para classificar a tabela de preços de mais alto para o menor.  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a>Inverso  
  
### <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Linq.Enumerable.Reverse%2A> para criar uma lista de pedidos onde `OrderDate` for anterior do 20 de fevereiro de 2002.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a>ThenByDescending  
  
### <a name="example"></a>Exemplo  
 Este exemplo usa `OrderBy… Descending` , que é equivalente ao método de <xref:System.Linq.Enumerable.ThenByDescending%2A> , para classificar uma lista de produtos, principalmente por nome e em seguida pelo custo da tabela, o mais alto para o menor.  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a>Consulte também  
 [Carregar dados para um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Exemplos de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Visão Geral de Operadores de Consulta Padrão](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
