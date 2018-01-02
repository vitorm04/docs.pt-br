---
title: "GetSchema e coleções de esquema"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d982964b596528b091f5367edd38e0cee5f923c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="28c7d-102">GetSchema e coleções de esquema</span><span class="sxs-lookup"><span data-stu-id="28c7d-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="28c7d-103">O **Conexão** classes em cada uma da implementação de provedores gerenciados do .NET Framework um **GetSchema** método que é usado para recuperar informações de esquema sobre o banco de dados que está conectado no momento, e as informações de esquema retornadas do **GetSchema** método vem na forma de um <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="28c7d-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="28c7d-104">O **GetSchema** é um método sobrecarregado que fornece parâmetros opcionais para especificar a coleção de esquema para retornar e restringir a quantidade de informações retornadas.</span><span class="sxs-lookup"><span data-stu-id="28c7d-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="28c7d-105">Especificar as coleções de esquema</span><span class="sxs-lookup"><span data-stu-id="28c7d-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="28c7d-106">O primeiro parâmetro opcional do **GetSchema** método é o nome da coleção que é especificado como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28c7d-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="28c7d-107">Há dois tipos de coleções de esquema: coleções de esquema comuns que são comuns a todos os provedores e coleções de esquema específicos que são específicas para cada provedor.</span><span class="sxs-lookup"><span data-stu-id="28c7d-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="28c7d-108">Você pode consultar um provedor gerenciado do .NET Framework para determinar a lista de coleções de esquema com suporte ao chamar o **GetSchema** método sem argumentos, ou com o nome da coleção de esquema "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="28c7d-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="28c7d-109">Isso retornará um <xref:System.Data.DataTable> com uma lista de coleções de esquema com suporte, o número de restrições que oferecem suporte a cada um deles e o número de partes do identificador que eles usam.</span><span class="sxs-lookup"><span data-stu-id="28c7d-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="28c7d-110">Recuperando um exemplo de coleções de esquema</span><span class="sxs-lookup"><span data-stu-id="28c7d-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="28c7d-111">Os exemplos a seguir demonstram como usar o <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> método do .NET Framework Data Provider para SQL Server <xref:System.Data.SqlClient.SqlConnection> classe para recuperar informações de esquema sobre todas as tabelas contidas no **AdventureWorks**banco de dados de exemplo:</span><span class="sxs-lookup"><span data-stu-id="28c7d-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28c7d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28c7d-112">See Also</span></span>  
 [<span data-ttu-id="28c7d-113">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="28c7d-113">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="28c7d-114">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="28c7d-114">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
