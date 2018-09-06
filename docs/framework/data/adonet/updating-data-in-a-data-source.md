---
title: Atualizando dados em uma fonte de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: d7b57a9572a285dfdc13afb0a520de67e231a1c0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858018"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="8e6fa-102">Atualizando dados em uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="8e6fa-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="8e6fa-103">As instruções SQL que modificam dados (como UPDATE, INSERT ou DELETE) não retornam linhas.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="8e6fa-104">Da mesma forma, muitos procedimentos armazenados executam uma ação, mas não retornam linhas.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="8e6fa-105">Para executar comandos que não retornam linhas, criar uma **comando** objeto com o comando SQL apropriado e uma **Conexão**, incluindo quaisquer **parâmetros**.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="8e6fa-106">Execute o comando com o **ExecuteNonQuery** método o **comando** objeto.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="8e6fa-107">O **ExecuteNonQuery** método retorna um inteiro que representa o número de linhas afetadas pela instrução ou procedimento armazenado que foi executado.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="8e6fa-108">Se várias instruções tiverem sido executadas, o valor retornado é a soma dos registros afetados por todas as instruções executadas.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e6fa-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e6fa-109">Example</span></span>  
 <span data-ttu-id="8e6fa-110">O exemplo de código a seguir executa uma instrução INSERT para inserir um registro em um banco de dados usando **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="8e6fa-111">O exemplo de código a seguir executa o procedimento armazenado criado pelo código de exemplo na [executando operações de catálogo](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8e6fa-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span></span> <span data-ttu-id="8e6fa-112">Nenhuma linha é retornada pelo procedimento armazenado, portanto, o **ExecuteNonQuery** método é usado, mas o procedimento armazenado recebe um parâmetro de entrada e retorna um parâmetro de saída e um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="8e6fa-113">Para o <xref:System.Data.OleDb.OleDbCommand> objeto, o **ReturnValue** parâmetro deve ser adicionado para o **parâmetros** coleção primeiro.</span><span class="sxs-lookup"><span data-stu-id="8e6fa-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e6fa-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e6fa-114">See Also</span></span>  
 [<span data-ttu-id="8e6fa-115">Usando os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="8e6fa-115">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 <span data-ttu-id="8e6fa-116">[Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)</span><span class="sxs-lookup"><span data-stu-id="8e6fa-116">[Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)</span></span>  
 [<span data-ttu-id="8e6fa-117">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="8e6fa-117">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="8e6fa-118">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8e6fa-118">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
