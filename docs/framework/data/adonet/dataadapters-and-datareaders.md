---
title: DataAdapters e DataReaders
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 20c6d514e70d2e4db451e0fff02e72688bf7d0ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786644"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapters e DataReaders
Você pode usar o **DataReader** ADO.net para recuperar um fluxo de dados somente leitura e somente encaminhamento de um banco de dado. Os resultados são retornados conforme a consulta é executada e são armazenados no buffer de rede no cliente até que você os solicite usando o método **Read** do **DataReader**. Usar o **DataReader** pode aumentar o desempenho do aplicativo recuperando dados assim que ele estiver disponível e (por padrão) armazenando apenas uma linha de cada vez na memória, reduzindo a sobrecarga do sistema.  
  
 Um <xref:System.Data.Common.DataAdapter> é usado para recuperar dados de uma fonte de dados e para popular tabelas em um <xref:System.Data.DataSet>. O `DataAdapter` também resolve as alterações feitas no `DataSet` de volta para a fonte de dados. O `DataAdapter` usa o objeto `Connection` do provedor de dados .NET Framework para se conectar a uma fonte de dados e usa objetos de `Command` para recuperar dados e para resolver alterações na fonte de dados.  
  
 Cada provedor de dados .NET Framework incluído com o .NET Framework tem um <xref:System.Data.Common.DbDataReader> e um objeto <xref:System.Data.Common.DbDataAdapter>: o Provedor de Dados .NET Framework para OLE DB inclui um <xref:System.Data.OleDb.OleDbDataReader> e um objeto <xref:System.Data.OleDb.OleDbDataAdapter>, o Provedor de Dados .NET Framework para SQL Server inclui um <xref:System.Data.SqlClient.SqlDataReader> e um objeto <xref:System.Data.SqlClient.SqlDataAdapter>, o Provedor de Dados .NET Framework para ODBC inclui um <xref:System.Data.Odbc.OdbcDataReader> e um objeto <xref:System.Data.Odbc.OdbcDataAdapter> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleDataReader> e um objeto <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Recuperando dados usando um DataReader](retrieving-data-using-a-datareader.md)  
 Descreve o objeto ADO.NET **DataReader** e como usá-lo para retornar um fluxo de resultados de uma fonte de dados.  
  
 [Populating a DataSet from a DataAdapter](populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)  
 Descreve como preencher um `DataSet` com tabelas, colunas, e linhas usando um `DataAdapter`.  
  
 [Parâmetros DataAdapter](dataadapter-parameters.md)  
 Descreve como usar parâmetros com as propriedades de comando de um `DataAdapter` incluindo como mapear o conteúdo de uma coluna em um `DataSet` para um parâmetro de comando.  
  
 [Adding Existing Constraints to a DataSet](adding-existing-constraints-to-a-dataset.md) (Adicionando restrições existentes a um DataSet)  
 Descreve como adicionar as restrições existentes a um `DataSet`.  
  
 [Mapeamentos de DataTable e de DataColumn do DataAdapter](dataadapter-datatable-and-datacolumn-mappings.md)  
 Descreve como configurar `DataTableMappings` e `ColumnMappings` para um `DataAdapter`.  
  
 [Paginação por um resultado de consulta](paging-through-a-query-result.md)  
 Fornece um exemplo de como exibir os resultados de uma consulta como páginas de dados.  
  
 [Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)  
 Descreve como usar um `DataAdapter` para resolver alterações em um `DataSet` de volta para o banco de dados.  
  
 [Manipulação de eventos DataAdapter](handling-dataadapter-events.md)  
 Descreve os eventos do `DataAdapter` e como usá-los.  
  
 [Executando operações em lote usando DataAdapters](performing-batch-operations-using-dataadapters.md)  
 Descreve como melhorar o desempenho do aplicativo reduzindo o número de viagens de ida e volta ao SQL Server para aplicar atualizações do `DataSet`.  
  
## <a name="see-also"></a>Consulte também

- [Conectando a uma fonte de dados](connecting-to-a-data-source.md)
- [Comandos e parâmetros](commands-and-parameters.md)
- [Transações e simultaneidade](transactions-and-concurrency.md)
- [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
