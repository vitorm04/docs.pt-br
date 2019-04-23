---
title: Executar operações de catálogo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: beb5d2db898df1c98662d53190ac1432acc746e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141447"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="4750d-102">Executar operações de catálogo</span><span class="sxs-lookup"><span data-stu-id="4750d-102">Performing Catalog Operations</span></span>
<span data-ttu-id="4750d-103">Para executar um comando para modificar um banco de dados ou o catálogo, como a instrução CREATE TABLE ou CREATE PROCEDURE, criar uma **comando** usando as instruções SQL apropriadas do objeto e um **Conexão** objeto.</span><span class="sxs-lookup"><span data-stu-id="4750d-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="4750d-104">Execute o comando com o **ExecuteNonQuery** método o **comando** objeto.</span><span class="sxs-lookup"><span data-stu-id="4750d-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="4750d-105">O exemplo de código a seguir cria um procedimento armazenado em um banco de dados do Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4750d-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +   
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +   
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +   
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="4750d-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4750d-106">See also</span></span>

- [<span data-ttu-id="4750d-107">Usando os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="4750d-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [<span data-ttu-id="4750d-108">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="4750d-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- <span data-ttu-id="4750d-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4750d-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
