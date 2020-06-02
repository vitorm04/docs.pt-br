---
title: Recuperando e modificando dados
description: No .NET Framework, os provedores de dados no ADO.NET servem como uma ponte entre um aplicativo e uma fonte de dados para ler e atualizar dados.
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: f916324dc829526a5e6b0078021b09786755f666
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286605"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="2427c-103">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2427c-103">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="2427c-104">A função principal de qualquer aplicativo de banco de dados é conectar-se a uma fonte de dados e recuperar os dados que ele contém.</span><span class="sxs-lookup"><span data-stu-id="2427c-104">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="2427c-105">Os .NET Framework provedores de dados do ADO.NET servem como uma ponte entre um aplicativo e uma fonte de dados, permitindo que você execute comandos, bem como recuperar dados usando um **DataReader** ou um **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="2427c-105">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="2427c-106">A função principal de qualquer aplicativo de banco de dados é a capacidade de atualizar os dados que estão armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="2427c-106">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="2427c-107">No ADO.NET, a atualização de dados envolve o uso de **DataAdapter** e e de <xref:System.Data.DataSet> objetos **Command** ; e também pode envolver o uso de transações.</span><span class="sxs-lookup"><span data-stu-id="2427c-107">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2427c-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2427c-108">In This Section</span></span>  
 [<span data-ttu-id="2427c-109">Conectando a uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="2427c-109">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="2427c-110">Descreve como estabelecer uma conexão com uma fonte de dados e como trabalhar com eventos de conexão.</span><span class="sxs-lookup"><span data-stu-id="2427c-110">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="2427c-111">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="2427c-111">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="2427c-112">Contém os tópicos que descrevem os vários aspectos do uso de cadeias de conexão, incluindo palavras-chave de cadeias de conexão, informações de segurança e seu respectivo armazenamento e recuperação.</span><span class="sxs-lookup"><span data-stu-id="2427c-112">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="2427c-113">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="2427c-113">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="2427c-114">Descreve o pool de conexões para provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2427c-114">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="2427c-115">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="2427c-115">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="2427c-116">Contém os tópicos que descrevem como criar comandos e construtores de comandos, configurar parâmetros e executar comandos para recuperar e modificar dados.</span><span class="sxs-lookup"><span data-stu-id="2427c-116">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="2427c-117">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="2427c-117">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="2427c-118">Contém os tópicos que descrevem DataReaders, DataAdapters, parâmetros, manipulação de eventos DataAdapter e execução de operações em lote.</span><span class="sxs-lookup"><span data-stu-id="2427c-118">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="2427c-119">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="2427c-119">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="2427c-120">Contém os tópicos que descrevem como executar transações locais, transações distribuídas e trabalho com concorrência otimista.</span><span class="sxs-lookup"><span data-stu-id="2427c-120">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="2427c-121">Recuperando identidade ou valores de Autonumber</span><span class="sxs-lookup"><span data-stu-id="2427c-121">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="2427c-122">Fornece um exemplo de mapeamento dos valores gerados para uma coluna de **identidade** em uma tabela SQL Server ou para um campo **AutoNumeração** em uma tabela do Microsoft Access, para uma coluna de uma linha inserida em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="2427c-122">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="2427c-123">Discute como mesclar valores de identidade em `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="2427c-123">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="2427c-124">Recuperando dados binários</span><span class="sxs-lookup"><span data-stu-id="2427c-124">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="2427c-125">Descreve como recuperar dados binários ou estruturas de dados grandes usando o `CommandBehavior` .`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="2427c-125">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="2427c-126">para modificar o comportamento padrão de um `DataReader` .</span><span class="sxs-lookup"><span data-stu-id="2427c-126">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="2427c-127">Modificando dados com procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="2427c-127">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="2427c-128">Descreve como usar parâmetros de entrada e de saída de procedimentos armazenados para inserir uma linha em um banco de dados, retornando um novo valor de identidade.</span><span class="sxs-lookup"><span data-stu-id="2427c-128">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="2427c-129">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="2427c-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="2427c-130">Descreve como obter bancos de dados ou catálogos disponíveis, tabelas e modos de exibição em um banco de dados, restrições existentes para tabelas e outras informações de esquema de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="2427c-130">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="2427c-131">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="2427c-131">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="2427c-132">Descreve o modelo de fábrica do provedor e demonstra como usar as classes base no namespace `System.Data.Common`.</span><span class="sxs-lookup"><span data-stu-id="2427c-132">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="2427c-133">Rastreamento de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2427c-133">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="2427c-134">Descreve como o ADO.NET fornece a funcionalidade interna de rastreamento de dados.</span><span class="sxs-lookup"><span data-stu-id="2427c-134">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="2427c-135">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="2427c-135">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="2427c-136">Descreve os contadores de desempenho disponíveis para `SqlClient` e `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="2427c-136">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="2427c-137">Programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="2427c-137">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="2427c-138">Descreve o suporte do ADO.NET para programação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2427c-138">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="2427c-139">Suporte de streaming do SqlClient</span><span class="sxs-lookup"><span data-stu-id="2427c-139">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="2427c-140">Discute como escrever aplicativos que transmitem dados de SQL Server sem tê-los totalmente carregados na memória.</span><span class="sxs-lookup"><span data-stu-id="2427c-140">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2427c-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="2427c-141">See also</span></span>

- <span data-ttu-id="2427c-142">[Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2427c-142">[Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md)</span></span>
- [<span data-ttu-id="2427c-143">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="2427c-143">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="2427c-144">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2427c-144">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="2427c-145">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2427c-145">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="2427c-146">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2427c-146">ADO.NET Overview</span></span>](ado-net-overview.md)
