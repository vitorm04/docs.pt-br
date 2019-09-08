---
title: Atualizando dados em uma fonte de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 0926e3c6513a698ae47b9983d0e6ad195394a4df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780618"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="2844d-102">Atualizando dados em uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="2844d-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="2844d-103">As instruções SQL que modificam dados (como UPDATE, INSERT ou DELETE) não retornam linhas.</span><span class="sxs-lookup"><span data-stu-id="2844d-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="2844d-104">Da mesma forma, muitos procedimentos armazenados executam uma ação, mas não retornam linhas.</span><span class="sxs-lookup"><span data-stu-id="2844d-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="2844d-105">Para executar comandos que não retornam linhas, crie um objeto de **comando** com o comando SQL apropriado e uma **conexão**, incluindo todos os **parâmetros**necessários.</span><span class="sxs-lookup"><span data-stu-id="2844d-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="2844d-106">Execute o comando com o método **ExecuteNonQuery** do objeto **Command** .</span><span class="sxs-lookup"><span data-stu-id="2844d-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="2844d-107">O método **ExecuteNonQuery** retorna um inteiro que representa o número de linhas afetadas pela instrução ou pelo procedimento armazenado que foi executado.</span><span class="sxs-lookup"><span data-stu-id="2844d-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="2844d-108">Se várias instruções tiverem sido executadas, o valor retornado é a soma dos registros afetados por todas as instruções executadas.</span><span class="sxs-lookup"><span data-stu-id="2844d-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2844d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2844d-109">Example</span></span>  
 <span data-ttu-id="2844d-110">O exemplo de código a seguir executa uma instrução INSERT para inserir um registro em um banco de dados usando **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="2844d-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="2844d-111">O exemplo de código a seguir executa o procedimento armazenado criado pelo código de exemplo em [executando operações de catálogo](performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2844d-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="2844d-112">Nenhuma linha é retornada pelo procedimento armazenado, portanto, o método **ExecuteNonQuery** é usado, mas o procedimento armazenado recebe um parâmetro de entrada e retorna um parâmetro de saída e um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="2844d-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="2844d-113">Para o <xref:System.Data.OleDb.OleDbCommand> objeto, o parâmetro **ReturnValue** deve ser adicionado primeiro à coleção **Parameters** .</span><span class="sxs-lookup"><span data-stu-id="2844d-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2844d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2844d-114">See also</span></span>

- [<span data-ttu-id="2844d-115">Usando os comandos para modificar dados</span><span class="sxs-lookup"><span data-stu-id="2844d-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- <span data-ttu-id="2844d-116">[Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)</span><span class="sxs-lookup"><span data-stu-id="2844d-116">[Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md)</span></span>
- [<span data-ttu-id="2844d-117">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="2844d-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- <span data-ttu-id="2844d-118">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="2844d-118">[ADO.NET Overview](ado-net-overview.md)</span></span>
