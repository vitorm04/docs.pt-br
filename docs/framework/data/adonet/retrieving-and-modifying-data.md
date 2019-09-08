---
title: Recuperando e modificando dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 78012a6a5ecdfac0e4cd7c4939ae3ab0036ab716
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782854"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="3c275-102">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3c275-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="3c275-103">A função principal de qualquer aplicativo de banco de dados é conectar-se a uma fonte de dados e recuperar os dados que ele contém.</span><span class="sxs-lookup"><span data-stu-id="3c275-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="3c275-104">Os .NET Framework provedores de dados do ADO.NET servem como uma ponte entre um aplicativo e uma fonte de dados, permitindo que você execute comandos, bem como recuperar dados usando um **DataReader** ou um **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="3c275-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="3c275-105">A função principal de qualquer aplicativo de banco de dados é a capacidade de atualizar os dados que estão armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3c275-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="3c275-106">No ADO.net, a atualização de dados envolve o uso <xref:System.Data.DataSet>de DataAdapter e e de objetos **Command** ; e também pode envolver o uso de transações.</span><span class="sxs-lookup"><span data-stu-id="3c275-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c275-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3c275-107">In This Section</span></span>  
 [<span data-ttu-id="3c275-108">Conectando a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="3c275-108">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="3c275-109">Descreve como estabelecer uma conexão com uma fonte de dados e como trabalhar com eventos de conexão.</span><span class="sxs-lookup"><span data-stu-id="3c275-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="3c275-110">Cadeia de Conexão</span><span class="sxs-lookup"><span data-stu-id="3c275-110">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="3c275-111">Contém os tópicos que descrevem os vários aspectos do uso de cadeias de conexão, incluindo palavras-chave de cadeias de conexão, informações de segurança e seu respectivo armazenamento e recuperação.</span><span class="sxs-lookup"><span data-stu-id="3c275-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="3c275-112">Pooling de Conexão</span><span class="sxs-lookup"><span data-stu-id="3c275-112">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="3c275-113">Descreve o pool de conexões para provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c275-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="3c275-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c275-114">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="3c275-115">Contém os tópicos que descrevem como criar comandos e construtores de comandos, configurar parâmetros e executar comandos para recuperar e modificar dados.</span><span class="sxs-lookup"><span data-stu-id="3c275-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="3c275-116">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="3c275-116">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="3c275-117">Contém os tópicos que descrevem DataReaders, DataAdapters, parâmetros, manipulação de eventos DataAdapter e execução de operações em lote.</span><span class="sxs-lookup"><span data-stu-id="3c275-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="3c275-118">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="3c275-118">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="3c275-119">Contém os tópicos que descrevem como executar transações locais, transações distribuídas e trabalho com concorrência otimista.</span><span class="sxs-lookup"><span data-stu-id="3c275-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="3c275-120">Recuperando identidade ou valores de Autonumber</span><span class="sxs-lookup"><span data-stu-id="3c275-120">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="3c275-121">Fornece um exemplo de mapeamento dos valores gerados para uma coluna de **identidade** em uma tabela SQL Server ou para um campo **AutoNumeração** em uma tabela do Microsoft Access, para uma coluna de uma linha inserida em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="3c275-121">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="3c275-122">Discute como mesclar valores de identidade em `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="3c275-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="3c275-123">Recuperando dados binários</span><span class="sxs-lookup"><span data-stu-id="3c275-123">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="3c275-124">Descreve como recuperar dados binários ou estruturas de dados grandes `CommandBehavior`usando o.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="3c275-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="3c275-125">para modificar o comportamento padrão de um `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="3c275-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="3c275-126">Modificando dados com procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="3c275-126">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="3c275-127">Descreve como usar parâmetros de entrada e de saída de procedimentos armazenados para inserir uma linha em um banco de dados, retornando um novo valor de identidade.</span><span class="sxs-lookup"><span data-stu-id="3c275-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="3c275-128">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="3c275-128">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="3c275-129">Descreve como obter bancos de dados ou catálogos disponíveis, tabelas e modos de exibição em um banco de dados, restrições existentes para tabelas e outras informações de esquema de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3c275-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="3c275-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="3c275-130">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="3c275-131">Descreve o modelo de fábrica do provedor e demonstra como usar as classes base no namespace `System.Data.Common`.</span><span class="sxs-lookup"><span data-stu-id="3c275-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="3c275-132">Rastreamento de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3c275-132">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="3c275-133">Descreve como o ADO.NET fornece a funcionalidade interna de rastreamento de dados.</span><span class="sxs-lookup"><span data-stu-id="3c275-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="3c275-134">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="3c275-134">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="3c275-135">Descreve os contadores de desempenho disponíveis para `SqlClient` e `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="3c275-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="3c275-136">Programação Assíncrona</span><span class="sxs-lookup"><span data-stu-id="3c275-136">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="3c275-137">Descreve o suporte do ADO.NET para programação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="3c275-137">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="3c275-138">Suporte de Streaming do SqlClient</span><span class="sxs-lookup"><span data-stu-id="3c275-138">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="3c275-139">Discute como escrever aplicativos que transmitem dados de SQL Server sem tê-los totalmente carregados na memória.</span><span class="sxs-lookup"><span data-stu-id="3c275-139">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c275-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c275-140">See also</span></span>

- <span data-ttu-id="3c275-141">[Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3c275-141">[Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md)</span></span>
- <span data-ttu-id="3c275-142">[DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="3c275-142">[DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="3c275-143">[Securing ADO.NET Applications](securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3c275-143">[Securing ADO.NET Applications](securing-ado-net-applications.md)</span></span>
- <span data-ttu-id="3c275-144">[SQL Server and ADO.NET](./sql/index.md) (SQL Server e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3c275-144">[SQL Server and ADO.NET](./sql/index.md)</span></span>
- <span data-ttu-id="3c275-145">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3c275-145">[ADO.NET Overview](ado-net-overview.md)</span></span>
