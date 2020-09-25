---
title: UDTs grandes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 032093244f51893cd3b0cf50ad81c79413aaa32e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194538"
---
# <a name="large-udts"></a><span data-ttu-id="a5f89-102">UDTs grandes</span><span class="sxs-lookup"><span data-stu-id="a5f89-102">Large UDTs</span></span>

<span data-ttu-id="a5f89-103">Os UDTs (tipos definidos pelo usuário) permitem que os desenvolvedores estendam o sistema de tipo escalar do servidor armazenando objetos de CLR (Common Language Runtime) em um banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5f89-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="a5f89-104">Os UDTs podem conter vários elementos e ter comportamentos, diferentemente dos tipos de dados de alias tradicionais, que consistem em um único tipo de dados do sistema no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5f89-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5f89-105">Você deve instalar o .NET Framework 3.5 SP1 (ou posterior) para se beneficiar do suporte avançado do SqlClient para UDTs grandes.</span><span class="sxs-lookup"><span data-stu-id="a5f89-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="a5f89-106">Os UDTs eram anteriormente restritas a um tamanho máximo de 8 kilobytes.</span><span class="sxs-lookup"><span data-stu-id="a5f89-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="a5f89-107">No SQL Server 2008, essa restrição foi removida para UDTs que têm um formato de <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="a5f89-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="a5f89-108">Para obter a documentação completa para tipos definidos pelo usuário, consulte a versão dos Manuais Online do SQL Server relativos à versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="a5f89-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="a5f89-109">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="a5f89-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="a5f89-110">Tipos definidos pelo usuário de CLR</span><span class="sxs-lookup"><span data-stu-id="a5f89-110">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="a5f89-111">Recuperando esquemas de UDT usando GetSchema</span><span class="sxs-lookup"><span data-stu-id="a5f89-111">Retrieving UDT Schemas Using GetSchema</span></span>  

 <span data-ttu-id="a5f89-112">O método <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> de <xref:System.Data.SqlClient.SqlConnection> retorna informações de esquema de banco de dados em um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a5f89-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a5f89-113">Para obter mais informações, consulte [SQL Server coleções de esquema](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="a5f89-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="a5f89-114">Valores de coluna de GetSchemaTable para UDTs</span><span class="sxs-lookup"><span data-stu-id="a5f89-114">GetSchemaTable Column Values for UDTs</span></span>  

 <span data-ttu-id="a5f89-115">O método <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> de um <xref:System.Data.SqlClient.SqlDataReader> retorna um <xref:System.Data.DataTable> que descreve os metadados da coluna.</span><span class="sxs-lookup"><span data-stu-id="a5f89-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="a5f89-116">A tabela a seguir descreve as diferenças nos metadados da coluna para UDTs grandes entre o SQL Server 2005 e o SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="a5f89-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="a5f89-117">Coluna SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="a5f89-117">SqlDataReader column</span></span>|<span data-ttu-id="a5f89-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="a5f89-118">SQL Server 2005</span></span>|<span data-ttu-id="a5f89-119">SQL Server 2008 e posterior</span><span class="sxs-lookup"><span data-stu-id="a5f89-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="a5f89-120">Varia</span><span class="sxs-lookup"><span data-stu-id="a5f89-120">Varies</span></span>|<span data-ttu-id="a5f89-121">Varia</span><span class="sxs-lookup"><span data-stu-id="a5f89-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="a5f89-122">255</span><span class="sxs-lookup"><span data-stu-id="a5f89-122">255</span></span>|<span data-ttu-id="a5f89-123">255</span><span class="sxs-lookup"><span data-stu-id="a5f89-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="a5f89-124">255</span><span class="sxs-lookup"><span data-stu-id="a5f89-124">255</span></span>|<span data-ttu-id="a5f89-125">255</span><span class="sxs-lookup"><span data-stu-id="a5f89-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="a5f89-126">Instância UDT</span><span class="sxs-lookup"><span data-stu-id="a5f89-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="a5f89-127">Instância UDT</span><span class="sxs-lookup"><span data-stu-id="a5f89-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="a5f89-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="a5f89-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="a5f89-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="a5f89-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="a5f89-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="a5f89-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="a5f89-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="a5f89-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="a5f89-132">O nome de três partes especificado como *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="a5f89-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="a5f89-133">Varia</span><span class="sxs-lookup"><span data-stu-id="a5f89-133">Varies</span></span>|<span data-ttu-id="a5f89-134">Varia</span><span class="sxs-lookup"><span data-stu-id="a5f89-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="a5f89-135">Considerações do SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="a5f89-135">SqlDataReader Considerations</span></span>  

 <span data-ttu-id="a5f89-136">O <xref:System.Data.SqlClient.SqlDataReader> foi estendido a partir do SQL Server 2008 para dar suporte à recuperação de UDTs de valores grandes.</span><span class="sxs-lookup"><span data-stu-id="a5f89-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="a5f89-137">A forma como as UDT de valores grandes são processadas por um <xref:System.Data.SqlClient.SqlDataReader> dependem da versão do SQL Server que você está usando, bem como do `Type System Version` especificado na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="a5f89-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="a5f89-138">Para obter mais informações, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5f89-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="a5f89-139">Os seguintes métodos de <xref:System.Data.SqlClient.SqlDataReader> retornarão um <xref:System.Data.SqlTypes.SqlBinary> em vez de uma UDT quando o `Type System Version` for definido como SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="a5f89-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="a5f89-140">Os seguintes métodos retornarão uma matriz de `Byte[]` em vez de uma UDT quando o `Type System Version` for definido como SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="a5f89-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="a5f89-141">Observe que nenhuma das conversões são feitas para a versão atual do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a5f89-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="a5f89-142">Especificar SqlParameters</span><span class="sxs-lookup"><span data-stu-id="a5f89-142">Specifying SqlParameters</span></span>  

 <span data-ttu-id="a5f89-143">As propriedades <xref:System.Data.SqlClient.SqlParameter> a seguir foram estendidas para funcionar com UDTs grandes.</span><span class="sxs-lookup"><span data-stu-id="a5f89-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="a5f89-144">Propriedade SqlParameter</span><span class="sxs-lookup"><span data-stu-id="a5f89-144">SqlParameter Property</span></span>|<span data-ttu-id="a5f89-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5f89-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="a5f89-146">Obtém ou define um objeto que representa o valor do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a5f89-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="a5f89-147">O padrão é nulo.</span><span class="sxs-lookup"><span data-stu-id="a5f89-147">The default is null.</span></span> <span data-ttu-id="a5f89-148">A propriedade pode ser `SqlBinary`, `Byte[]` ou um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a5f89-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="a5f89-149">Obtém ou define um objeto que representa o valor do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a5f89-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="a5f89-150">O padrão é nulo.</span><span class="sxs-lookup"><span data-stu-id="a5f89-150">The default is null.</span></span> <span data-ttu-id="a5f89-151">A propriedade pode ser `SqlBinary`, `Byte[]` ou um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a5f89-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="a5f89-152">Obtém ou define o tamanho do valor do parâmetro a ser resolvido.</span><span class="sxs-lookup"><span data-stu-id="a5f89-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="a5f89-153">O valor padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="a5f89-153">The default value is 0.</span></span> <span data-ttu-id="a5f89-154">A propriedade pode ser um inteiro que representa o tamanho do valor do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a5f89-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="a5f89-155">Para UDTs grandes, pode ser o tamanho real da UDT ou -1 para desconhecido.</span><span class="sxs-lookup"><span data-stu-id="a5f89-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="a5f89-156">Recuperando exemplo de dados</span><span class="sxs-lookup"><span data-stu-id="a5f89-156">Retrieving Data Example</span></span>  

 <span data-ttu-id="a5f89-157">O fragmento de código a seguir demonstra como recuperar dados de uma UDT grande.</span><span class="sxs-lookup"><span data-stu-id="a5f89-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="a5f89-158">A variável `connectionString` assume uma conexão válida com um banco de dados SQL Server, e a variável `commandString` pressupõe uma instrução SELECT válida com a coluna de chave primária listada primeiro.</span><span class="sxs-lookup"><span data-stu-id="a5f89-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5f89-159">Veja também</span><span class="sxs-lookup"><span data-stu-id="a5f89-159">See also</span></span>

- [<span data-ttu-id="a5f89-160">Configurar parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="a5f89-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="a5f89-161">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="a5f89-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="a5f89-162">Mapeamentos de tipos de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5f89-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="a5f89-163">SQL Server dados binários e de valor grande</span><span class="sxs-lookup"><span data-stu-id="a5f89-163">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="a5f89-164">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a5f89-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
