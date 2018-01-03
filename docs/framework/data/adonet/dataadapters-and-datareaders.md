---
title: DataAdapters e DataReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6d071622862a645d11ea8228574f81d5f8c3e6e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dataadapters-and-datareaders"></a>DataAdapters e DataReaders
Você pode usar o ADO.NET **DataReader** para recuperar um fluxo de dados somente leitura, somente encaminhamento de um banco de dados. Os resultados são retornados como a consulta é executada e são armazenados no buffer de rede no cliente até que você os solicita usando o **leitura** método o **DataReader**. Usando o **DataReader** pode aumentar o desempenho do aplicativo ao recuperar dados assim que ele está disponível e (por padrão) armazenar apenas uma linha por vez na memória, reduzindo a sobrecarga do sistema.  
  
 Um <xref:System.Data.Common.DataAdapter> é usado para recuperar dados de uma fonte de dados e para popular tabelas em um <xref:System.Data.DataSet>. O `DataAdapter` também resolve as alterações feitas no `DataSet` de volta para a fonte de dados. O `DataAdapter` usa o objeto `Connection` do provedor de dados .NET Framework para se conectar a uma fonte de dados e usa objetos de `Command` para recuperar dados e para resolver alterações na fonte de dados.  
  
 Cada provedor de dados .NET Framework incluído com o .NET Framework tem um <xref:System.Data.Common.DbDataReader> e um objeto <xref:System.Data.Common.DbDataAdapter>: o Provedor de Dados .NET Framework para OLE DB inclui um <xref:System.Data.OleDb.OleDbDataReader> e um objeto <xref:System.Data.OleDb.OleDbDataAdapter>, o Provedor de Dados .NET Framework para SQL Server inclui um <xref:System.Data.SqlClient.SqlDataReader> e um objeto <xref:System.Data.SqlClient.SqlDataAdapter>, o Provedor de Dados .NET Framework para ODBC inclui um <xref:System.Data.Odbc.OdbcDataReader> e um objeto <xref:System.Data.Odbc.OdbcDataAdapter> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleDataReader> e um objeto <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Recuperando dados usando um DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 Descreve o ADO.NET **DataReader** objeto e como usá-lo para retornar um fluxo de resultados de uma fonte de dados.  
  
 [Populating a DataSet from a DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)  
 Descreve como preencher um `DataSet` com tabelas, colunas, e linhas usando um `DataAdapter`.  
  
 [Parâmetros DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Descreve como usar parâmetros com as propriedades de comando de um `DataAdapter` incluindo como mapear o conteúdo de uma coluna em um `DataSet` para um parâmetro de comando.  
  
 [Adding Existing Constraints to a DataSet](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md) (Adicionando restrições existentes a um DataSet)  
 Descreve como adicionar as restrições existentes a um `DataSet`.  
  
 [Mapeamentos de DataTable e de DataColumn do DataAdapter](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 Descreve como configurar `DataTableMappings` e `ColumnMappings` para um `DataAdapter`.  
  
 [Paginação por um resultado de consulta](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Fornece um exemplo de como exibir os resultados de uma consulta como páginas de dados.  
  
 [Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)  
 Descreve como usar um `DataAdapter` para resolver alterações em um `DataSet` de volta para o banco de dados.  
  
 [Manipulação de eventos DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 Descreve os eventos do `DataAdapter` e como usá-los.  
  
 [Executando operações em lote usando DataAdapters](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 Descreve como melhorar o desempenho do aplicativo reduzindo o número de viagens de ida e volta ao SQL Server para aplicar atualizações do `DataSet`.  
  
## <a name="see-also"></a>Consulte também  
 [Conectando a uma fonte de dados](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
