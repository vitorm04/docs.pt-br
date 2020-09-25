---
title: SQL Server e ADO.NET
description: Saiba mais sobre os recursos e comportamentos do Provedor de Dados de .NET Framework para SQL Server, que encapsula protocolos específicos de banco de dados.
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: a517bccd9b60d00f6c6c636c9164d63fb5966de3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197385"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="f9e25-103">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9e25-103">SQL Server and ADO.NET</span></span>

<span data-ttu-id="f9e25-104">Esta seção descreve os recursos e os comportamentos que são específicos ao Provedor de Dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="f9e25-104">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="f9e25-105"><xref:System.Data.SqlClient> fornece acesso a versões do SQL Server, que encapsula protocolos específicos do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f9e25-105"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="f9e25-106">A funcionalidade do provedor de dados foi criada para ser semelhante aos provedores de dados .NET Framework para OLE DB, ODBC e Oracle.</span><span class="sxs-lookup"><span data-stu-id="f9e25-106">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="f9e25-107"><xref:System.Data.SqlClient> inclui um analisador de TDS (tabela de dados tabulares) para se comunicar diretamente com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f9e25-107"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9e25-108">Para usar o Provedor de Dados .NET Framework para SQL Server, um aplicativo deve fazer referência ao namespace <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="f9e25-108">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9e25-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f9e25-109">In This Section</span></span>  

 [<span data-ttu-id="f9e25-110">Segurança de SQL Server</span><span class="sxs-lookup"><span data-stu-id="f9e25-110">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="f9e25-111">Fornece uma visão geral dos recursos de segurança do SQL Server, bem como cenários de aplicativo para criar aplicativos ADO.NET seguros direcionados ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f9e25-111">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="f9e25-112">Tipos de dados SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9e25-112">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="f9e25-113">Descreve como trabalhar com tipos de dados do SQL Server e como interagir com os tipos de dados do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9e25-113">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="f9e25-114">SQL Server dados binários e de valor grande</span><span class="sxs-lookup"><span data-stu-id="f9e25-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="f9e25-115">Descreve como trabalhar com os dados de valor grande no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f9e25-115">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="f9e25-116">SQL Server operações de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9e25-116">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="f9e25-117">Descreve como trabalhar com os dados no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f9e25-117">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="f9e25-118">Contém seções sobre operações de cópia em massa, MARS, operações assíncronas e parâmetros com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="f9e25-118">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="f9e25-119">Recursos de SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9e25-119">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="f9e25-120">Descreve recursos do SQL Server que são úteis para desenvolvedores de aplicativos ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f9e25-120">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="f9e25-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f9e25-121">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="f9e25-122">Descreve os blocos de construção, os processos e as técnicas básicas necessários para criar aplicativos LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="f9e25-122">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="f9e25-123">Para ver a documentação completa do Mecanismo de Banco de Dados do SQL Server, consulte os Manuais Online do SQL Server para saber qual versão do SQL Server você está usando.</span><span class="sxs-lookup"><span data-stu-id="f9e25-123">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="f9e25-124">Manuais Online do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="f9e25-124">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="f9e25-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="f9e25-125">See also</span></span>

- [<span data-ttu-id="f9e25-126">Protegendo aplicativos ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9e25-126">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="f9e25-127">Mapeamentos de tipos de dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9e25-127">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="f9e25-128">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="f9e25-128">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="f9e25-129">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9e25-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="f9e25-130">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9e25-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
