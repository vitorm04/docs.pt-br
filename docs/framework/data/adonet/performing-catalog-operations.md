---
title: Executar operações de catálogo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 802762592a63a2046abcde8ed83ac67be47faf96
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161640"
---
# <a name="performing-catalog-operations"></a>Executar operações de catálogo

Para executar um comando para modificar um banco de dados ou catálogo, como a instrução CREATE TABLE ou criar procedimento, crie um objeto de **comando** usando as instruções SQL apropriadas e um objeto de **conexão** . Execute o comando com o método **ExecuteNonQuery** do objeto **Command** .  
  
 O exemplo de código a seguir cria um procedimento armazenado em um banco de dados Microsoft SQL Server.  
  
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
  
## <a name="see-also"></a>Confira também

- [Usar os comandos para modificar dados](using-commands-to-modify-data.md)
- [Comandos e parâmetros](commands-and-parameters.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
