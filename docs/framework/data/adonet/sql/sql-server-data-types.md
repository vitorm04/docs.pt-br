---
title: Tipos de dados do SQL Server e ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 878bbe41f259f1e50cd0a41669c7a352e78bc0f1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424347"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="f9554-102">Tipos de dados do SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f9554-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="f9554-103">O SQL Server e o .NET Framework são baseados em diferentes tipos de sistema, o que pode resultar em potencial perda de dados.</span><span class="sxs-lookup"><span data-stu-id="f9554-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="f9554-104">Para preservar a integridade dos dados, o provedor de dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>) fornece métodos tipados acessadores para trabalhar com dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f9554-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="f9554-105">É possível usar enumerações nas classes <xref:System.Data.SqlDbType> para especificar tipos de dados <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="f9554-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="f9554-106">Para obter mais informações e uma tabela que descreve os dados de tipo mapeamentos entre tipos de dados do .NET Framework e do SQL Server, consulte [mapeamentos de tipo de dados do SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="f9554-106">For more information and a table that that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="f9554-107">O SQL Server 2008 apresenta novos tipos de dados cujo objetivo é atender às necessidades de negócios de trabalhar com dados de data e hora, estruturados, semiestruturados e não estruturados.</span><span class="sxs-lookup"><span data-stu-id="f9554-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="f9554-108">Esses tipos de dados estão documentados em Manuais Online do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f9554-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="f9554-109">Os tipos de dados do SQL Server disponíveis para uso em seu aplicativo dependem da versão do SQL Server em uso.</span><span class="sxs-lookup"><span data-stu-id="f9554-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="f9554-110">Para obter mais informações, consulte a versão relevante de Manuais Online do SQL Server na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f9554-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="f9554-111">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f9554-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="f9554-112">Tipos de dados (mecanismo de banco de dados)</span><span class="sxs-lookup"><span data-stu-id="f9554-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="f9554-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f9554-113">In This Section</span></span>  
 [<span data-ttu-id="f9554-114">SqlTypes e DataSet</span><span class="sxs-lookup"><span data-stu-id="f9554-114">SqlTypes and the DataSet</span></span>](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 <span data-ttu-id="f9554-115">Descreve o suporte a tipos para `SqlTypes` em `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f9554-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="f9554-116">Manipulando valores nulos</span><span class="sxs-lookup"><span data-stu-id="f9554-116">Handling Null Values</span></span>](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 <span data-ttu-id="f9554-117">Demonstra como trabalhar com valores nulos e a lógica com três valores.</span><span class="sxs-lookup"><span data-stu-id="f9554-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="f9554-118">Comparando valores de GUID e uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="f9554-118">Comparing GUID and uniqueidentifier Values</span></span>](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="f9554-119">Demonstra como trabalhar com GUID e com valores uniqueidentifier no SQL Server e no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9554-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="f9554-120">Dados de data e hora</span><span class="sxs-lookup"><span data-stu-id="f9554-120">Date and Time Data</span></span>](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 <span data-ttu-id="f9554-121">Descreve como usar os novos tipos de dados de data e hora introduzidos no SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f9554-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="f9554-122">UDTs grandes</span><span class="sxs-lookup"><span data-stu-id="f9554-122">Large UDTs</span></span>](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 <span data-ttu-id="f9554-123">Demonstra como recuperar dados de UDTs de valor grande introduzidos no SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f9554-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="f9554-124">Dados XML no SQL Server</span><span class="sxs-lookup"><span data-stu-id="f9554-124">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 <span data-ttu-id="f9554-125">Descreve como trabalhar com dados XML recuperados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f9554-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f9554-126">Referência</span><span class="sxs-lookup"><span data-stu-id="f9554-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="f9554-127">Descreve a classe `DataSet` e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="f9554-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="f9554-128">Descreve o namespace `SqlTypes` e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="f9554-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="f9554-129">Descreve a enumeração `SqlDbType` e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="f9554-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="f9554-130">Descreve a enumeração `DbType` e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="f9554-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9554-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9554-131">See Also</span></span>  
 [<span data-ttu-id="f9554-132">Mapeamentos de tipo de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="f9554-132">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="f9554-133">Configurando parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="f9554-133">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="f9554-134">Parâmetros com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="f9554-134">Table-Valued Parameters</span></span>](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 <span data-ttu-id="f9554-135">[SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f9554-135">[SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)</span></span>  
 <span data-ttu-id="f9554-136">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f9554-136">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
