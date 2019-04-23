---
title: Navegando em DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: f4dfccad23bf5d15f5cbd0a33e76a136417e13ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204153"
---
# <a name="navigating-datarelations"></a>Navegando em DataRelations
Uma das principais funções de um <xref:System.Data.DataRelation> é permitir a navegação de um <xref:System.Data.DataTable> para outro em um <xref:System.Data.DataSet>. Isso permite que você recupere todos os relacionado <xref:System.Data.DataRow> objetos em um **DataTable** quando receber um único **DataRow** de um relacionados **DataTable**. Por exemplo, depois de estabelecer uma **DataRelation** entre uma tabela de clientes e uma tabela de pedidos, você pode recuperar todas as linhas de pedido para uma linha de cliente específico usando **GetChildRows**.  
  
 O exemplo de código a seguir cria uma **DataRelation** entre o **clientes** tabela e o **pedidos** tabela de uma **DataSet** e retorna todos os pedidos para cada cliente.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 O exemplo a seguir se baseia no exemplo anterior, relacionando quatro tabelas juntas e navegando nessas relações. Como no exemplo anterior, **CustomerID** está relacionado a **clientes** de tabela para o **pedidos** tabela. Para cada cliente na **clientes** da tabela, todas as linhas filho na **pedidos** tabela são determinadas, para retornar o número de pedidos de um cliente específico e seus **OrderID** valores.  
  
 O exemplo expandido também retorna os valores da **OrderDetails** e **produtos** tabelas. O **pedidos** tabela está relacionada com o **OrderDetails** tabela usando **OrderID** para determinar, para cada pedido de cliente, quais produtos e quantidades pedidas. Porque o **OrderDetails** tabela contém somente os **ProductID** de um produto pedido, **OrderDetails** está relacionado à **produtos** usando o **ProductID** para retornar o **ProductName**. Nessa relação, o **produtos** tabela é o pai e o **detalhes do pedido** tabela é o filho. Como resultado, ao iterar por meio de **OrderDetails** tabela, **GetParentRow** é chamado para recuperar o relacionados **ProductName** valor.  
  
 Observe que, quando o **DataRelation** é criado para o **clientes** e **pedidos** tabelas, nenhum valor for especificado para o **createConstraints**sinalizador (o padrão é **verdadeira**). Isso pressupõe que todas as linhas na **pedidos** tabela ter um **CustomerID** valor existe no pai **clientes** tabela. Se um **CustomerID** existe na **pedidos** que não existe na tabela a **clientes** tabela, um <xref:System.Data.ForeignKeyConstraint> faz com que uma exceção seja lançada.  
  
 Quando a coluna filho pode conter valores que não contém a coluna pai, defina as **createConstraints** sinalizador como **falso** ao adicionar o **DataRelation**. No exemplo, o **createConstraints** sinalizador é definido como **falso** para o **DataRelation** entre o **pedidos** tabela e o  **OrderDetails** tabela. Isso permite que o aplicativo para retornar todos os registros do **OrderDetails** tabela e apenas um subconjunto de registros da **pedidos** tabela sem gerar uma exceção de tempo de execução. O exemplo expandido gera saída no formato a seguir.  
  
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
  
 O exemplo de código a seguir é um exemplo expandido em que os valores da **OrderDetails** e **produtos** tabelas forem retornadas, com apenas um subconjunto dos registros no **pedidos**tabela que está sendo retornada.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
