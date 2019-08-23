---
title: UDTs grandes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 97df0bee10440dd03f07b980589d9dda85ce121e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909876"
---
# <a name="large-udts"></a>UDTs grandes
Os tipos definidos pelo usuário (UDTs) permitem que um desenvolvedor estenda o sistema de tipo escalar do servidor armazenando objetos CLR em um banco de dados do SQL Server. Os UDTs podem conter vários elementos e podem ter comportamentos, ao contrário dos tipos de dados de alias tradicionais, que consistem em um único tipo de dados do sistema do SQL Server.  
  
> [!NOTE]
> Você deve instalar o .NET Framework 3.5 SP1 (ou posterior) para se beneficiar do suporte avançado do SqlClient para UDTs grandes.  
  
 Anteriormente, os UDTs eram restritos a um tamanho máximo de 8 quilobytes. No SQL Server 2008, essa limitação foi removida para UDTs que têm um formato de <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Para obter a documentação completa para tipos definidos pelo usuário, consulte a versão dos Manuais Online do SQL Server relativos à versão do SQL Server que você está usando.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
1. [Tipos CLR definidos pelo usuário](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Recuperando esquemas de UDT usando GetSchema  
 O método <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> de <xref:System.Data.SqlClient.SqlConnection> retorna informações de esquema do banco de dados em um <xref:System.Data.DataTable>. Para obter mais informações, consulte [SQL Server coleções de esquema](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Valores de coluna de GetSchemaTable para UDTs  
 O método <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> de um <xref:System.Data.SqlClient.SqlDataReader> retorna um <xref:System.Data.DataTable> que descreve metadados de coluna. A tabela a seguir descreve as diferenças nos metadados da coluna para UDTs grandes entre o SQL Server 2005 e SQL Server 2008.  
  
|Coluna SqlDataReader|SQL Server 2005|SQL Server 2008 e posterior|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Varia|Varia|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Instância de UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Instância de UDT|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|O nome de três partes especificado como *Database. SchemaName. TypeName*.|  
|`IsLong`|Varia|Varia|  
  
## <a name="sqldatareader-considerations"></a>Considerações do SqlDataReader  
 O <xref:System.Data.SqlClient.SqlDataReader> foi estendido no início do SQL Server 2008 para dar suporte à recuperação de grandes valores de UDT. O tamanho dos valores de UDT que são processados por um <xref:System.Data.SqlClient.SqlDataReader> depende da versão do SQL Server que você está usando, bem como o `Type System Version` especificado na cadeia de conexão. Para obter mais informações, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Os seguintes métodos de <xref:System.Data.SqlClient.SqlDataReader> retornarão <xref:System.Data.SqlTypes.SqlBinary> em vez de um UDT quando o `Type System Version` for definido como o SQL Server 2005:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Os seguintes métodos retornarão uma matriz de `Byte[]` em vez de um UDT quando o `Type System Version` for definido como o SQL Server 2005:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Observe que nenhuma conversão é feita para a versão atual do ADO.NET.  
  
## <a name="specifying-sqlparameters"></a>Especificando SqlParameters  
 As seguintes propriedades de <xref:System.Data.SqlClient.SqlParameter> foram estendidas para funcionar com UDTs grandes.  
  
|Propriedade do SqlParameter|Descrição|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Obtém ou define um objeto que representa o valor do parâmetro. O padrão é nulo. A propriedade pode ser `SqlBinary`, `Byte[]` ou um objeto gerenciado.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Obtém ou define um objeto que representa o valor do parâmetro. O padrão é nulo. A propriedade pode ser `SqlBinary`, `Byte[]` ou um objeto gerenciado.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Obtém ou define o tamanho do valor do parâmetro para resolver. O valor padrão é 0. A propriedade pode ser um inteiro que representa o tamanho do valor do parâmetro. Para UDTs grandes, pode ser o tamanho real do UDT, ou -1 para o desconhecido.|  
  
## <a name="retrieving-data-example"></a>Recuperando exemplo de dados  
 O fragmento de código a seguir demonstra como recuperar dados grandes de UDT. A variável `connectionString` pressupõe uma conexão válida para um banco de dados do SQL Server e a variável de `commandString` pressupõe uma instrução SELECT válida com a coluna de chave primária listada primeiro.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Configurando parâmetros e tipos de dados de parâmetro](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Recuperando informações de esquema de banco de dados](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [Mapeamentos de tipo de dados do SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
