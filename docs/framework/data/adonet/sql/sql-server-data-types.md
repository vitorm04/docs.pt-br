---
title: Tipos de dados do SQL Server e ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 642fe0d541aca01d6ffb2d9279c4d0fa91eadb63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780852"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="0f971-102">Tipos de dados do SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0f971-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="0f971-103">O SQL Server e o .NET Framework são baseados em diferentes tipos de sistema, o que pode resultar em potencial perda de dados.</span><span class="sxs-lookup"><span data-stu-id="0f971-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="0f971-104">Para preservar a integridade dos dados, o provedor de dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>) fornece métodos tipados acessadores para trabalhar com dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f971-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="0f971-105">É possível usar enumerações nas classes <xref:System.Data.SqlDbType> para especificar tipos de dados <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="0f971-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="0f971-106">Para obter mais informações e uma tabela que descreve os mapeamentos de tipo de dados entre SQL Server e .NET Framework tipos de dados, consulte [SQL Server mapeamentos de tipo de dados](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="0f971-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="0f971-107">O SQL Server 2008 apresenta novos tipos de dados cujo objetivo é atender às necessidades de negócios de trabalhar com dados de data e hora, estruturados, semiestruturados e não estruturados.</span><span class="sxs-lookup"><span data-stu-id="0f971-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="0f971-108">Esses tipos de dados estão documentados em Manuais Online do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="0f971-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="0f971-109">Os tipos de dados do SQL Server disponíveis para uso em seu aplicativo dependem da versão do SQL Server em uso.</span><span class="sxs-lookup"><span data-stu-id="0f971-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="0f971-110">Para obter mais informações, consulte a versão relevante de Manuais Online do SQL Server na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="0f971-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="0f971-111">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0f971-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="0f971-112">Tipos de dados (Mecanismo de Banco de Dados)</span><span class="sxs-lookup"><span data-stu-id="0f971-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="0f971-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0f971-113">In This Section</span></span>  
 [<span data-ttu-id="0f971-114">SqlTypes e DataSet</span><span class="sxs-lookup"><span data-stu-id="0f971-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="0f971-115">Descreve o suporte a tipos para `SqlTypes` em `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="0f971-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="0f971-116">Manipulando valores nulos</span><span class="sxs-lookup"><span data-stu-id="0f971-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="0f971-117">Demonstra como trabalhar com valores nulos e a lógica com três valores.</span><span class="sxs-lookup"><span data-stu-id="0f971-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="0f971-118">Comparando valores de GUID e uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="0f971-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="0f971-119">Demonstra como trabalhar com GUID e com valores uniqueidentifier no SQL Server e no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f971-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="0f971-120">Dados de data e hora</span><span class="sxs-lookup"><span data-stu-id="0f971-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="0f971-121">Descreve como usar os novos tipos de dados de data e hora introduzidos no SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="0f971-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="0f971-122">UDTs grandes</span><span class="sxs-lookup"><span data-stu-id="0f971-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="0f971-123">Demonstra como recuperar dados de UDTs de valor grande introduzidos no SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="0f971-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="0f971-124">Dados XML no SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f971-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="0f971-125">Descreve como trabalhar com dados XML recuperados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f971-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0f971-126">Referência</span><span class="sxs-lookup"><span data-stu-id="0f971-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="0f971-127">Descreve a classe `DataSet` e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="0f971-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="0f971-128">Descreve o namespace `SqlTypes` e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="0f971-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="0f971-129">Descreve a enumeração `SqlDbType` e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="0f971-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="0f971-130">Descreve a enumeração `DbType` e todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="0f971-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f971-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f971-131">See also</span></span>

- [<span data-ttu-id="0f971-132">Mapeamentos de tipo de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f971-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="0f971-133">Configurando parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="0f971-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="0f971-134">Parâmetros com valor de tabela</span><span class="sxs-lookup"><span data-stu-id="0f971-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- <span data-ttu-id="0f971-135">[SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0f971-135">[SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md)</span></span>
- <span data-ttu-id="0f971-136">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0f971-136">[ADO.NET Overview](../ado-net-overview.md)</span></span>
