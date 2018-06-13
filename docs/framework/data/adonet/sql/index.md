---
title: SQL Server e ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: 87e46ad9e83929e40daecc3e3af2eb1281c5ced9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360707"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="ee38b-102">SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ee38b-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="ee38b-103">Esta seção descreve os recursos e os comportamentos que são específicos ao Provedor de Dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="ee38b-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="ee38b-104">O <xref:System.Data.SqlClient> fornece acesso às versões do SQL Server, o que encapsula protocolos específicos ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ee38b-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="ee38b-105">A funcionalidade do provedor de dados foi criada para ser semelhante aos provedores de dados .NET Framework para OLE DB, ODBC e Oracle.</span><span class="sxs-lookup"><span data-stu-id="ee38b-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="ee38b-106">O <xref:System.Data.SqlClient> inclui um analisador de protocolo TDS para se comunicar diretamente com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ee38b-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee38b-107">Para usar o Provedor de Dados .NET Framework para SQL Server, um aplicativo deve fazer referência ao namespace <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="ee38b-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee38b-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ee38b-108">In This Section</span></span>  
 <span data-ttu-id="ee38b-109">[SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md) (Segurança do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ee38b-109">[SQL Server Security](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)</span></span>  
 <span data-ttu-id="ee38b-110">Fornece uma visão geral dos recursos de segurança do SQL Server e cenários de aplicativos para criar aplicativos ADO.NET seguros que direcionam o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ee38b-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 <span data-ttu-id="ee38b-111">[SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ee38b-111">[SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)</span></span>  
 <span data-ttu-id="ee38b-112">Descreve como trabalhar com tipos de dados do SQL Server e como interagir com os tipos de dados do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ee38b-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 <span data-ttu-id="ee38b-113">[SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ee38b-113">[SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)</span></span>  
 <span data-ttu-id="ee38b-114">Descreve como trabalhar com dados de valor grande no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ee38b-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 <span data-ttu-id="ee38b-115">[SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ee38b-115">[SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)</span></span>  
 <span data-ttu-id="ee38b-116">Descreve como trabalhar com dados no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ee38b-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="ee38b-117">Contém seções sobre operações de cópia em massa, MARS, operações assíncronas e parâmetros com valor de tabela.</span><span class="sxs-lookup"><span data-stu-id="ee38b-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 <span data-ttu-id="ee38b-118">[SQL Server Features and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md) (Recursos do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ee38b-118">[SQL Server Features and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)</span></span>  
 <span data-ttu-id="ee38b-119">Descreve os recursos do SQL Server que são úteis para desenvolvedores de aplicativos ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ee38b-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="ee38b-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ee38b-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="ee38b-121">Descreve os blocos de construção, os processos e as técnicas básicas necessários para criar aplicativos LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="ee38b-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="ee38b-122">Para obter a documentação completa do Mecanismo de Banco de Dados do SQL Server, consulte os Manuais Online do SQL Server relativos à versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="ee38b-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="ee38b-123">[SQL Server Books Online](http://msdn.microsoft.com/library/ms130214.aspx) (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ee38b-123">[SQL Server Books Online](http://msdn.microsoft.com/library/ms130214.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee38b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee38b-124">See Also</span></span>  
 <span data-ttu-id="ee38b-125">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ee38b-125">[Securing ADO.NET Applications](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 <span data-ttu-id="ee38b-126">[Data Type Mappings in ADO.NET](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ee38b-126">[Data Type Mappings in ADO.NET](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)</span></span>  
 <span data-ttu-id="ee38b-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="ee38b-127">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="ee38b-128">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ee38b-128">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="ee38b-129">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ee38b-129">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
