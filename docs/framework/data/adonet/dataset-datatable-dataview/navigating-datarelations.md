---
title: Navegando em DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: c46007fb86a76405fd99d6e943779238d6885aa8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="navigating-datarelations"></a>Navegando em DataRelations
Uma das principais funções de um <xref:System.Data.DataRelation> é permitir a navegação de um <xref:System.Data.DataTable> para outro em um <xref:System.Data.DataSet>. Isso permite que você recupere todos relacionado <xref:System.Data.DataRow> objetos em um **DataTable** quando é fornecido um único **DataRow** de um relacionados **DataTable**. Por exemplo, depois de estabelecer um **DataRelation** entre uma tabela de clientes e uma tabela de pedidos, você pode recuperar todas as linhas de ordem para uma linha de cliente específico usando **GetChildRows**.  
  
 O exemplo de código a seguir cria um **DataRelation** entre o **clientes** tabela e o **pedidos** tabela de uma **conjunto de dados** e retorna todos os pedidos para cada cliente.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 O exemplo a seguir se baseia no exemplo anterior, relacionando quatro tabelas juntas e navegando nessas relações. Como no exemplo anterior, **CustomerID** relaciona o **clientes** de tabela para o **pedidos** tabela. Para cada cliente no **clientes** tabela, todas as linhas filho no **pedidos** tabela são determinados, para retornar o número de pedidos de um cliente específico tiver e seus **OrderID** valores.  
  
 O exemplo expandido também retorna os valores da **OrderDetails** e **produtos** tabelas. O **pedidos** tabela está relacionada ao **OrderDetails** tabela usando **OrderID** para determinar para cada pedido do cliente, que produtos e quantidades foram solicitadas. Porque o **OrderDetails** tabela contém apenas o **ProductID** de um produto pedido, **OrderDetails** está relacionado à **produtos** usando **ProductID** para retornar o **ProductName**. Nessa relação, o **produtos** tabela é o pai e o **Order Details** tabela é o filho. Como resultado, ao fazer a iteração por meio de **OrderDetails** tabela, **GetParentRow** é chamado para recuperar o relacionados **ProductName** valor.  
  
 Observe que, quando o **DataRelation** é criado para o **clientes** e **pedidos** tabelas, nenhum valor for especificado para o **createConstraints**sinalizador (o padrão é **true**). Isso pressupõe que todas as linhas no **pedidos** tabela ter um **CustomerID** valor existe no pai **clientes** tabela. Se um **CustomerID** existe no **pedidos** que não existe na tabela a **clientes** tabela, um <xref:System.Data.ForeignKeyConstraint> faz com que uma exceção seja lançada.  
  
 Quando a coluna filho pode conter valores que não contém a coluna pai, defina o **createConstraints** sinalizador como **false** ao adicionar o **DataRelation**. No exemplo, o **createConstraints** sinalizador é definido como **false** para o **DataRelation** entre o **pedidos** tabela e o  **OrderDetails** tabela. Isso permite que o aplicativo retornar todos os registros da **OrderDetails** tabela e apenas um subconjunto de registros da **pedidos** tabela sem gerar uma exceção de tempo de execução. O exemplo expandido gera saída no formato a seguir.  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 O exemplo de código a seguir é um exemplo de expandido onde os valores da **OrderDetails** e **produtos** tabelas são retornadas, com apenas um subconjunto dos registros da **pedidos**tabela que está sendo retornada.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
