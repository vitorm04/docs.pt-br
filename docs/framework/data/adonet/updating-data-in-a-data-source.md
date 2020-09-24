---
title: Atualizando dados em uma fonte de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 6b0234337c85ace0797d75b72560ccb55635daae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177261"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="586fc-102">Atualizando dados em uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="586fc-102">Updating Data in a Data Source</span></span>

<span data-ttu-id="586fc-103">As instruções SQL que modificam dados (como UPDATE, INSERT ou DELETE) não retornam linhas.</span><span class="sxs-lookup"><span data-stu-id="586fc-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="586fc-104">Da mesma forma, muitos procedimentos armazenados executam uma ação, mas não retornam linhas.</span><span class="sxs-lookup"><span data-stu-id="586fc-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="586fc-105">Para executar comandos que não retornam linhas, crie um objeto de **comando** com o comando SQL apropriado e uma **conexão**, incluindo todos os **parâmetros**necessários.</span><span class="sxs-lookup"><span data-stu-id="586fc-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="586fc-106">Execute o comando com o método **ExecuteNonQuery** do objeto **Command** .</span><span class="sxs-lookup"><span data-stu-id="586fc-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="586fc-107">O método **ExecuteNonQuery** retorna um inteiro que representa o número de linhas afetadas pela instrução ou pelo procedimento armazenado que foi executado.</span><span class="sxs-lookup"><span data-stu-id="586fc-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="586fc-108">Se várias instruções tiverem sido executadas, o valor retornado é a soma dos registros afetados por todas as instruções executadas.</span><span class="sxs-lookup"><span data-stu-id="586fc-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="586fc-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="586fc-109">Example</span></span>  

 <span data-ttu-id="586fc-110">O exemplo de código a seguir executa uma instrução INSERT para inserir um registro em um banco de dados usando **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="586fc-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="586fc-111">O exemplo de código a seguir executa o procedimento armazenado criado pelo código de exemplo em [executando operações de catálogo](performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="586fc-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="586fc-112">Nenhuma linha é retornada pelo procedimento armazenado, portanto, o método **ExecuteNonQuery** é usado, mas o procedimento armazenado recebe um parâmetro de entrada e retorna um parâmetro de saída e um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="586fc-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="586fc-113">Para o <xref:System.Data.OleDb.OleDbCommand> objeto, o parâmetro **ReturnValue** deve ser adicionado primeiro à coleção **Parameters** .</span><span class="sxs-lookup"><span data-stu-id="586fc-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="586fc-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="586fc-114">See also</span></span>

- [<span data-ttu-id="586fc-115">Usar os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="586fc-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="586fc-116">Atualizando fontes de dados com DataAdapters</span><span class="sxs-lookup"><span data-stu-id="586fc-116">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="586fc-117">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="586fc-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="586fc-118">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="586fc-118">ADO.NET Overview</span></span>](ado-net-overview.md)
