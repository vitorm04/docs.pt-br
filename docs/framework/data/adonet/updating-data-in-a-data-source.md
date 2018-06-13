---
title: Atualizando dados em uma fonte de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 11c3faa85d6d0b77c4e606815aa8252188b6f67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357787"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="60517-102">Atualizando dados em uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="60517-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="60517-103">As instruções SQL que modificam dados (como UPDATE, INSERT ou DELETE) não retornam linhas.</span><span class="sxs-lookup"><span data-stu-id="60517-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="60517-104">Da mesma forma, muitos procedimentos armazenados executam uma ação, mas não retornam linhas.</span><span class="sxs-lookup"><span data-stu-id="60517-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="60517-105">Para executar comandos que não retornam linhas, criar um **comando** objeto com o comando SQL apropriado e um **Conexão**, incluindo quaisquer **parâmetros**.</span><span class="sxs-lookup"><span data-stu-id="60517-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="60517-106">Execute o comando com o **ExecuteNonQuery** método o **comando** objeto.</span><span class="sxs-lookup"><span data-stu-id="60517-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="60517-107">O **ExecuteNonQuery** método retorna um inteiro que representa o número de linhas afetadas pela instrução ou procedimento armazenado foi executado.</span><span class="sxs-lookup"><span data-stu-id="60517-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="60517-108">Se várias instruções tiverem sido executadas, o valor retornado é a soma dos registros afetados por todas as instruções executadas.</span><span class="sxs-lookup"><span data-stu-id="60517-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60517-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60517-109">Example</span></span>  
 <span data-ttu-id="60517-110">O exemplo de código a seguir executa uma instrução INSERT para inserir um registro em um banco de dados usando **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="60517-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 <span data-ttu-id="60517-111">O exemplo de código a seguir executa o procedimento armazenado criado pelo código de exemplo no [executando operações de catálogo](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="60517-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span></span> <span data-ttu-id="60517-112">Nenhuma linha será retornada pelo procedimento armazenado, portanto, o **ExecuteNonQuery** método é usado, mas o procedimento armazenado receber um parâmetro de entrada e retorna um parâmetro de saída e um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="60517-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="60517-113">Para o <xref:System.Data.OleDb.OleDbCommand> objeto, o **ReturnValue** parâmetro deve ser adicionado para o **parâmetros** coleção primeiro.</span><span class="sxs-lookup"><span data-stu-id="60517-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a><span data-ttu-id="60517-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60517-114">See Also</span></span>  
 [<span data-ttu-id="60517-115">Usando os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="60517-115">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 <span data-ttu-id="60517-116">[Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)</span><span class="sxs-lookup"><span data-stu-id="60517-116">[Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)</span></span>  
 [<span data-ttu-id="60517-117">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="60517-117">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="60517-118">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="60517-118">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
