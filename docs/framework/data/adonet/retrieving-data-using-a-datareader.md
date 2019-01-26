---
title: Recuperando dados usando um DataReader
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 75d1dba6678be0bfa45be5f3e60e8e76f80a7e9e
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083841"
---
# <a name="retrieve-data-using-a-datareader"></a>Recuperar dados usando um DataReader
Para recuperar dados usando um **DataReader**, crie uma instância das **comando** do objeto e, em seguida, crie um **DataReader** chamando **ExecuteReader**  para recuperar linhas de uma fonte de dados. O **DataReader** fornece um fluxo não armazenado em buffer de dados que permite que a lógica procedural processe com eficiência os resultados de uma fonte de dados em sequência. O **DataReader** é uma boa opção quando você estiver recuperando grandes quantidades de dados porque os dados não é armazenado em cache na memória.

O exemplo a seguir ilustra o uso de um **DataReader**, onde `reader` representa um DataReader válido e `command` representa um objeto de comando válido.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Use o **DataReader.Read** método para obter uma linha dos resultados da consulta. Você pode acessar cada coluna da linha retornada passando o nome ou número ordinal da coluna para o **DataReader**. No entanto, para melhor desempenho, o **DataReader** fornece uma série de métodos que permitem que você acesse valores de coluna em seus tipos de dados nativos (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**e assim por diante). Para obter uma lista de métodos de acessador tipado para dados específicos do provedor **DataReaders**, consulte <xref:System.Data.OleDb.OleDbDataReader> e <xref:System.Data.SqlClient.SqlDataReader>. Usando os métodos de acessador digitadas quando você souber que os dados subjacentes tipo reduz a quantidade de conversão de tipos necessária ao recuperar o valor da coluna.  
  
 O exemplo a seguir itera por meio de um **DataReader** de objeto e retorna duas colunas de cada linha.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Fechando o DataReader  
 Sempre chamar o **feche** método quando você terminar de usar o **DataReader** objeto.  
  
 Se sua **comando** contém a saída de parâmetros ou valores de retorno, esses valores não estarão disponíveis até que o **DataReader** está fechado.  
  
 Enquanto um **DataReader** é aberto, o **Conexão** está sendo usado exclusivamente pelo **DataReader**. Você não pode executar nenhum comando para o **Conexão**, incluindo a criação de outro **DataReader**, até que o original **DataReader** está fechado.  
  
> [!NOTE]
>  Não chame **feche** ou **Dispose** em um **Conexão**, um **DataReader**, ou qualquer outro objeto gerenciado no **Finalize**  método de sua classe. Em um finalizador, libere somente recursos não gerenciados que sua classe possui diretamente. Se sua classe não possuir nenhum recurso não gerenciado, não inclua uma **Finalize** método em sua definição de classe. Para obter mais informações, consulte [coleta de lixo](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Recuperar resultados múltiplos define usando NextResult  
 Se o **DataReader** retorna vários conjuntos de resultados, a chamada a **NextResult** define um método para iterar por meio de resultados em sequência. O exemplo a seguir mostra <xref:System.Data.SqlClient.SqlDataReader> processando os resultados de duas instruções SELECT usando o método <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Obtendo informações de esquema do DataReader  
 Enquanto um **DataReader** é aberto, você pode recuperar informações de esquema sobre o atual conjunto de resultados usando o **GetSchemaTable** método. **GetSchemaTable** retorna um <xref:System.Data.DataTable> objeto preenchido com linhas e colunas que contêm as informações de esquema para o conjunto de resultados atual. O **DataTable** contém uma linha para cada coluna do conjunto de resultados. Cada coluna da tabela de esquema é mapeada para uma propriedade de colunas retornadas no conjunto as linhas do resultado, em que o **ColumnName** é o nome da propriedade e o valor da coluna é o valor da propriedade. O exemplo a seguir grava as informações de esquema **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Trabalhando com capítulos OLE DB  
 Conjuntos de linhas hierárquicos ou capítulos (tipo OLE DB **DBTYPE_HCHAPTER**, tipo ADO **adChapter**), podem ser recuperados usando o <xref:System.Data.OleDb.OleDbDataReader>. Quando uma consulta que inclui um capítulo é retornada como um **DataReader**, o capítulo é retornado como uma coluna em que **DataReader** e é exposta como um **DataReader** objeto.  
  
 O ADO.NET **conjunto de dados** também pode ser usado para representar conjuntos de linhas hierárquicos usando relações pai-filho entre tabelas. Para obter mais informações, consulte [DataSets, DataTables e DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 O exemplo de código a seguir usa o provedor de MSDataShape para gerar uma coluna de capítulo de pedidos para cada cliente em uma lista de clientes.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Retornando resultados com REF CURSORs do Oracle  
 O Provedor de Dados .NET Framework para Oracle oferece suporte ao uso de REF CURSORs Oracle para retornar um resultado de consulta. Um REF CURSOR Oracle é retornado como um <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Você pode recuperar um <xref:System.Data.OracleClient.OracleDataReader> objeto que representa um REF CURSOR Oracle usando o <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> método. Você também pode especificar uma <xref:System.Data.OracleClient.OracleCommand> que retorna um ou mais REF CURSORs Oracle como o **SelectCommand** para um <xref:System.Data.OracleClient.OracleDataAdapter> usado para preencher um <xref:System.Data.DataSet>.  
  
 Para acessar um REF CURSOR retornado de uma fonte de dados Oracle, crie uma <xref:System.Data.OracleClient.OracleCommand> para a sua consulta e adicione um parâmetro de saída que referencie o REF CURSOR para o <xref:System.Data.OracleClient.OracleCommand.Parameters> coleção de seu <xref:System.Data.OracleClient.OracleCommand>. O nome do parâmetro deve corresponder ao nome do parâmetro REF CURSOR em sua consulta. Defina o tipo do parâmetro a ser <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>. O <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> método de seu <xref:System.Data.OracleClient.OracleCommand> retorna um <xref:System.Data.OracleClient.OracleDataReader> para o REF CURSOR.  
  
 Se seu <xref:System.Data.OracleClient.OracleCommand> retornar vários REF CURSORS, adicione vários parâmetros de saída. Você pode acessar diferentes REF CURSORs chamando o <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> método. A chamada para <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> retorna um <xref:System.Data.OracleClient.OracleDataReader> referenciando primeiro REF CURSOR. Em seguida, você pode chamar o <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> método para acessar REF CURSORs subsequentes. Embora os parâmetros em seu <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> parâmetros de saída de coleção correspondem o REF CURSOR pelo nome, o <xref:System.Data.OracleClient.OracleDataReader> acessa-os na ordem em que foram adicionados ao <xref:System.Data.OracleClient.OracleCommand.Parameters> coleção.  
  
 Por exemplo, considere o seguinte pacote Oracle e o corpo do pacote.  
  
```sql
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
  
 O código a seguir cria uma <xref:System.Data.OracleClient.OracleCommand> que retorna REF CURSORs do pacote Oracle anterior adicionando dois parâmetros de tipo <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> para o <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> coleção.  
  
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
  
 O código a seguir retorna os resultados do comando anterior usando o <xref:System.Data.OracleClient.OracleDataReader.Read> e <xref:System.Data.OracleClient.OracleDataReader.NextResult> métodos do <xref:System.Data.OracleClient.OracleDataReader>. Os parâmetros REF CURSOR são retornados em ordem.  
  
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
  
 O exemplo a seguir usa o comando anterior para preencher um <xref:System.Data.DataSet> com os resultados do pacote Oracle.  
  
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

> [!NOTE]
>  Para evitar uma **OverflowException**, é recomendável que você também pode manipular qualquer conversão do tipo NUMBER Oracle em um tipo válido do .NET Framework antes de armazenar o valor em um <xref:System.Data.DataRow>. Você pode usar o <xref:System.Data.Common.DataAdapter.FillError> evento para determinar se um **OverflowException** ocorreu. Para obter mais informações sobre o <xref:System.Data.Common.DataAdapter.FillError> eventos, consulte [manipulação de eventos DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Consulte também
- [Trabalhando com DataReaders](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)
- [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Recuperando informações de esquema de banco de dados](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
