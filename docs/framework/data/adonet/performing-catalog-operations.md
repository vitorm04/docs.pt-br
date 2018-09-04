---
title: Executando operações de catálogo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 7588b2b4592a5298a69eb4adfbc06edb6913ef76
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519090"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="e558c-102">Executando operações de catálogo</span><span class="sxs-lookup"><span data-stu-id="e558c-102">Performing Catalog Operations</span></span>
<span data-ttu-id="e558c-103">Para executar um comando para modificar um banco de dados ou o catálogo, como a instrução CREATE TABLE ou CREATE PROCEDURE, criar uma **comando** usando as instruções SQL apropriadas do objeto e um **Conexão** objeto.</span><span class="sxs-lookup"><span data-stu-id="e558c-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="e558c-104">Execute o comando com o **ExecuteNonQuery** método o **comando** objeto.</span><span class="sxs-lookup"><span data-stu-id="e558c-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="e558c-105">O exemplo de código a seguir cria um procedimento armazenado em um banco de dados do Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e558c-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e558c-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e558c-106">See Also</span></span>  
 [<span data-ttu-id="e558c-107">Usando os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="e558c-107">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="e558c-108">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="e558c-108">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="e558c-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e558c-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
