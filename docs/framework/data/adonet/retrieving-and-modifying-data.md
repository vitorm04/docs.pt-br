---
title: Recuperando e modificando dados no ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ff937e619d449fbfbedb234749292b6acc4bdf50
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="352af-102">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="352af-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="352af-103">A função principal de qualquer aplicativo de banco de dados é conectar-se a uma fonte de dados e recuperar os dados que ele contém.</span><span class="sxs-lookup"><span data-stu-id="352af-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="352af-104">Os provedores de dados do .NET Framework do ADO.NET servem como uma ponte entre um aplicativo e uma fonte de dados, permitindo que você execute comandos, bem como para recuperar dados usando um **DataReader** ou um **DataAdapter** .</span><span class="sxs-lookup"><span data-stu-id="352af-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="352af-105">A função principal de qualquer aplicativo de banco de dados é a capacidade de atualizar os dados que estão armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="352af-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="352af-106">No ADO.NET, atualização de dados envolve o uso de **DataAdapter** e <xref:System.Data.DataSet>, e **comando** objetos; e ele também podem envolver o uso de transações.</span><span class="sxs-lookup"><span data-stu-id="352af-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="352af-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="352af-107">In This Section</span></span>  
 [<span data-ttu-id="352af-108">Conectando a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="352af-108">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="352af-109">Descreve como estabelecer uma conexão com uma fonte de dados e como trabalhar com eventos de conexão.</span><span class="sxs-lookup"><span data-stu-id="352af-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="352af-110">Cadeia de Conexão</span><span class="sxs-lookup"><span data-stu-id="352af-110">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 <span data-ttu-id="352af-111">Contém os tópicos que descrevem os vários aspectos do uso de cadeias de conexão, incluindo palavras-chave de cadeias de conexão, informações de segurança e seu respectivo armazenamento e recuperação.</span><span class="sxs-lookup"><span data-stu-id="352af-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="352af-112">Pooling de Conexão</span><span class="sxs-lookup"><span data-stu-id="352af-112">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 <span data-ttu-id="352af-113">Descreve o pool de conexões para provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="352af-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="352af-114">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="352af-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="352af-115">Contém os tópicos que descrevem como criar comandos e construtores de comandos, configurar parâmetros e executar comandos para recuperar e modificar dados.</span><span class="sxs-lookup"><span data-stu-id="352af-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="352af-116">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="352af-116">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="352af-117">Contém os tópicos que descrevem DataReaders, DataAdapters, parâmetros, manipulação de eventos DataAdapter e execução de operações em lote.</span><span class="sxs-lookup"><span data-stu-id="352af-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="352af-118">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="352af-118">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="352af-119">Contém os tópicos que descrevem como executar transações locais, transações distribuídas e trabalho com concorrência otimista.</span><span class="sxs-lookup"><span data-stu-id="352af-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="352af-120">Recuperando identidade ou valores de Autonumber</span><span class="sxs-lookup"><span data-stu-id="352af-120">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="352af-121">Fornece um exemplo de mapeamento de valores gerados para uma **identidade** coluna em uma [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] tabela ou para um **Autonumber** campo em uma tabela do Microsoft Access, para uma coluna de uma linha inserida em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="352af-121">Provides an example of mapping the values generated for an **identity** column in a [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="352af-122">Discute como mesclar valores de identidade em `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="352af-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="352af-123">Recuperando dados binários</span><span class="sxs-lookup"><span data-stu-id="352af-123">Retrieving Binary Data</span></span>](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 <span data-ttu-id="352af-124">Descreve como recuperar dados binários ou estruturas de dados grandes usando `CommandBehavior`.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="352af-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="352af-125">Para modificar o comportamento padrão de um `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="352af-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="352af-126">Modificando dados com procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="352af-126">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="352af-127">Descreve como usar parâmetros de entrada e de saída de procedimentos armazenados para inserir uma linha em um banco de dados, retornando um novo valor de identidade.</span><span class="sxs-lookup"><span data-stu-id="352af-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="352af-128">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="352af-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="352af-129">Descreve como obter bancos de dados ou catálogos disponíveis, tabelas e modos de exibição em um banco de dados, restrições existentes para tabelas e outras informações de esquema de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="352af-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="352af-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="352af-130">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="352af-131">Descreve o modelo de fábrica do provedor e demonstra como usar as classes base no namespace `System.Data.Common`.</span><span class="sxs-lookup"><span data-stu-id="352af-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="352af-132">Rastreamento de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="352af-132">Data Tracing in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-tracing.md)  
 <span data-ttu-id="352af-133">Descreve como o ADO.NET fornece a funcionalidade interna de rastreamento de dados.</span><span class="sxs-lookup"><span data-stu-id="352af-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="352af-134">Contadores de desempenho</span><span class="sxs-lookup"><span data-stu-id="352af-134">Performance Counters</span></span>](../../../../docs/framework/data/adonet/performance-counters.md)  
 <span data-ttu-id="352af-135">Descreve os contadores de desempenho disponíveis para `SqlClient` e `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="352af-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="352af-136">Programação Assíncrona</span><span class="sxs-lookup"><span data-stu-id="352af-136">Asynchronous Programming</span></span>](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 <span data-ttu-id="352af-137">Descreve o suporte do [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] à programação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="352af-137">Describes [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="352af-138">Suporte de Streaming do SqlClient</span><span class="sxs-lookup"><span data-stu-id="352af-138">SqlClient Streaming Support</span></span>](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 <span data-ttu-id="352af-139">Discute como criar aplicativos que transmitem dados do [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] sem carregá-los completamente na memória.</span><span class="sxs-lookup"><span data-stu-id="352af-139">Discusses how to write applications that stream data from [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352af-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="352af-140">See Also</span></span>  
 <span data-ttu-id="352af-141">[Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="352af-141">[Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)</span></span>  
 <span data-ttu-id="352af-142">[DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="352af-142">[DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="352af-143">[Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="352af-143">[Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 <span data-ttu-id="352af-144">[SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="352af-144">[SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)</span></span>  
 <span data-ttu-id="352af-145">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="352af-145">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
