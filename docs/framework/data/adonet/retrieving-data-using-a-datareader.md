---
title: Recuperando dados usando um DataReader
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149018"
---
# <a name="retrieve-data-using-a-datareader"></a>Recuperar dados usando um DataReader
Para recuperar dados usando um **DataReader,** crie uma instância do objeto **Command** e crie um **DataReader** chamando **Command.ExecuteReader** para recuperar linhas de uma fonte de dados. O **DataReader** fornece um fluxo de dados não tamponado que permite que a lógica processual processe eficientemente os resultados de uma fonte de dados sequencialmente. O **DataReader** é uma boa escolha quando você está recuperando grandes quantidades de dados porque os dados não são armazenados em cache na memória.

O exemplo a seguir ilustra usando `reader` um **DataReader**, `command` onde representa um DataReader válido e representa um objeto de Comando válido.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Use o método **DataReader.Read** para obter uma linha dos resultados da consulta. Você pode acessar cada coluna da linha retornada passando o nome ou número ordinal da coluna para o **DataReader**. No entanto, para obter um melhor desempenho, o **DataReader** fornece uma série de métodos que permitem acessar valores de coluna em seus tipos de dados nativos (**GetDateTime**, **GetDouble,** **GetGuid,** **GetInt32,** e assim por diante). Para obter uma lista de métodos de acessórios digitados para **DataReaders**específicos do provedor de dados, consulte <xref:System.Data.OleDb.OleDbDataReader> e <xref:System.Data.SqlClient.SqlDataReader>. Usar os métodos do acessório digitado quando você sabe que o tipo de dados subjacente reduz a quantidade de conversão de tipo necessária ao recuperar o valor da coluna.  
  
 O exemplo a seguir itera através de um objeto **DataReader** e retorna duas colunas de cada linha.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Fechando o DataReader  
 Sempre chame o método **Fechar** quando terminar de usar o objeto **DataReader.**  
  
 Se **o** comando contiver parâmetros de saída ou valores de retorno, esses valores não estão disponíveis até que o **DataReader** seja fechado.  
  
 Enquanto um **DataReader** está aberto, a **Conexão** é usada exclusivamente por esse **DataReader**. Não é possível executar nenhum comando para a **Conexão**, incluindo a criação de outro **DataReader**, até que o **DataReader** original seja fechado.  
  
> [!NOTE]
> Não chame **Fechar** ou **Descartar em** uma **conexão,** um **DataReader**ou qualquer outro objeto gerenciado no método **Finalizar** da sua classe. Em um finalizador, libere somente recursos não gerenciados que sua classe possui diretamente. Se sua classe não possui nenhum recurso não gerenciado, não inclua um método **Finalizar** na sua definição de classe. Para obter mais informações, consulte [Coleta de Lixo](../../../standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Recuperando vários conjuntos de resultados usando NextResult  
 Se o **DataReader** retornar vários conjuntos de resultados, chame o método **NextResult** para iterar através dos conjuntos de resultados sequencialmente. O exemplo a seguir mostra <xref:System.Data.SqlClient.SqlDataReader> processando os resultados de duas instruções SELECT usando o método <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Obtendo informações sobre esquemas do DataReader  
 Enquanto um **DataReader** estiver aberto, você pode recuperar informações de esquema sobre o conjunto de resultados atuais usando o método **GetSchemaTable.** **GetSchemaTable** retorna <xref:System.Data.DataTable> um objeto preenchido com linhas e colunas que contêm as informações do esquema para o conjunto de resultados atual. A **Tabela de Dados** contém uma linha para cada coluna do conjunto de resultados. Cada coluna da tabela de esquema mapeia uma propriedade das colunas devolvidas nas linhas do conjunto de resultados, onde o **ColumnName** é o nome da propriedade e o valor da coluna é o valor da propriedade. O exemplo a seguir escreve as informações do esquema para **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Trabalhando com capítulos do OLE DB  
 Os conjuntos de linhas hierárquicas, ou capítulos **(tipo**OLE <xref:System.Data.OleDb.OleDbDataReader>DB DBTYPE_HCHAPTER , tipo ADO **adChapter**), podem ser recuperados usando o . Quando uma consulta que inclui um capítulo é retornada como um **DataReader,** o capítulo é retornado como uma coluna nesse **DataReader** e é exposto como um objeto **DataReader.**  
  
 O ADO.NET **DataSet** também pode ser usado para representar conjuntos de linhas hierárquicas usando relações pai-filho entre tabelas. Para obter mais informações, consulte [DataSets, DataTables e DataViews](./dataset-datatable-dataview/index.md).  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Retornando os resultados com cursors Oracle REF  
 O Provedor de Dados .NET Framework para Oracle oferece suporte ao uso de REF CURSORs Oracle para retornar um resultado de consulta. Um REF CURSOR Oracle é retornado como um <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Você pode <xref:System.Data.OracleClient.OracleDataReader> recuperar um objeto que representa um <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> CursoR Oracle REF usando o método. Você também pode <xref:System.Data.OracleClient.OracleCommand> especificar um que retorna um ou mais <xref:System.Data.OracleClient.OracleDataAdapter> CURSORs <xref:System.Data.DataSet>Oracle REF como o **SelectCommand** para um usado para preencher um .  
  
 Para acessar um CURSOR REF retornado de <xref:System.Data.OracleClient.OracleCommand> uma fonte de dados Oracle, crie um para sua <xref:System.Data.OracleClient.OracleCommand.Parameters> consulta e <xref:System.Data.OracleClient.OracleCommand>adicione um parâmetro de saída que referencia o CURSOR REF à coleção do seu . O nome do parâmetro deve corresponder ao nome do parâmetro REF CURSOR em sua consulta. Defina o tipo do <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>parâmetro para . O <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> método <xref:System.Data.OracleClient.OracleCommand> de <xref:System.Data.OracleClient.OracleDataReader> seu retorna um para o CURSOR REF.  
  
 Se <xref:System.Data.OracleClient.OracleCommand> o seu retornar vários CURSORS REF, adicione vários parâmetros de saída. Você pode acessar os diferentes CURSORs REF chamando o <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> método. A chamada <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> para <xref:System.Data.OracleClient.OracleDataReader> retornar uma referência ao primeiro CURSOR REF. Em seguida, <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> você pode chamar o método para acessar cursors de REF subseqüentes. Embora os parâmetros em sua <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> coleção correspondam aos <xref:System.Data.OracleClient.OracleDataReader> parâmetros de saída ref cursor <xref:System.Data.OracleClient.OracleCommand.Parameters> por nome, os acessa na ordem em que foram adicionados à coleção.  
  
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
  
 O código a <xref:System.Data.OracleClient.OracleCommand> seguir cria um que retorna os CURSORs REF <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> do <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> pacote Oracle anterior adicionando dois parâmetros de tipo à coleção.  
  
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
  
 O código a seguir retorna os <xref:System.Data.OracleClient.OracleDataReader.Read> resultados <xref:System.Data.OracleClient.OracleDataReader.NextResult> do comando <xref:System.Data.OracleClient.OracleDataReader>anterior usando os métodos e métodos do . Os parâmetros REF CURSOR são retornados em ordem.  
  
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
  
 O exemplo a seguir usa <xref:System.Data.DataSet> o comando anterior para preencher um com os resultados do pacote Oracle.  
  
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
> Para evitar uma **Exceção de Estouro,** recomendamos que você também manuseie qualquer conversão do <xref:System.Data.DataRow>tipo Oracle NUMBER para um tipo de framework .NET válido antes de armazenar o valor em um . Você pode <xref:System.Data.Common.DataAdapter.FillError> usar o evento para determinar se ocorreu uma **Exceção de Transbordamento.** Para obter mais <xref:System.Data.Common.DataAdapter.FillError> informações sobre o evento, consulte [Handling DataAdapter Events](handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Confira também

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [Comandos e Parâmetros](commands-and-parameters.md)
- [Recuperando informações de esquema de banco de dados](retrieving-database-schema-information.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
