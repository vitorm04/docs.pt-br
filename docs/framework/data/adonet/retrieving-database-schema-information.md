---
title: Recuperando informações de esquema de banco de dados
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 00cf0e36dd7886897c26adf50102f32892ebb18e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562698"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="c55a4-102">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="c55a4-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="c55a4-103">A obtenção de informações de esquema de um banco de dados é realizada com o processo de descoberta de esquema.</span><span class="sxs-lookup"><span data-stu-id="c55a4-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="c55a4-104">Descoberta de esquema permite que os aplicativos podem solicitar que os provedores gerenciados localizem e retornam informações sobre o esquema de banco de dados, também conhecido como *metadados*, de um determinado banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c55a4-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="c55a4-105">Os diferentes elementos de esquema de banco de dados, como tabelas, colunas e procedimentos armazenados, são expostos por meio de coleções de esquema.</span><span class="sxs-lookup"><span data-stu-id="c55a4-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="c55a4-106">Cada coleção de esquema contém uma variedade de informações de esquema específicas ao provedor em uso.</span><span class="sxs-lookup"><span data-stu-id="c55a4-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="c55a4-107">Cada uma da implementação de provedores gerenciados do .NET Framework a **GetSchema** método na **Conexão** classe e as informações de esquema que são retornadas o **GetSchema**método vem na forma de um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="c55a4-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c55a4-108">O **GetSchema** método é um método sobrecarregado que fornece parâmetros opcionais para especificar a coleção de esquema para retornar e restringir a quantidade de informações retornadas.</span><span class="sxs-lookup"><span data-stu-id="c55a4-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="c55a4-109">Os provedores de dados do .NET Framework para OLE DB, ODBC, Oracle e SqlClient fornecem um **GetSchemaTable** método que retorna um DataTable que descreve os metadados da coluna a **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="c55a4-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="c55a4-110">O Provedor de Dados .NET Framework para OLE DB também expõe informações de esquema usando o método <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> do objeto <xref:System.Data.OleDb.OleDbConnection>.</span><span class="sxs-lookup"><span data-stu-id="c55a4-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="c55a4-111">Como argumentos, **GetOleDbSchemaTable** leva um <xref:System.Data.OleDb.OleDbSchemaGuid> que identifica as informações de esquema para retornar e uma matriz de restrições nessas colunas retornadas.</span><span class="sxs-lookup"><span data-stu-id="c55a4-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="c55a4-112">**{1&gt;GetOleDbSchemaTable&lt;1** retorna um <xref:System.Data.DataTable> preenchido com as informações de esquema solicitadas.</span><span class="sxs-lookup"><span data-stu-id="c55a4-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c55a4-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c55a4-113">In This Section</span></span>  
 [<span data-ttu-id="c55a4-114">GetSchema e coleções de esquema</span><span class="sxs-lookup"><span data-stu-id="c55a4-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="c55a4-115">Descreve o **GetSchema** método e como ele pode ser usado para recuperar e restringir informações de esquema de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c55a4-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="c55a4-116">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="c55a4-116">Schema Restrictions</span></span>  
 <span data-ttu-id="c55a4-117">Descreve as restrições de esquema que podem ser usadas com **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="c55a4-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="c55a4-118">Coleções de esquema comuns</span><span class="sxs-lookup"><span data-stu-id="c55a4-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="c55a4-119">Descreve todas as coleções de esquema comuns com suporte em todos os provedores gerenciados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c55a4-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="c55a4-120">Coleções de esquema do SQL Server</span><span class="sxs-lookup"><span data-stu-id="c55a4-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="c55a4-121">Descreve a coleção de esquema com suporte pelo provedor .NET Framework para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c55a4-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="c55a4-122">Coleções de esquema do Oracle</span><span class="sxs-lookup"><span data-stu-id="c55a4-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="c55a4-123">Descreve a coleção de esquema com suporte pelo provedor .NET Framework para Oracle.</span><span class="sxs-lookup"><span data-stu-id="c55a4-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="c55a4-124">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="c55a4-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="c55a4-125">Descreve as coleções de esquema para drivers ODBC.</span><span class="sxs-lookup"><span data-stu-id="c55a4-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="c55a4-126">Coleções de esquema de OLE DB</span><span class="sxs-lookup"><span data-stu-id="c55a4-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="c55a4-127">Descreve as coleções de esquema para provedores OLE DB.</span><span class="sxs-lookup"><span data-stu-id="c55a4-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c55a4-128">Referência</span><span class="sxs-lookup"><span data-stu-id="c55a4-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="c55a4-129">Descreve o **GetSchema** método o <xref:System.Data.Common.DbConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="c55a4-130">Descreve o **GetSchema** método o <xref:System.Data.Odbc.OdbcConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="c55a4-131">Descreve o **GetSchema** método o <xref:System.Data.OleDb.OleDbConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="c55a4-132">Descreve o **GetSchema** método o <xref:System.Data.OracleClient.OracleConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="c55a4-133">Descreve o **GetSchema** método o <xref:System.Data.SqlClient.SqlConnection> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c55a4-134">Descreve o **GetSchemaTable** método o <xref:System.Data.Common.DbDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c55a4-135">Descreve o **GetSchemaTable** método o <xref:System.Data.Odbc.OdbcDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c55a4-136">Descreve o **GetSchemaTable** método o <xref:System.Data.OleDb.OleDbDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c55a4-137">Descreve o **GetSchemaTable** método o <xref:System.Data.OracleClient.OracleDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c55a4-138">Descreve o **GetSchemaTable** método o <xref:System.Data.SqlClient.SqlDataReader> classe.</span><span class="sxs-lookup"><span data-stu-id="c55a4-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55a4-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c55a4-139">See Also</span></span>  
 <span data-ttu-id="c55a4-140">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c55a4-140">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="c55a4-141">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c55a4-141">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
