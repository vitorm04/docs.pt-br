---
title: Estatísticas do provedor para SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: d52c6bfdadf0a53ac4c5f62c37f1056c6702a82c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46706418"
---
# <a name="provider-statistics-for-sql-server"></a>Estatísticas do provedor para SQL Server
A partir da versão 2.0 do .NET Framework, o provedor de dados do .NET Framework para SQL Server dá suporte a estatísticas de tempo de execução. Você deve habilitar estatísticas definindo a propriedade <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> do objeto de <xref:System.Data.SqlClient.SqlConnection> para `True` depois de criar um objeto de conexão válido. Depois que as estatísticas forem habilitadas, você poderá examiná-las como um "instantâneo no tempo" recuperando uma referência do <xref:System.Collections.IDictionary> pelo método <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> do objeto <xref:System.Data.SqlClient.SqlConnection>. Enumere por meio da lista como um conjunto de entradas no dicionário de pares de nome/valor. Esses pares de nome/valor não são ordenados. A qualquer momento, você pode chamar o método <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> do objeto <xref:System.Data.SqlClient.SqlConnection> para redefinir os contadores. Se a coleta de estatísticas não estiver habilitada, uma exceção não será gerada. Além disso, se <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> for chamado sem <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> ter sido chamado primeiro, os valores recuperados serão os valores iniciais para cada entrada. Se você habilitar estatísticas, execute o aplicativo por um tempo e, em seguida, desabilite as estatísticas. Os valores recuperados refletirão os valores coletados até o ponto em que as estatísticas foram desabilitadas. Todos os valores estatísticos são coletados a cada conexão.  
  
## <a name="statistical-values-available"></a>Valores estatísticos disponíveis  
 No momento, há 18 itens diferentes disponíveis do provedor do Microsoft SQL Server. O número de itens disponíveis pode ser acessado por meio de **contagem** propriedade da <xref:System.Collections.IDictionary> referência retornada pela interface <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Todos os contadores para estatísticas do provedor usam o common language runtime <xref:System.Int64> tipo (**longo** em c# e Visual Basic), que é de 64 bits de largura. O valor máximo do **int64** tipo de dados, conforme definido pelo **int64. MaxValue** campo, ((2^63)-1)). Quando os valores para os contadores atingirem esse valor máximo, eles não deverão ser considerados precisos. Isso significa que **int64. MaxValue**-1((2^63)-2) é efetivamente o maior valor válido para qualquer estatística.  
  
> [!NOTE]
>  Um dicionário é usado retornar estatísticas do provedor porque o número, os nomes e a ordem das estatísticas retornadas podem ser alteradas no futuro. Os aplicativos não devem confiar em um valor específico localizado no dicionário, mas devem verificar se o valor está lá e está ramificado adequadamente.  
  
 A tabela a seguir descreve os valores estatísticos atuais disponíveis. Observe que os nomes de chave para os valores individuais não são localizados em versões regionais do Microsoft .NET Framework.  
  
|Nome da chave|Descrição|  
|--------------|-----------------|  
|`BuffersReceived`|Retorna o número de pacotes de protocolo TDS recebidos pelo provedor do SQL Server depois que o aplicativo tiver começado a usar o provedor e tiver habilitado estatísticas.|  
|`BuffersSent`|Retorna o número de pacotes de protocolo TDS enviados para o SQL Server pelo provedor depois que as estatísticas tiverem sido habilitadas. Os comandos grandes podem exigir vários buffers. Por exemplo, se um comando grande for enviado para o servidor e exigir seis pacotes, o `ServerRoundtrips` será incrementado em um e `BuffersSent` será incrementado em seis.|  
|`BytesReceived`|Retorna o número de bytes de dados nos pacotes do protocolo TDS recebidos pelo provedor do SQL Server assim que o aplicativo tiver começado a usar o provedor e tiver habilitado estatísticas.|  
|`BytesSent`|Retorna o número de bytes de dados enviados para o SQL Server nos pacotes do protocolo TDS depois que o aplicativo tiver começado a usar o provedor e tiver habilitado estatísticas.|  
|`ConnectionTime`|A quantidade de tempo (em milissegundos) que a conexão foi aberta depois que as estatísticas foram habilitadas (tempo total de conexão se as estatísticas foram habilitadas antes de abrir a conexão).|  
|`CursorOpens`|Retorna o número de vezes que um cursor foi aberto pela conexão depois que o aplicativo começou a usar o provedor e habilitou estatísticas.<br /><br /> Observe que os resultados somente leitura/somente encaminhamento retornados pelas instruções SELECT não são considerados cursores e, portanto, não afetam esse contador.|  
|`ExecutionTime`|Retorna a quantidade de tempo cumulativo (em milissegundos) que o provedor gastou processando assim que as estatísticas foram habilitadas, incluindo o tempo gasto esperando respostas do servidor bem como o tempo gasto na execução do código no próprio provedor.<br /><br /> As classes que incluem o código de tempo são:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Para manter membros de desempenho crítico o menor possível, os seguintes membros não serão cronometrados:<br /><br /> SqlDataReader<br /><br /> this[] operator (all overloads)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Retorna o número total de instruções INSERT, DELETE e UPDATE executadas pela conexão depois que o aplicativo começou a usar o provedor e habilitou estatísticas.|  
|`IduRows`|Retorna o número total de linhas afetadas por instruções INSERT, DELETE e UPDATE executadas pela conexão depois que o aplicativo começou a usar o provedor e habilitou estatísticas.|  
|`NetworkServerTime`|Retorna a quantidade de tempo cumulativo (em milissegundos) que o provedor gastou esperando respostas do servidor depois do aplicativo começou a usar o provedor e habilitou estatísticas.|  
|`PreparedExecs`|Retorna o número de comandos preparados executados pela conexão depois que o aplicativo começou a usar o provedor e habilitou estatísticas.|  
|`Prepares`|Retorna o número de instruções preparadas pela conexão depois que o aplicativo começou a usar o provedor e habilitou estatísticas.|  
|`SelectCount`|Retorna o número de instruções SELECT executadas pela conexão depois que o aplicativo começou a usar o provedor e habilitou estatísticas. Isso inclui instruções FETCH para recuperar linhas de cursores e a contagem para instruções SELECT é atualizada quando o término de um <xref:System.Data.SqlClient.SqlDataReader> é atingido.|  
|`SelectRows`|Retorna o número de linhas selecionadas depois que o aplicativo começou a usar o provedor e habilitou estatísticas. Esse contador reflete todas as linhas geradas por instruções SQL, até mesmo aquelas que não foram realmente consumidas pelo chamador. Por exemplo, fechar um leitor de dados antes de ler todo o conjunto de resultados não afetaria a contagem. Isso inclui as linhas recuperadas dos cursores pelas instruções FETCH.|  
|`ServerRoundtrips`|Retorna o número de vezes que a conexão enviou comandos para o servidor e obteve uma resposta depois que o aplicativo começou a usar o provedor e habilitou estatísticas.|  
|`SumResultSets`|Retorna o número de conjuntos de resultados que foram usados depois que o aplicativo começou a usar o provedor e habilitou estatísticas. Por exemplo, isso inclui qualquer conjunto de resultados retornado para o cliente. Para cursores, cada operação de fetch ou block-fetch é considerada um conjunto de resultados independente.|  
|`Transactions`|Retorna o número de transações de usuário iniciadas depois que o aplicativo começou a usar o provedor e habilitou estatísticas, incluindo rollbacks. Se uma conexão está sendo executado com confirmação automática, cada comando é considerado uma transação.<br /><br /> Esse contador incrementa a contagem de transações assim que uma instrução BEGIN TRAN é executada, independentemente de a transação ser confirmada ou revertida posteriormente.|  
|`UnpreparedExecs`|Retorna o número de instruções não preparadas executadas pela conexão depois que o aplicativo começou a usar o provedor e habilitou estatísticas.|  
  
### <a name="retrieving-a-value"></a>Recuperando um valor  
 O aplicativo de console seguir mostra como habilitar estatísticas em uma conexão, recuperar quatro valores de estatística individual e gravá-los na janela do console.  
  
> [!NOTE]
>  O exemplo a seguir usa o exemplo **AdventureWorks** banco de dados incluído com o SQL Server. A cadeia de conexão fornecida no código de exemplo presume que o banco de dados esteja instalado e disponível no computador local. Modifique a cadeia de conexão conforme o necessário para seu ambiente.  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Recuperando todos os valores  
 O aplicativo de console seguir mostra como habilitar estatísticas em uma conexão, recuperar todos os valores de estatística disponíveis usando o enumerador, e gravá-los na janela do console.  
  
> [!NOTE]
>  O exemplo a seguir usa o exemplo **AdventureWorks** banco de dados incluído com o SQL Server. A cadeia de conexão fornecida no código de exemplo presume que o banco de dados esteja instalado e disponível no computador local. Modifique a cadeia de conexão conforme o necessário para seu ambiente.  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server and ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
