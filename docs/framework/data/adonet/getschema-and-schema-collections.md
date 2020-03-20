---
title: GetSchema e coleções de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: e18c23e9bbec97a64110aba6eb7241761ecece06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149551"
---
# <a name="getschema-and-schema-collections"></a>GetSchema e coleções de esquema
As classes **De Conexão** em cada um dos provedores gerenciados do .NET Framework implementam um método **GetSchema** que é usado para recuperar informações de esquema sobre <xref:System.Data.DataTable>o banco de dados atualmente conectado, e as informações de esquema retornadas do método **GetSchema** vêm na forma de um . O método **GetSchema** é um método sobrecarregado que fornece parâmetros opcionais para especificar a coleta de esquemas para retornar e restringir a quantidade de informações devolvidas.  
  
## <a name="specifying-the-schema-collections"></a>Especificando as Coleções de Esquema  
 O primeiro parâmetro opcional do método **GetSchema** é o nome de coleta que é especificado como uma string. Existem dois tipos de coleções de esquemas: coleções de esquemas comuns que são comuns a todos os provedores, e coleções específicas de esquemas específicos que são específicas para cada provedor.  
  
 Você pode consultar um provedor gerenciado pelo .NET Framework para determinar a lista de coleções de esquemas suportadas chamando o método **GetSchema** sem argumentos ou com o nome de coleta de esquemas "MetaDataCollections". Isso retornará <xref:System.Data.DataTable> um com uma lista das coleções de esquemas suportadas, o número de restrições que cada um suporta e o número de peças de identificação que eles usam.  
  
### <a name="retrieving-schema-collections-example"></a>Recuperando o exemplo das coleções de esquemas  
 Os exemplos a seguir demonstram <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> como usar o método do .NET <xref:System.Data.SqlClient.SqlConnection> Framework Data Provider para a classe SQL Server para recuperar informações de esquema sobre todas as tabelas contidas no banco de dados de amostra **do AdventureWorks:**  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
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
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
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
  
## <a name="see-also"></a>Confira também

- [Recuperando informações de esquema de banco de dados](retrieving-database-schema-information.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
