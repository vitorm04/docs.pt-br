---
title: Parâmetros de valores de tabela
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 333154f26a575886f19a914ce2f91beebd6be49e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742509"
---
# <a name="table-valued-parameters"></a>Parâmetros de valores de tabela
Os parâmetros com valor de tabela fornecem uma maneira fácil de empacotar várias linhas de dados de um aplicativo cliente para o SQL Server sem exigir várias viagens de ida e volta ou lógica especial do lado do servidor para processar os dados. Você pode usar parâmetros de valores de tabela para encapsular linhas de dados em um aplicativo cliente e enviar os dados para o servidor em um único comando parametrizado. As linhas de dados de entrada são armazenadas em uma variável da tabela que pode, em seguida, ser operada usando o [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].  
  
 Os valores de coluna em parâmetros de valores de tabela podem ser acessados usando instruções SELECT padrão do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]. Os parâmetros de valores de tabela são fortemente tipados e sua estrutura é validada automaticamente. O tamanho de parâmetros de valores de tabela é delimitado somente pela memória do servidor.  
  
> [!NOTE]
>  Você não pode retornar dados em um parâmetro com valor de tabela. Os parâmetros de valores de tabela são somente entrada; a palavra-chave OUTPUT não tem suporte.  
  
 Para obter mais informações sobre parâmetros de valores de tabela, consulte os seguintes recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Parâmetros com valor de tabela (mecanismo de banco de dados)](https://go.microsoft.com/fwlink/?LinkId=98363) nos Manuais Online do SQL Server|Descreve como criar e usar parâmetros de valores de tabela.|  
|[Tipos de tabela definidos pelo usuário](https://go.microsoft.com/fwlink/?LinkId=98364) nos Manuais Online do SQL Server|Descreve os tipos de tabela definidos pelo usuário que são usados para declarar parâmetros de valores de tabela.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Passando várias linhas em versões anteriores do SQL Server  
 Antes de parâmetros com valor de tabela foram introduzidos no SQL Server 2008, as opções para passar várias linhas de dados para um procedimento armazenado ou um comando SQL parametrizado eram limitadas. Um desenvolvedor poderia escolher as seguintes opções para passar várias linhas para o servidor:  
  
-   Usar uma série de parâmetros individuais para representar os valores em várias colunas e linhas de dados. A quantidade de dados que podem ser passados usando esse método é limitada pelo número de parâmetros permitidos. Procedimentos do SQL Server podem ter, no máximo, 2100 parâmetros. A lógica do lado do servidor é necessária para reunir esses valores individuais em uma variável da tabela ou uma tabela temporária para processamento.  
  
-   Empacotar vários valores de dados em cadeias de caracteres delimitados ou documentos XML e, em seguida, passar esses valores de texto para um procedimento ou a uma instrução. Isso exige que o procedimento ou a declaração inclua a lógica necessária para validar as estruturas de dados e desempacotar os valores.  
  
-   Criar uma série de instruções SQL individuais para as modificações de dados que afetam várias linhas, como as criadas chamando o método `Update` de um <xref:System.Data.SqlClient.SqlDataAdapter>. As alterações podem ser enviadas para o servidor individualmente ou serem distribuídas em grupos. No entanto, mesmo quando enviadas em lotes que contêm várias instruções, cada declaração é executada separadamente no servidor.  
  
-   Use o programa de utilitário do `bcp` ou o objeto de <xref:System.Data.SqlClient.SqlBulkCopy> para carregar várias linhas de dados em uma tabela. Embora essa técnica seja muito eficiente, ela não dá suporte ao processamento do lado do servidor a menos que os dados sejam carregados em uma tabela temporária ou uma variável da tabela.  
  
## <a name="creating-table-valued-parameter-types"></a>Criando tipos de parâmetro com valor de tabela  
 Os parâmetros de valores de tabela são baseados em estruturas de tabela fortemente tipadas que são definidas usando as instruções CREATE TYPE do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]. Você precisa criar um tipo de tabela e definir a estrutura no SQL Server antes de poder usar parâmetros com valor de tabela em seus aplicativos cliente. Para obter mais informações sobre como criar tipos de tabela, consulte [tipos de tabela definidos pelo usuário](https://go.microsoft.com/fwlink/?LinkID=98364) nos Manuais Online do SQL Server.  
  
 A instrução a seguir cria um tipo de tabela chamado CategoryTableType composto pelas colunas CategoryID e CategoryName:  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Depois de criar um tipo de tabela, você poderá declarar parâmetros de valores de tabela com base nesse tipo. O fragmento do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] a seguir demonstra como declarar um parâmetro com valor de tabela em uma definição de procedimento armazenado. Observe que a palavra-chave READONLY é necessária para declarar um parâmetro com valor de tabela.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Modificando dados com parâmetros de valores de tabela (Transact-SQL)  
 Os parâmetros de valores de tabela podem ser usados em modificações de dados baseadas em conjuntos que afetam várias linhas executando uma única instrução. Por exemplo, você pode selecionar todas as linhas em um parâmetro com valor de tabela e inseri-las em uma tabela de banco de dados, ou você pode criar uma instrução de atualização unindo um parâmetro com valor de tabela à tabela que você deseja atualizar.  
  
 A instrução UPDATE do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] a seguir demonstra como usar um parâmetro com valor de tabela unindo-a à tabela Categories. Quando você usa um parâmetro com valor de tabela com um JOIN em uma cláusula FROM, você deverá também utilizar um alias, como mostrado aqui, onde o alias do parâmetro com valor de tabela é “ec”:  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 Este exemplo de [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] demonstra como selecionar linhas de um parâmetro com valor de tabela para realizar um INSERT em uma única operação baseada em conjuntos.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Limitações de parâmetros de valores de tabela  
 Há várias limitações para os parâmetros de valores de tabela:  
  
-   Você não pode passar parâmetros com valor de tabela [funções CLR definidas pelo usuário](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).  
  
-   Os parâmetros de valores de tabela somente podem ser indexados para oferecer suporte às restrições UNIQUE ou PRIMARY KEY. SQL Server não mantém estatísticas sobre parâmetros com valor de tabela.  
  
-   Os parâmetros com valor de tabela são somente leitura no código do [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]. Você não pode atualizar os valores da coluna nas linhas de um parâmetro com valor de tabela e você não pode inserir ou excluir linhas. Para modificar os dados que são passados para um procedimento armazenado ou instrução parametrizada no parâmetro com valor de tabela, você deverá inserir os dados em uma tabela temporária ou variável da tabela.  
  
-   Você não pode usar instruções ALTER TABLE para modificar o design de parâmetros de valores de tabela.  
  
## <a name="configuring-a-sqlparameter-example"></a>Configurando um exemplo de SqlParameter  
 <xref:System.Data.SqlClient> dá suporte ao preenchimento de parâmetros com valor de tabela do <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> ou <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objetos. Você deve especificar um nome de tipo para o parâmetro com valor de tabela usando a propriedade <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> de um <xref:System.Data.SqlClient.SqlParameter>. O `TypeName` deve corresponder ao nome de um tipo compatível criado anteriormente no servidor. O fragmento de código a seguir demonstra como configurar o <xref:System.Data.SqlClient.SqlParameter> para inserir dados.  
  
```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 Você também pode usar qualquer objeto derivado do <xref:System.Data.Common.DbDataReader> para transmitir as linhas de dados para um parâmetro com valor de tabela, conforme mostrado neste fragmento:  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a>Passando um parâmetro com valor de tabela para um procedimento armazenado  
 Este exemplo demonstra como passar dados de parâmetro com valor de tabela para um procedimento armazenado. O código extrai linhas adicionadas em um novo <xref:System.Data.DataTable> usando o método <xref:System.Data.DataTable.GetChanges%2A>. O código em seguida define um <xref:System.Data.SqlClient.SqlCommand>, definindo a propriedade <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> como <xref:System.Data.CommandType.StoredProcedure>. O <xref:System.Data.SqlClient.SqlParameter> é preenchido usando o método <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> e o <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> é definido como `Structured`. O <xref:System.Data.SqlClient.SqlCommand> é, em seguida, executado usando o método <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>.  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Passando um parâmetro com valor de tabela para uma instrução SQL parametrizada  
 O exemplo a seguir demonstra como inserir dados na tabela dbo.Categories usando uma instrução INSERT com uma subconsulta SELECT que tem um parâmetro com valor de tabela como a fonte de dados. Ao passar um parâmetro com valor de tabela para uma instrução SQL parametrizada, você deve especificar um nome de tipo para o parâmetro com valor de tabela usando a nova propriedade <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> de um <xref:System.Data.SqlClient.SqlParameter>. Esse `TypeName` deve corresponder ao nome de um tipo compatível criado anteriormente no servidor. O código nesse exemplo usa a propriedade `TypeName` para fazer referência à estrutura do tipo definida em dbo.CategoryTableType.  
  
> [!NOTE]
>  Se você fornecer um valor para uma coluna de identidade em um parâmetro com valor de tabela, deverá emitir a instrução SET IDENTITY_INSERT para a sessão.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a>Transmitindo linhas com um DataReader  
 Você também pode usar qualquer objeto derivado do <xref:System.Data.Common.DbDataReader> para transmitir as linhas de dados para um parâmetro com valor de tabela. O fragmento de código a seguir demonstra a recuperação de dados de um banco de dados Oracle usando <xref:System.Data.OracleClient.OracleCommand> e um <xref:System.Data.OracleClient.OracleDataReader>. O código em seguida configura um <xref:System.Data.SqlClient.SqlCommand> para chamar um procedimento armazenado com um único parâmetro de entrada. A propriedade <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> do <xref:System.Data.SqlClient.SqlParameter> é definida como `Structured`. O <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passa o conjunto de resultados de `OracleDataReader` para o procedimento armazenado como um parâmetro com valor de tabela.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a>Consulte também  
 [Configurando parâmetros e tipos de dados de parâmetro](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Comandos e parâmetros](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Parâmetros DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
