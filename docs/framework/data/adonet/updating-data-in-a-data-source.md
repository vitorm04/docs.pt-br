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
# <a name="updating-data-in-a-data-source"></a>Atualizando dados em uma fonte de dados

As instruções SQL que modificam dados (como UPDATE, INSERT ou DELETE) não retornam linhas. Da mesma forma, muitos procedimentos armazenados executam uma ação, mas não retornam linhas. Para executar comandos que não retornam linhas, crie um objeto de **comando** com o comando SQL apropriado e uma **conexão**, incluindo todos os **parâmetros**necessários. Execute o comando com o método **ExecuteNonQuery** do objeto **Command** .  
  
 O método **ExecuteNonQuery** retorna um inteiro que representa o número de linhas afetadas pela instrução ou pelo procedimento armazenado que foi executado. Se várias instruções tiverem sido executadas, o valor retornado é a soma dos registros afetados por todas as instruções executadas.  
  
## <a name="example"></a>Exemplo  

 O exemplo de código a seguir executa uma instrução INSERT para inserir um registro em um banco de dados usando **ExecuteNonQuery**.  
  
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
  
 O exemplo de código a seguir executa o procedimento armazenado criado pelo código de exemplo em [executando operações de catálogo](performing-catalog-operations.md). Nenhuma linha é retornada pelo procedimento armazenado, portanto, o método **ExecuteNonQuery** é usado, mas o procedimento armazenado recebe um parâmetro de entrada e retorna um parâmetro de saída e um valor de retorno.  
  
 Para o <xref:System.Data.OleDb.OleDbCommand> objeto, o parâmetro **ReturnValue** deve ser adicionado primeiro à coleção **Parameters** .  
  
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
  
## <a name="see-also"></a>Veja também

- [Usar os comandos para modificar dados](using-commands-to-modify-data.md)
- [Atualizando fontes de dados com DataAdapters](updating-data-sources-with-dataadapters.md)
- [Comandos e parâmetros](commands-and-parameters.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
