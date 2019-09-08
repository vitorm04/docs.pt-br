---
title: Executar operações de catálogo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 0291b6684092ec15fc672c39c909caf7781194e3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783248"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="4819a-102">Executar operações de catálogo</span><span class="sxs-lookup"><span data-stu-id="4819a-102">Performing Catalog Operations</span></span>
<span data-ttu-id="4819a-103">Para executar um comando para modificar um banco de dados ou catálogo, como a instrução CREATE TABLE ou criar procedimento, crie um objeto de **comando** usando as instruções SQL apropriadas e um objeto de **conexão** .</span><span class="sxs-lookup"><span data-stu-id="4819a-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="4819a-104">Execute o comando com o método **ExecuteNonQuery** do objeto **Command** .</span><span class="sxs-lookup"><span data-stu-id="4819a-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="4819a-105">O exemplo de código a seguir cria um procedimento armazenado em um banco de dados Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4819a-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4819a-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4819a-106">See also</span></span>

- [<span data-ttu-id="4819a-107">Usando os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="4819a-107">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="4819a-108">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="4819a-108">Commands and Parameters</span></span>](commands-and-parameters.md)
- <span data-ttu-id="4819a-109">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4819a-109">[ADO.NET Overview](ado-net-overview.md)</span></span>
