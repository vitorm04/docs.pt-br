---
title: Inserindo uma imagem de um arquivo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.openlocfilehash: f2bc67b4130633fba3a6e42e2b6925fc09f835c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032416"
---
# <a name="inserting-an-image-from-a-file"></a><span data-ttu-id="b0a31-102">Inserindo uma imagem de um arquivo</span><span class="sxs-lookup"><span data-stu-id="b0a31-102">Inserting an Image from a File</span></span>
<span data-ttu-id="b0a31-103">Você pode gravar um objeto binário grande (BLOB) em um banco de dados como dados binários ou de caracteres, dependendo do tipo de campo na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="b0a31-103">You can write a binary large object (BLOB) to a database as either binary or character data, depending on the type of field at your data source.</span></span> <span data-ttu-id="b0a31-104">BLOB é um termo genérico que faz referência aos tipos de dados `text`, `ntext` e `image`, que normalmente contêm documentos e imagens.</span><span class="sxs-lookup"><span data-stu-id="b0a31-104">BLOB is a generic term that refers to the `text`, `ntext`, and `image` data types, which typically contain documents and pictures.</span></span>  
  
 <span data-ttu-id="b0a31-105">Para gravar um valor BLOB em seu banco de dados, emita a instrução INSERT ou UPDATE apropriada e passe o valor do BLOB como um parâmetro de entrada (consulte [Configurando parâmetros e tipos de dados do parâmetro](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)).</span><span class="sxs-lookup"><span data-stu-id="b0a31-105">To write a BLOB value to your database, issue the appropriate INSERT or UPDATE statement and pass the BLOB value as an input parameter (see [Configuring Parameters and Parameter Data Types](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)).</span></span> <span data-ttu-id="b0a31-106">Se seu BLOB estiver armazenado como texto, como um campo `text` do SQL Server, você poderá passar o BLOB como um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b0a31-106">If your BLOB is stored as text, such as a SQL Server `text` field, you can pass the BLOB as a string parameter.</span></span> <span data-ttu-id="b0a31-107">Se o BLOB estiver armazenado no formato binário, como um campo `image` do SQL Server, você poderá passar uma matriz do tipo `byte` como um parâmetro binário.</span><span class="sxs-lookup"><span data-stu-id="b0a31-107">If the BLOB is stored in binary format, such as a SQL Server `image` field, you can pass an array of type `byte` as a binary parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0a31-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0a31-108">Example</span></span>  
 <span data-ttu-id="b0a31-109">O exemplo de código a seguir adiciona informações do funcionário à tabela Employees no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="b0a31-109">The following code example adds employee information to the Employees table in the Northwind database.</span></span> <span data-ttu-id="b0a31-110">Uma foto do funcionário é lida de um arquivo e adicionada ao campo Photo na tabela, que é um campo de imagem.</span><span class="sxs-lookup"><span data-stu-id="b0a31-110">A photo of the employee is read from a file and added to the Photo field in the table, which is an image field.</span></span>  
  
```vb  
Public Shared Sub AddEmployee( _  
  lastName As String, _  
  firstName As String, _  
  title As String, _  
  hireDate As DateTime, _  
  reportsTo As Integer, _  
  photoFilePath As String, _  
  connectionString As String)  
  
  Dim photo() as Byte = GetPhoto(photoFilePath)  
  
  Using connection As SqlConnection = New SqlConnection( _  
    connectionString)  
  
  Dim command As SqlCommand = New SqlCommand( _  
    "INSERT INTO Employees (LastName, FirstName, Title, " & _  
    "HireDate, ReportsTo, Photo) " & _  
    "Values(@LastName, @FirstName, @Title, " & _  
    "@HireDate, @ReportsTo, @Photo)", connection)   
  
  command.Parameters.Add("@LastName",  _  
    SqlDbType.NVarChar, 20).Value = lastName  
  command.Parameters.Add("@FirstName", _  
    SqlDbType.NVarChar, 10).Value = firstName  
  command.Parameters.Add("@Title", _  
    SqlDbType.NVarChar, 30).Value = title  
  command.Parameters.Add("@HireDate", _  
    SqlDbType.DateTime).Value = hireDate  
  command.Parameters.Add("@ReportsTo", _  
    SqlDbType.Int).Value = reportsTo  
  
  command.Parameters.Add("@Photo", _  
    SqlDbType.Image, photo.Length).Value = photo  
  
  connection.Open()  
  command.ExecuteNonQuery()  
  
  End Using  
End Sub  
  
Public Shared Function GetPhoto(filePath As String) As Byte()  
  Dim stream As FileStream = new FileStream( _  
     filePath, FileMode.Open, FileAccess.Read)  
  Dim reader As BinaryReader = new BinaryReader(stream)  
  
  Dim photo() As Byte = reader.ReadBytes(stream.Length)  
  
  reader.Close()  
  stream.Close()  
  
  Return photo  
End Function  
```  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0a31-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0a31-111">See also</span></span>

- [<span data-ttu-id="b0a31-112">Usando os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="b0a31-112">Using Commands to Modify Data</span></span>](../../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [<span data-ttu-id="b0a31-113">Recuperando dados binários</span><span class="sxs-lookup"><span data-stu-id="b0a31-113">Retrieving Binary Data</span></span>](../../../../../docs/framework/data/adonet/retrieving-binary-data.md)
- <span data-ttu-id="b0a31-114">[SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b0a31-114">[SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)</span></span>
- [<span data-ttu-id="b0a31-115">Mapeamentos de tipo de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="b0a31-115">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- <span data-ttu-id="b0a31-116">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b0a31-116">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
