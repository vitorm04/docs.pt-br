---
title: UDTs grandes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 012bddc0b4c29a0b50abc3a0df5c3cd34dc4725a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452390"
---
# <a name="large-udts"></a><span data-ttu-id="677d2-102">UDTs grandes</span><span class="sxs-lookup"><span data-stu-id="677d2-102">Large UDTs</span></span>
<span data-ttu-id="677d2-103">Os UDTs (tipos definidos pelo usuário) permitem que os desenvolvedores estendam o sistema de tipo escalar do servidor armazenando objetos de CLR (Common Language Runtime) em um banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="677d2-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="677d2-104">Os UDTs podem conter vários elementos e ter comportamentos, diferentemente dos tipos de dados de alias tradicionais, que consistem em um único tipo de dados do sistema no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="677d2-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="677d2-105">Você deve instalar o .NET Framework 3.5 SP1 (ou posterior) para se beneficiar do suporte avançado do SqlClient para UDTs grandes.</span><span class="sxs-lookup"><span data-stu-id="677d2-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="677d2-106">Os UDTs eram anteriormente restritas a um tamanho máximo de 8 kilobytes.</span><span class="sxs-lookup"><span data-stu-id="677d2-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="677d2-107">No SQL Server 2008, essa limitação foi removida para UDTs que têm um formato de <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="677d2-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="677d2-108">Para obter a documentação completa para tipos definidos pelo usuário, consulte a versão dos Manuais Online do SQL Server relativos à versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="677d2-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="677d2-109">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="677d2-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="677d2-110">Tipos definidos pelo usuário do CLR</span><span class="sxs-lookup"><span data-stu-id="677d2-110">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="677d2-111">Recuperando esquemas de UDT usando GetSchema</span><span class="sxs-lookup"><span data-stu-id="677d2-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="677d2-112">O método <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> de <xref:System.Data.SqlClient.SqlConnection> retorna informações de esquema do banco de dados em um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="677d2-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="677d2-113">Para obter mais informações, consulte [SQL Server coleções de esquema](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="677d2-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="677d2-114">Valores de coluna de GetSchemaTable para UDTs</span><span class="sxs-lookup"><span data-stu-id="677d2-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="677d2-115">O método <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> de um <xref:System.Data.SqlClient.SqlDataReader> retorna um <xref:System.Data.DataTable> que descreve metadados de coluna.</span><span class="sxs-lookup"><span data-stu-id="677d2-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="677d2-116">A tabela a seguir descreve as diferenças nos metadados da coluna para UDTs grandes entre o SQL Server 2005 e SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="677d2-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="677d2-117">Coluna SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="677d2-117">SqlDataReader column</span></span>|<span data-ttu-id="677d2-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="677d2-118">SQL Server 2005</span></span>|<span data-ttu-id="677d2-119">SQL Server 2008 e posterior</span><span class="sxs-lookup"><span data-stu-id="677d2-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="677d2-120">Varia</span><span class="sxs-lookup"><span data-stu-id="677d2-120">Varies</span></span>|<span data-ttu-id="677d2-121">Varia</span><span class="sxs-lookup"><span data-stu-id="677d2-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="677d2-122">255</span><span class="sxs-lookup"><span data-stu-id="677d2-122">255</span></span>|<span data-ttu-id="677d2-123">255</span><span class="sxs-lookup"><span data-stu-id="677d2-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="677d2-124">255</span><span class="sxs-lookup"><span data-stu-id="677d2-124">255</span></span>|<span data-ttu-id="677d2-125">255</span><span class="sxs-lookup"><span data-stu-id="677d2-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="677d2-126">Instância de UDT</span><span class="sxs-lookup"><span data-stu-id="677d2-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="677d2-127">Instância de UDT</span><span class="sxs-lookup"><span data-stu-id="677d2-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="677d2-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="677d2-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="677d2-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="677d2-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="677d2-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="677d2-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="677d2-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="677d2-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="677d2-132">O nome de três partes especificado como *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="677d2-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="677d2-133">Varia</span><span class="sxs-lookup"><span data-stu-id="677d2-133">Varies</span></span>|<span data-ttu-id="677d2-134">Varia</span><span class="sxs-lookup"><span data-stu-id="677d2-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="677d2-135">Considerações do SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="677d2-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="677d2-136">O <xref:System.Data.SqlClient.SqlDataReader> foi estendido no início do SQL Server 2008 para dar suporte à recuperação de grandes valores de UDT.</span><span class="sxs-lookup"><span data-stu-id="677d2-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="677d2-137">O tamanho dos valores de UDT que são processados por um <xref:System.Data.SqlClient.SqlDataReader> depende da versão do SQL Server que você está usando, bem como o `Type System Version` especificado na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="677d2-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="677d2-138">Para obter mais informações, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="677d2-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="677d2-139">Os seguintes métodos de <xref:System.Data.SqlClient.SqlDataReader> retornarão <xref:System.Data.SqlTypes.SqlBinary> em vez de um UDT quando o `Type System Version` for definido como o SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="677d2-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="677d2-140">Os seguintes métodos retornarão uma matriz de `Byte[]` em vez de um UDT quando o `Type System Version` for definido como o SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="677d2-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="677d2-141">Observe que nenhuma conversão é feita para a versão atual do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="677d2-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="677d2-142">Especificando SqlParameters</span><span class="sxs-lookup"><span data-stu-id="677d2-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="677d2-143">As seguintes propriedades de <xref:System.Data.SqlClient.SqlParameter> foram estendidas para funcionar com UDTs grandes.</span><span class="sxs-lookup"><span data-stu-id="677d2-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="677d2-144">Propriedade do SqlParameter</span><span class="sxs-lookup"><span data-stu-id="677d2-144">SqlParameter Property</span></span>|<span data-ttu-id="677d2-145">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="677d2-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="677d2-146">Obtém ou define um objeto que representa o valor do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="677d2-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="677d2-147">O padrão é nulo.</span><span class="sxs-lookup"><span data-stu-id="677d2-147">The default is null.</span></span> <span data-ttu-id="677d2-148">A propriedade pode ser `SqlBinary`, `Byte[]` ou um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="677d2-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="677d2-149">Obtém ou define um objeto que representa o valor do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="677d2-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="677d2-150">O padrão é nulo.</span><span class="sxs-lookup"><span data-stu-id="677d2-150">The default is null.</span></span> <span data-ttu-id="677d2-151">A propriedade pode ser `SqlBinary`, `Byte[]` ou um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="677d2-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="677d2-152">Obtém ou define o tamanho do valor do parâmetro para resolver.</span><span class="sxs-lookup"><span data-stu-id="677d2-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="677d2-153">O valor padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="677d2-153">The default value is 0.</span></span> <span data-ttu-id="677d2-154">A propriedade pode ser um inteiro que representa o tamanho do valor do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="677d2-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="677d2-155">Para UDTs grandes, pode ser o tamanho real do UDT, ou -1 para o desconhecido.</span><span class="sxs-lookup"><span data-stu-id="677d2-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="677d2-156">Recuperando exemplo de dados</span><span class="sxs-lookup"><span data-stu-id="677d2-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="677d2-157">O fragmento de código a seguir demonstra como recuperar dados grandes de UDT.</span><span class="sxs-lookup"><span data-stu-id="677d2-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="677d2-158">A variável `connectionString` pressupõe uma conexão válida para um banco de dados do SQL Server e a variável de `commandString` pressupõe uma instrução SELECT válida com a coluna de chave primária listada primeiro.</span><span class="sxs-lookup"><span data-stu-id="677d2-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="677d2-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="677d2-159">See also</span></span>

- [<span data-ttu-id="677d2-160">Configurando parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="677d2-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="677d2-161">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="677d2-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="677d2-162">Mapeamentos de tipo de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="677d2-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- <span data-ttu-id="677d2-163">[SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="677d2-163">[SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md)</span></span>
- <span data-ttu-id="677d2-164">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="677d2-164">[ADO.NET Overview](../ado-net-overview.md)</span></span>
