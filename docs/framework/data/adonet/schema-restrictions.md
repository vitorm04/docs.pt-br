---
title: Restrições de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149005"
---
# <a name="schema-restrictions"></a>Restrições de esquema
O segundo parâmetro opcional do método **GetSchema** são as restrições que são usadas para limitar a quantidade de informações de esquema devolvidas, e é passada para o método **GetSchema** como uma matriz de strings. A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.  
  
 Por exemplo, a tabela a seguir descreve as restrições suportadas pela coleção de esquemas "Tabelas" usando o .NET Framework Data Provider for SQL Server. Restrições adicionais para coleções de esquemas do SQL Server são listadas no final deste tópico.  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Especificando valores de restrição  
 Para usar uma das restrições da coleção de esquema "Tabelas", basta criar uma matriz de strings com quatro elementos e, em seguida, colocar um valor no elemento que corresponde ao número de restrição. Por exemplo, para restringir as tabelas devolvidas pelo método **GetSchema** apenas para aquelas tabelas no esquema "Vendas", defina o segundo elemento da matriz como "Vendas" antes de passá-lo para o método **GetSchema.**  
  
> [!NOTE]
> As restrições `SqlClient` coletam `OracleClient` e `ParameterName` têm uma coluna adicional. A coluna padrão de restrição ainda está lá para retrocompatibilidade, mas atualmente é ignorada. Consultas parametrizadas em vez de substituição de cordas devem ser usadas para minimizar o risco de um ataque de injeção SQL ao especificar valores de restrição.  
  
> [!NOTE]
> O número de elementos na matriz deve ser menor ou igual ao número de restrições <xref:System.ArgumentException> suportadas para a coleção de esquemas especificada, caso não seja lançada. Pode haver menos do que o número máximo de restrições. As restrições que faltam são consideradas nulas (irrestritas).  
  
 Você pode consultar um provedor gerenciado pelo .NET Framework para determinar a lista de restrições suportadas ligando para o método **GetSchema** com o nome da coleção de esquemas de restrições, que é "Restrições". Isso retornará <xref:System.Data.DataTable> um com uma lista dos nomes da coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.  
  
### <a name="example"></a>Exemplo  
 Os exemplos a seguir demonstram <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> como usar o método do .NET <xref:System.Data.SqlClient.SqlConnection> Framework Data Provider para a classe SQL Server para recuperar informações de esquema sobre todas as tabelas contidas no banco de dados de amostra **do AdventureWorks** e restringir as informações devolvidas apenas às tabelas no esquema "Vendas":  
  
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
  
## <a name="sql-server-schema-restrictions"></a>Restrições ao esquema do servidor SQL  
 As tabelas a seguir listam as restrições para coleções de esquemas do SQL Server.  
  
### <a name="users"></a>Usuários  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|User_name|@Name|name|1|  
  
### <a name="databases"></a>Bancos de dados  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Nome|@Name|Nome|1|  
  
### <a name="tables"></a>Tabelas  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Colunas  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Coluna|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>Membros estruturados  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Coluna|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Exibições  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>VerColunas  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|VIEW_CATALOG|1|  
|Proprietário|@Owner|VIEW_SCHEMA|2|  
|Tabela|@Table|VIEW_NAME|3|  
|Coluna|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>Parâmetros do procedimento  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|SPECIFIC_CATALOG|1|  
|Proprietário|@Owner|SPECIFIC_SCHEMA|2|  
|Nome|@Name|SPECIFIC_NAME|3|  
|Parâmetro|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Procedimentos  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|SPECIFIC_CATALOG|1|  
|Proprietário|@Owner|SPECIFIC_SCHEMA|2|  
|Nome|@Name|SPECIFIC_NAME|3|  
|Type|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>Colunas de Índice  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|db_name|1|  
|Proprietário|@Owner|user_name|2|  
|Tabela|@Table|o.name|3|  
|Constraintname|@ConstraintName|x.name|4|  
|Coluna|@Column|c.name|5|  
  
### <a name="indexes"></a>Índices  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|db_name|1|  
|Proprietário|@Owner|user_name|2|  
|Tabela|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|tipos.assembly_class|2|  
  
### <a name="foreignkeys"></a>Chaves estrangeiras  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|CONSTRAINT_CATALOG|1|  
|Proprietário|@Owner|CONSTRAINT_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Nome|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>Restrições ao esquema do SQL Server 2008  
 As tabelas a seguir listam as restrições para coleções de esquemas do SQL Server 2008. Essas restrições são válidas a partir da versão 3.5 SP1 do .NET Framework e do SQL Server 2008. Eles não são suportados em versões anteriores do .NET Framework e SQL Server.  
  
### <a name="columnsetcolumns"></a>ColunasSetColunas  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>Todas as Colunas  
  
|Nome da restrição|Nome do Parâmetro|Padrão de restrição|Número de restrição|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catálogo|@Catalog|TABLE_CATALOG|1|  
|Proprietário|@Owner|TABLE_SCHEMA|2|  
|Tabela|@Table|TABLE_NAME|3|  
|Coluna|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Confira também

- [Visão geral do ADO.NET](ado-net-overview.md)
