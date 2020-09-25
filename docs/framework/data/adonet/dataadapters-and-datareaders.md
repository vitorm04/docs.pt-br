---
title: DataAdapters e DataReaders
description: Saiba mais sobre o ADO.NET DataReader, que recupera dados de um banco de dados, e DataAdapter, que recupera dados de uma fonte e popula um DataSet.
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 2584f8b382dd90f2f8b4554663dc545b9ccceb62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177599"
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="ef0c1-103">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="ef0c1-103">DataAdapters and DataReaders</span></span>

<span data-ttu-id="ef0c1-104">Você pode usar o **DataReader** ADO.net para recuperar um fluxo de dados somente leitura e somente encaminhamento de um banco de dado.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-104">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="ef0c1-105">Os resultados são retornados conforme a consulta é executada e são armazenados no buffer de rede no cliente até que você os solicite usando o método **Read** do **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-105">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="ef0c1-106">Usar o **DataReader** pode aumentar o desempenho do aplicativo recuperando dados assim que ele estiver disponível e (por padrão) armazenando apenas uma linha de cada vez na memória, reduzindo a sobrecarga do sistema.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-106">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="ef0c1-107">Um <xref:System.Data.Common.DataAdapter> é usado para recuperar dados de uma fonte de dados e para popular tabelas em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-107">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ef0c1-108">O `DataAdapter` também resolve as alterações feitas no `DataSet` de volta para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-108">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="ef0c1-109">O `DataAdapter` usa o objeto `Connection` do provedor de dados .NET Framework para se conectar a uma fonte de dados e usa objetos de `Command` para recuperar dados e para resolver alterações na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-109">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="ef0c1-110">Cada provedor de dados .NET Framework incluído com o .NET Framework tem um <xref:System.Data.Common.DbDataReader> e um objeto <xref:System.Data.Common.DbDataAdapter>: o Provedor de Dados .NET Framework para OLE DB inclui um <xref:System.Data.OleDb.OleDbDataReader> e um objeto <xref:System.Data.OleDb.OleDbDataAdapter>, o Provedor de Dados .NET Framework para SQL Server inclui um <xref:System.Data.SqlClient.SqlDataReader> e um objeto <xref:System.Data.SqlClient.SqlDataAdapter>, o Provedor de Dados .NET Framework para ODBC inclui um <xref:System.Data.Odbc.OdbcDataReader> e um objeto <xref:System.Data.Odbc.OdbcDataAdapter> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleDataReader> e um objeto <xref:System.Data.OracleClient.OracleDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-110">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef0c1-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ef0c1-111">In This Section</span></span>  

 [<span data-ttu-id="ef0c1-112">Recuperando dados usando um DataReader</span><span class="sxs-lookup"><span data-stu-id="ef0c1-112">Retrieving Data Using a DataReader</span></span>](retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="ef0c1-113">Descreve o objeto ADO.NET **DataReader** e como usá-lo para retornar um fluxo de resultados de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-113">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="ef0c1-114">Populando um DataSet a partir de um DataAdapter</span><span class="sxs-lookup"><span data-stu-id="ef0c1-114">Populating a DataSet from a DataAdapter</span></span>](populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="ef0c1-115">Descreve como preencher um `DataSet` com tabelas, colunas, e linhas usando um `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-115">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="ef0c1-116">Parâmetros DataAdapter</span><span class="sxs-lookup"><span data-stu-id="ef0c1-116">DataAdapter Parameters</span></span>](dataadapter-parameters.md)  
 <span data-ttu-id="ef0c1-117">Descreve como usar parâmetros com as propriedades de comando de um `DataAdapter` incluindo como mapear o conteúdo de uma coluna em um `DataSet` para um parâmetro de comando.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-117">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="ef0c1-118">Adicionar restrições existentes a um DataSet</span><span class="sxs-lookup"><span data-stu-id="ef0c1-118">Adding Existing Constraints to a DataSet</span></span>](adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="ef0c1-119">Descreve como adicionar as restrições existentes a um `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-119">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="ef0c1-120">Mapeamentos de DataTable e de DataColumn do DataAdapter</span><span class="sxs-lookup"><span data-stu-id="ef0c1-120">DataAdapter DataTable and DataColumn Mappings</span></span>](dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="ef0c1-121">Descreve como configurar `DataTableMappings` e `ColumnMappings` para um `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-121">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="ef0c1-122">Paginação por um resultado de consulta</span><span class="sxs-lookup"><span data-stu-id="ef0c1-122">Paging Through a Query Result</span></span>](paging-through-a-query-result.md)  
 <span data-ttu-id="ef0c1-123">Fornece um exemplo de como exibir os resultados de uma consulta como páginas de dados.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-123">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="ef0c1-124">Atualizando fontes de dados com DataAdapters</span><span class="sxs-lookup"><span data-stu-id="ef0c1-124">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="ef0c1-125">Descreve como usar um `DataAdapter` para resolver alterações em um `DataSet` de volta para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-125">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="ef0c1-126">Manipulação de eventos DataAdapter</span><span class="sxs-lookup"><span data-stu-id="ef0c1-126">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)  
 <span data-ttu-id="ef0c1-127">Descreve os eventos do `DataAdapter` e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-127">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="ef0c1-128">Executando operações em lote usando DataAdapters</span><span class="sxs-lookup"><span data-stu-id="ef0c1-128">Performing Batch Operations Using DataAdapters</span></span>](performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="ef0c1-129">Descreve como melhorar o desempenho do aplicativo reduzindo o número de viagens de ida e volta ao SQL Server para aplicar atualizações do `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="ef0c1-129">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef0c1-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="ef0c1-130">See also</span></span>

- [<span data-ttu-id="ef0c1-131">Conectando a uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="ef0c1-131">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="ef0c1-132">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef0c1-132">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="ef0c1-133">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="ef0c1-133">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="ef0c1-134">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="ef0c1-134">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="ef0c1-135">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ef0c1-135">ADO.NET Overview</span></span>](ado-net-overview.md)
