---
title: Restrições de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c62f934561fa4a6c352ff84b8c1201461c42de39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357251"
---
# <a name="schema-restrictions"></a>Restrições de esquema
O segundo parâmetro opcional do **GetSchema** método é retornado as restrições que são usadas para limitar a quantidade de informações de esquema e ela é passada para o **GetSchema** método como uma matriz de cadeias de caracteres . A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.  
  
 Por exemplo, a tabela a seguir descreve as restrições que a coleção de esquemas "Tabelas" usando o .NET Framework Data Provider para SQL Server com suporte. Restrições adicionais para coleções de esquema do SQL Server são listadas no final deste tópico.  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Especificando valores de restrição  
 Para usar uma das restrições da coleção de esquemas "Tabelas", basta criar uma matriz de cadeias de caracteres com quatro elementos e colocar um valor no elemento que corresponde ao número de restrição. Por exemplo restringir as tabelas retornadas pelo **GetSchema** método apenas as tabelas no esquema de "Vendas", defina o segundo elemento da matriz para "Vendas" antes de passá-lo para o **GetSchema** método.  
  
> [!NOTE]
>  As coleções de restrições de `SqlClient` e `OracleClient` ter adicional `ParameterName` coluna. A coluna de restrição padrão ainda está lá para versões anteriores compatibilidade, mas é ignorada atualmente. Consultas parametrizadas em vez de substituição de cadeia de caracteres deve ser usada para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.  
  
> [!NOTE]
>  O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquema especificado mais de um <xref:System.ArgumentException> será lançada. Pode haver menos do que o número máximo de restrições. As restrições ausentes devem para ser null (ilimitado).  
  
 Você pode consultar um provedor gerenciado do .NET Framework para determinar a lista de restrições com suporte ao chamar o **GetSchema** método com o nome da coleção de esquema para restrições, que é "Restrições". Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.  
  
### <a name="example"></a>Exemplo  
 Os exemplos a seguir demonstram como usar o <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> método do .NET Framework Data Provider para SQL Server <xref:System.Data.SqlClient.SqlConnection> classe para recuperar informações de esquema sobre todas as tabelas contidas no **AdventureWorks**banco de dados de exemplo e restringir as informações retornadas somente as tabelas no esquema de "Vendas":  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a>Restrições de esquema do SQL Server  
 As tabelas a seguir listam as restrições para coleções de esquema do SQL Server.  
  
### <a name="users"></a>Usuários  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|User_Name|@Name|name|1|  
  
### <a name="databases"></a>Bancos de dados  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nome|@Name|Nome|1|  
  
### <a name="tables"></a>Tabelas  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Colunas  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Column|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Column|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Exibições  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|VIEW_CATALOG|1|  
|Proprietário|@Owner|VIEW_SCHEMA|2|  
|Tabela|@Table|VIEW_NAME|3|  
|Column|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|SPECIFIC_CATALOG|1|  
|Proprietário|@Owner|SPECIFIC_SCHEMA|2|  
|Nome|@Name|SPECIFIC_NAME|3|  
|Parâmetro|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Procedimentos  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|SPECIFIC_CATALOG|1|  
|Proprietário|@Owner|SPECIFIC_SCHEMA|2|  
|Nome|@Name|SPECIFIC_NAME|3|  
|Tipo|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|db_name()|1|  
|Proprietário|@Owner|user_name)|2|  
|Tabela|@Table|o.Name|3|  
|ConstraintName|@ConstraintName|x.Name|4|  
|Column|@Column|c.name|5|  
  
### <a name="indexes"></a>Índices  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|db_name()|1|  
|Proprietário|@Owner|user_name)|2|  
|Tabela|@Table|o.Name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|Types.assembly_class|2|  
  
### <a name="foreignkeys"></a>Chaves externas  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|CONSTRAINT_CATALOG|1|  
|Proprietário|@Owner|CONSTRAINT_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Nome|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 Schema Restrictions  
 As tabelas a seguir listam as restrições para coleções de esquema do SQL Server 2008. Essas restrições são válida começando com a versão 3.5 SP1 do .NET Framework e do SQL Server 2008. Eles não têm suporte em versões anteriores do .NET Framework e do SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Nome da restrição|Nome do Parâmetro|Restrição padrão|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Column|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
