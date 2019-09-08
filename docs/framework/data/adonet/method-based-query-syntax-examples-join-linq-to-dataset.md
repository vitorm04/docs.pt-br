---
title: 'Exemplos de sintaxe de consulta baseada em método: Junção (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: ba6e33f98e063aab946db27b97106272c5adef63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783665"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a>Exemplos de sintaxe de consulta baseada em método: Junção (LINQ to DataSet)
A junção é uma operação importante em consultas que usam fontes de dados de destino que não têm nenhuma relação navegável entre si, como, por exemplo, as tabelas do banco de dados relacional. Uma junção de duas fontes de dados é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados. Para obter mais informações, consulte Visão geral [dos operadoresC#de consulta Standard ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ou [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Os exemplos neste tópico demonstram como usar o método de <xref:System.Linq.Enumerable.Join%2A> para ver <xref:System.Data.DataSet> usando a sintaxe da consulta de método.  
  
 O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).  
  
 Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.  
  
 Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Para obter mais informações, confira [Como: Crie um projeto LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="join"></a>Join  
  
### <a name="example"></a>Exemplo  
 Este exemplo reproduz uma união sobre as tabelas de `Contact` e de `SalesOrderHeader` .  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a>Exemplo  
 Este exemplo reproduz uma união sobre as tabelas de `Contact` e de `SalesOrderHeader` , agrupamento os resultados pela identificação de contatos  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a>Consulte também

- [Carregar dados para um conjunto de dados](loading-data-into-a-dataset.md)
- [Exemplos de LINQ to DataSet](linq-to-dataset-examples.md)
- [Visão geral de operadores de consulta padrão (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Visão geral de operadores de consulta padrão (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Exemplos de junção](https://go.microsoft.com/fwlink/?LinkId=187357)
- [Exemplos de conjuntos de conjunto](https://go.microsoft.com/fwlink/?LinkId=187358)
