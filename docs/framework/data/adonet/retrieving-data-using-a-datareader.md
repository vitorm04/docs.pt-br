---
title: Recuperando dados usando um DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 0c78db5ce7a6a988e40718daca1d828096a734d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353254"
---
# <a name="retrieving-data-using-a-datareader"></a>Recuperando dados usando um DataReader
Recuperando dados usando um **DataReader** envolve a criação de uma instância do **comando** objeto e, em seguida, criando um **DataReader** chamando  **ExecuteReader** para recuperar linhas de uma fonte de dados. O exemplo a seguir ilustra o uso uma **DataReader** onde `reader` representa um DataReader válido e `command` representa um objeto de comando válido.  
  
```  
reader = command.ExecuteReader();  
```  
  
 Você usa o **leitura** método o **DataReader** para obter uma linha dos resultados da consulta. Você pode acessar cada coluna da linha retornada, passando o nome ou a referência ordinal da coluna para o **DataReader**. No entanto, para melhor desempenho, o **DataReader** fornece uma série de métodos que permitem que você acesse os valores de coluna em seus tipos de dados nativos (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, e assim por diante). Para obter uma lista de métodos de acessador tipado para dados específicos do provedor **DataReaders**, consulte <xref:System.Data.OleDb.OleDbDataReader> e <xref:System.Data.SqlClient.SqlDataReader>. Usar os métodos de acessador tipados, supondo-se que o tipo de dados subjacente seja conhecido, reduz a quantidade de conversão de tipos necessária ao recuperar o valor da coluna.  
  
> [!NOTE]
>  A versão do Windows Server 2003 do .NET Framework inclui uma propriedade adicional para o **DataReader**, **HasRows**, que permite que você determine se o **DataReader**retornou nenhum resultado antes da leitura dele.  
  
 O exemplo de código a seguir itera por meio de um **DataReader** objeto e retorna duas colunas de cada linha.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 O **DataReader** fornece um fluxo sem buffer de dados que permite que a lógica de procedimento processar com eficácia sequencialmente os resultados de uma fonte de dados. O **DataReader** é uma boa opção quando recuperar grandes quantidades de dados porque os dados não é armazenado em cache na memória.  
  
## <a name="closing-the-datareader"></a>Fechando o DataReader  
 Você sempre deve chamar o **fechar** método quando você terminar de usar o **DataReader** objeto.  
  
 Se seu **comando** contém saída parâmetros ou valores de retorno, eles não estarão disponíveis até que o **DataReader** está fechado.  
  
 Observe que, embora uma **DataReader** é aberto, o **Conexão** está em uso exclusivamente pelo **DataReader**. Não é possível executar os comandos para o **Conexão**, incluindo a criação de outro **DataReader**, até que o original **DataReader** está fechado.  
  
> [!NOTE]
>  Não chame **fechar** ou **Dispose** em uma **Conexão**, um **DataReader**, ou qualquer outro objeto gerenciado no **Finalize**  método de sua classe. Em um finalizador, libere somente recursos não gerenciados que sua classe possui diretamente. Se sua classe não possui todos os recursos não gerenciados, não inclua um **Finalize** método em sua definição de classe. Para obter mais informações, consulte [coleta de lixo](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Recuperando vários conjuntos de resultados usando NextResult  
 Se vários conjuntos de resultados são retornados, o **DataReader** fornece o **NextResult** define um método para iterar o resultados em ordem. O exemplo a seguir mostra <xref:System.Data.SqlClient.SqlDataReader> processando os resultados de duas instruções SELECT usando o método <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Obtendo informações de esquema do DataReader  
 Enquanto um **DataReader** é aberto, você pode recuperar informações de esquema sobre o resultado atual definido usando o **GetSchemaTable** método. **GetSchemaTable** retorna um <xref:System.Data.DataTable> objeto preenchido com linhas e colunas que contêm as informações de esquema para o conjunto de resultados atual. O **DataTable** contém uma linha para cada coluna do conjunto de resultados. Cada coluna da linha da tabela de esquema é mapeado para uma propriedade da coluna retornada no conjunto de resultados, onde o **ColumnName** é o nome da propriedade e o valor da coluna é o valor da propriedade. O exemplo de código a seguir grava as informações de esquema **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Trabalhando com capítulos OLE DB  
 Conjuntos de linhas hierárquicos, ou capítulos (tipo de OLE DB **DBTYPE_HCHAPTER**, tipo ADO **adChapter**) podem ser recuperados usando o <xref:System.Data.OleDb.OleDbDataReader>. Quando uma consulta que inclui um capítulo é retornada como um **DataReader**, o capítulo é retornado como uma coluna em que **DataReader** e é exposto como um **DataReader** objeto.  
  
 O ADO.NET **DataSet** também pode ser usado para representar os conjuntos de linhas hierárquicos usando relações pai-filho entre tabelas. Para obter mais informações, consulte [DataSets, DataTables e DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 O exemplo de código a seguir usa o provedor de MSDataShape para gerar uma coluna de capítulo de pedidos para cada cliente em uma lista de clientes.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Retornando resultados com REF CURSORs Oracle  
 O Provedor de Dados .NET Framework para Oracle oferece suporte ao uso de REF CURSORs Oracle para retornar um resultado de consulta. Um REF CURSOR Oracle é retornado como um <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Você pode recuperar um **OracleDataReader** objeto que representa um Oracle REF CURSOR usando o <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> método e você também pode especificar um <xref:System.Data.OracleClient.OracleCommand> que retorna um ou mais REF CURSORs do Oracle como o  **SelectCommand** para um <xref:System.Data.OracleClient.OracleDataAdapter> usado para preencher um <xref:System.Data.DataSet>.  
  
 Para acessar uma REF CURSOR retornado de uma fonte de dados Oracle, crie um **OracleCommand** para sua consulta e adicione um parâmetro de saída que faz referência a REF CURSOR para o **parâmetros** coleção de seu  **OracleCommand**. O nome do parâmetro deve corresponder ao nome do parâmetro REF CURSOR em sua consulta. Defina o tipo do parâmetro para **OracleType**. O **ExecuteReader** método de sua **OracleCommand** retornará um **OracleDataReader** para REF CURSOR.  
  
 Se seu **OracleCommand** retorna vários CURSORES REF, adicionar vários parâmetros de saída. Você pode acessar os cursores de referência diferente chamando o **OracleCommand.ExecuteReader** método. A chamada para **ExecuteReader** retorna um **OracleDataReader** faz referência ao CURSOR REF primeiro. Em seguida, você pode chamar o **OracleDataReader.NextResult** método para acessar os cursores de REF subsequentes. Embora os parâmetros em seu **OracleCommand.Parameters** parâmetros de saída de correspondência de coleção REF CURSOR por nome, o **OracleDataReader** acessa-los na ordem em que foram adicionados para o  **Parâmetros** coleção.  
  
 Por exemplo, considere o seguinte pacote Oracle e o corpo do pacote.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 O código a seguir cria um **OracleCommand** que retorna os cursores de referência de pacote Oracle anterior adicionando dois parâmetros de tipo **OracleType** para o **parâmetros** coleção.  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 O código a seguir retorna os resultados do comando anterior usando o **leitura** e **NextResult** métodos do **OracleDataReader**. Os parâmetros REF CURSOR são retornados em ordem.  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 O exemplo a seguir usa o comando anterior para preencher um **DataSet** com os resultados do pacote Oracle.  
  
> [!NOTE]
>  Para evitar um **OverflowException**, é recomendável que você também pode manipular qualquer conversão do tipo de número de Oracle como um tipo válido do .NET Framework antes de armazenar o valor em uma **DataRow**. Você pode usar o **FillError** evento para determinar se um **OverflowException** ocorreu. Para obter mais informações sobre o **FillError** evento, consulte [manipulando eventos de DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com DataReaders](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Recuperando informações de esquema de banco de dados](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
