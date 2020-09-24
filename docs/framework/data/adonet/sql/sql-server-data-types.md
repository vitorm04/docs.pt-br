---
title: Tipos de dados do SQL Server e ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: db4618ac624ea8401cab682a8c21d8f23c253d05
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155452"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="b63a9-102">Tipos de dados do SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b63a9-102">SQL Server Data Types and ADO.NET</span></span>

<span data-ttu-id="b63a9-103">O SQL Server e o .NET Framework são baseados em diferentes tipos de sistema, o que pode resultar em potencial perda de dados.</span><span class="sxs-lookup"><span data-stu-id="b63a9-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="b63a9-104">Para preservar a integridade dos dados, o provedor de dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>) fornece métodos tipados acessadores para trabalhar com dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b63a9-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="b63a9-105">Você pode usar as enumerações nas classes de <xref:System.Data.SqlDbType> para especificar tipos de dados <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="b63a9-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="b63a9-106">Para obter mais informações e uma tabela que descreve os mapeamentos de tipo de dados entre SQL Server e .NET Framework tipos de dados, consulte [SQL Server mapeamentos de tipo de dados](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="b63a9-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="b63a9-107">O SQL Server 2008 apresenta novos tipos de dados criados para atender às necessidades empresariais para trabalhar usando dados de data e hora, estruturados, semiestruturados e não estruturados.</span><span class="sxs-lookup"><span data-stu-id="b63a9-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="b63a9-108">Eles são documentados nos Manuais Online do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b63a9-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="b63a9-109">Os tipos de dados do SQL Server disponíveis para uso em seu aplicativo dependem da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="b63a9-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="b63a9-110">Para obter mais informações, consulte a versão relevante de Manuais Online do SQL Server na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b63a9-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="b63a9-111">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="b63a9-111">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="b63a9-112">Tipos de dados (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b63a9-112">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a><span data-ttu-id="b63a9-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b63a9-113">In This Section</span></span>  

 [<span data-ttu-id="b63a9-114">SqlTypes e DataSet</span><span class="sxs-lookup"><span data-stu-id="b63a9-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="b63a9-115">Descreve o suporte de tipo para `SqlTypes` no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b63a9-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="b63a9-116">Manipulando valores nulos</span><span class="sxs-lookup"><span data-stu-id="b63a9-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="b63a9-117">Demonstra como trabalhar com valores nulos e lógica de três valores.</span><span class="sxs-lookup"><span data-stu-id="b63a9-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="b63a9-118">Comparando valores de GUID e uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="b63a9-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="b63a9-119">Demonstra como trabalhar com GUID e com valores uniqueidentifier no SQL Server e no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b63a9-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="b63a9-120">Dados de data e hora</span><span class="sxs-lookup"><span data-stu-id="b63a9-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="b63a9-121">Descreve como usar os novos tipos de dados de data e hora introduzidos no SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b63a9-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="b63a9-122">UDTs grandes</span><span class="sxs-lookup"><span data-stu-id="b63a9-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="b63a9-123">Demonstra como recuperar dados de UDTs de valor grande introduzidos no SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b63a9-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="b63a9-124">Dados XML no SQL Server</span><span class="sxs-lookup"><span data-stu-id="b63a9-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="b63a9-125">Descreve como trabalhar com os dados XML recuperados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b63a9-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b63a9-126">Referência</span><span class="sxs-lookup"><span data-stu-id="b63a9-126">Reference</span></span>  

 <xref:System.Data.DataSet>  
 <span data-ttu-id="b63a9-127">Descreve a classe `DataSet` e todos os membros dela.</span><span class="sxs-lookup"><span data-stu-id="b63a9-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="b63a9-128">Descreve o namespace `SqlTypes` e todos os membros dele.</span><span class="sxs-lookup"><span data-stu-id="b63a9-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="b63a9-129">Descreve a enumeração `SqlDbType` e todos os membros dela.</span><span class="sxs-lookup"><span data-stu-id="b63a9-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="b63a9-130">Descreve a enumeração `DbType` e todos os membros dela.</span><span class="sxs-lookup"><span data-stu-id="b63a9-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63a9-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="b63a9-131">See also</span></span>

- [<span data-ttu-id="b63a9-132">Mapeamentos de tipos de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="b63a9-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="b63a9-133">Configurar parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="b63a9-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="b63a9-134">Parâmetros com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="b63a9-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="b63a9-135">SQL Server dados binários e de valor grande</span><span class="sxs-lookup"><span data-stu-id="b63a9-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="b63a9-136">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b63a9-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
