---
title: 'Exemplos de sintaxe da expressão de consulta: Divisão (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 9f907d16c78b550fbc11cc2cfad3c8249966a2f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189026"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a>Exemplos de sintaxe da expressão de consulta: Divisão (LINQ to DataSet)

Os exemplos neste tópico demonstram como usar os métodos <xref:System.Linq.Enumerable.Skip%2A> e <xref:System.Linq.Enumerable.Take%2A> para consultar um <xref:System.Data.DataSet> usando a sintaxe de expressão de consulta.  
  
 O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).  
  
 Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.  
  
 Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Para obter mais informações, consulte [como: criar um projeto de LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="skip"></a>Ignorar  
  
### <a name="example"></a>Exemplo  

 Este exemplo usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter todos mas os dois primeiros endereços em Seattle.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a>Take  
  
### <a name="example"></a>Exemplo  

 Este exemplo usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter os três primeiros endereços em Seattle.  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a>Veja também

- [Carregando dados em um DataSet](loading-data-into-a-dataset.md)
- [LINQ para exemplos de DataSet](linq-to-dataset-examples.md)
- [Visão geral de operadores de consulta padrão (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Visão geral de operadores de consulta padrão (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
