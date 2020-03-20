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
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="9cddd-102">GetSchema e coleções de esquema</span><span class="sxs-lookup"><span data-stu-id="9cddd-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="9cddd-103">As classes **De Conexão** em cada um dos provedores gerenciados do .NET Framework implementam um método **GetSchema** que é usado para recuperar informações de esquema sobre <xref:System.Data.DataTable>o banco de dados atualmente conectado, e as informações de esquema retornadas do método **GetSchema** vêm na forma de um .</span><span class="sxs-lookup"><span data-stu-id="9cddd-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="9cddd-104">O método **GetSchema** é um método sobrecarregado que fornece parâmetros opcionais para especificar a coleta de esquemas para retornar e restringir a quantidade de informações devolvidas.</span><span class="sxs-lookup"><span data-stu-id="9cddd-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="9cddd-105">Especificando as Coleções de Esquema</span><span class="sxs-lookup"><span data-stu-id="9cddd-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="9cddd-106">O primeiro parâmetro opcional do método **GetSchema** é o nome de coleta que é especificado como uma string.</span><span class="sxs-lookup"><span data-stu-id="9cddd-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="9cddd-107">Existem dois tipos de coleções de esquemas: coleções de esquemas comuns que são comuns a todos os provedores, e coleções específicas de esquemas específicos que são específicas para cada provedor.</span><span class="sxs-lookup"><span data-stu-id="9cddd-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="9cddd-108">Você pode consultar um provedor gerenciado pelo .NET Framework para determinar a lista de coleções de esquemas suportadas chamando o método **GetSchema** sem argumentos ou com o nome de coleta de esquemas "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="9cddd-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="9cddd-109">Isso retornará <xref:System.Data.DataTable> um com uma lista das coleções de esquemas suportadas, o número de restrições que cada um suporta e o número de peças de identificação que eles usam.</span><span class="sxs-lookup"><span data-stu-id="9cddd-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="9cddd-110">Recuperando o exemplo das coleções de esquemas</span><span class="sxs-lookup"><span data-stu-id="9cddd-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="9cddd-111">Os exemplos a seguir demonstram <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> como usar o método do .NET <xref:System.Data.SqlClient.SqlConnection> Framework Data Provider para a classe SQL Server para recuperar informações de esquema sobre todas as tabelas contidas no banco de dados de amostra **do AdventureWorks:**</span><span class="sxs-lookup"><span data-stu-id="9cddd-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9cddd-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="9cddd-112">See also</span></span>

- [<span data-ttu-id="9cddd-113">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="9cddd-113">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="9cddd-114">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9cddd-114">ADO.NET Overview</span></span>](ado-net-overview.md)
