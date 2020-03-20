---
title: Integração de System.Transactions com o SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 42007dafbdc9f61b9fc0776e0aaa2987551b704a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174232"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integração de System.Transactions com o SQL Server
A versão 2.0 do .NET Framework introduziu uma <xref:System.Transactions> estrutura de transação que pode ser acessada através do namespace. Essa estrutura expõe as transações de forma totalmente integrada ao Quadro .NET, incluindo ADO.NET.  
  
 Além dos aprimoramentos de <xref:System.Transactions> programação, e ADO.NET podem trabalhar em conjunto para coordenar otimizações quando você trabalha com transações. Uma transação promovidada é uma transação leve (local) que pode ser automaticamente promovida para uma transação totalmente distribuída conforme necessário.  
  
 Começando com ADO.NET 2.0, <xref:System.Data.SqlClient> suporta transações promotáveis quando você trabalha com o SQL Server. Uma transação passível de promoção não chama a sobrecarga adicional de uma transação distribuída a menos que a sobrecarga adicional seja necessária. As transações promovidas são automáticas e não requerem nenhuma intervenção do desenvolvedor.  
  
 As transações promoviais só estão disponíveis quando você usa o`SqlClient`.NET Framework Data Provider for SQL Server ( ) com o SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Criando transações promotáveis  
 O .NET Framework Provider for SQL Server fornece suporte para transações promoviadas, <xref:System.Transactions> que são tratadas através das classes no namespace .NET Framework. As transações promovidas otimizam as transações distribuídas, adiando a criação de uma transação distribuída até que seja necessária. Se apenas um gerenciador de recursos for necessário, nenhuma transação distribuída ocorrerá.  
  
> [!NOTE]
> Em um cenário parcialmente <xref:System.Transactions.DistributedTransactionPermission> confiável, o é necessário quando uma transação é promovida a uma transação distribuída.  
  
## <a name="promotable-transaction-scenarios"></a>Cenários de transações promoviais  
 As transações distribuídas normalmente consomem recursos significativos do sistema, sendo gerenciadas pelo Microsoft Distributed Transaction Coordinator (MS DTC), que integra todos os gerenciadores de recursos acessados na transação. Uma transação promovidada é <xref:System.Transactions> uma forma especial de uma transação que efetivamente delega o trabalho a uma simples transação sql server. <xref:System.Transactions>, <xref:System.Data.SqlClient>e o SQL Server coordenam o trabalho envolvido na movimentação da transação, promovendo-a para uma transação distribuída completa, conforme necessário.  
  
 A vantagem de usar transações promoviais é que <xref:System.Transactions.TransactionScope> quando uma conexão é aberta usando uma transação ativa, e nenhuma outra conexão é aberta, a transação se compromete como uma transação leve, em vez de incorrer na sobrecarga adicional de uma transação distribuída completa.  
  
### <a name="connection-string-keywords"></a>Palavras-chave de cadeia de conexão  
 A <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> propriedade suporta uma `Enlist`palavra-chave, <xref:System.Data.SqlClient> que indica se detectará contextos transacionais e alistará automaticamente a conexão em uma transação distribuída. Se `Enlist=true`, a conexão é automaticamente alistada no contexto atual de transação do segmento de abertura. Se `Enlist=false`, `SqlClient` a conexão não interagir com uma transação distribuída. O valor `Enlist` padrão para é verdadeiro. Se `Enlist` não for especificado na seqüência de conexões, a conexão será automaticamente alistada em uma transação distribuída se for detectada quando a conexão for aberta.  
  
 As `Transaction Binding` palavras-chave <xref:System.Data.SqlClient.SqlConnection> em uma seqüência de conexões controlam a associação da conexão com uma `System.Transactions` transação alistada. Também está disponível <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> através <xref:System.Data.SqlClient.SqlConnectionStringBuilder>da propriedade de um .  
  
 A tabela a seguir descreve os valores possíveis.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|Desvincular implícita|O padrão. A conexão se desprende da transação quando termina, mudando de volta para o modo de confirmação automática.|  
|Desvincular explícito|A conexão permanece anexada à transação até que a transação seja encerrada. A conexão falhará se a transação <xref:System.Transactions.Transaction.Current%2A>associada não estiver ativa ou não corresponder .|  
  
## <a name="using-transactionscope"></a>Usando transactionscope  
 Uma classe <xref:System.Transactions.TransactionScope> torna um bloco de código transacional inscrevendo implicitamente conexões em uma transação distribuída. Você deve <xref:System.Transactions.TransactionScope.Complete%2A> chamar o método <xref:System.Transactions.TransactionScope> no final do bloco antes de deixá-lo. Sair do bloco <xref:System.Transactions.TransactionScope.Dispose%2A> invoca o método. Se uma exceção foi lançada que faz com que o código saia do escopo, a transação é considerada abortada.  
  
 Recomendamos que você `using` use um <xref:System.Transactions.TransactionScope.Dispose%2A> bloco para <xref:System.Transactions.TransactionScope> certificar-se de que é chamado no objeto quando o bloco de uso é saído. A falha em cometer ou reverter transações pendentes pode prejudicar significativamente o desempenho, porque o tempo de intervalo padrão para o <xref:System.Transactions.TransactionScope> é de um minuto. Se você não usar uma instrução `using`, deverá executar todo o trabalho em um bloco `Try` e chamar explicitamente o método <xref:System.Transactions.TransactionScope.Dispose%2A> no bloco `Finally`.  
  
 Se ocorrer uma <xref:System.Transactions.TransactionScope>exceção no , a transação é marcada como inconsistente e é abandonada. Será revertido quando <xref:System.Transactions.TransactionScope> o descarte for descartado. Se nenhuma exceção ocorrer, as transações participantes serão confirmadas.  
  
> [!NOTE]
> Por padrão, a classe `TransactionScope` cria uma transação com um <xref:System.Transactions.Transaction.IsolationLevel%2A> de `Serializable`. Dependendo do seu aplicativo, talvez você queira considerar abaixar o nível de isolamento para evitar uma contenção elevada em seu aplicativo.  
  
> [!NOTE]
> Recomendamos que você execute apenas atualizações, inserções e exclusões em transações distribuídas porque consomem recursos significativos do banco de dados. As instruções selecionadas podem bloquear os recursos do banco de dados desnecessariamente e, em alguns cenários, você pode ter que usar transações para seleções. Qualquer trabalho não-banco de dados deve ser feito fora do escopo da transação, a menos que envolva outros gestores de recursos transacionados. Embora uma exceção no escopo da transação impeça <xref:System.Transactions.TransactionScope> a transação de cometer, a classe não tem nenhuma provisão para reverter quaisquer alterações que seu código tenha feito fora do escopo da transação em si. Se você tiver que tomar alguma ação quando a transação for <xref:System.Transactions.IEnlistmentNotification> revertida, você deve escrever sua própria implementação da interface e se alistar explicitamente na transação.  
  
## <a name="example"></a>Exemplo  
 Trabalhar <xref:System.Transactions> com requer que você tenha uma referência ao System.Transactions.dll.  
  
 A função a seguir demonstra como criar uma transação promotora contra <xref:System.Data.SqlClient.SqlConnection> duas instâncias diferentes <xref:System.Transactions.TransactionScope> do SQL Server, representadas por dois objetos diferentes, que estão envoltos em um bloco. O código <xref:System.Transactions.TransactionScope> cria o `using` bloco com uma declaração e abre a <xref:System.Transactions.TransactionScope>primeira conexão, que o alista automaticamente no . A transação é inscrita inicialmente como uma transação lightweight, não uma transação distribuída completa. A segunda conexão é <xref:System.Transactions.TransactionScope> alistada no único se o comando na primeira conexão não lançar uma exceção. Quando a segunda conexão é aberta, a transação é automaticamente promovida para uma transação distribuída completa. O <xref:System.Transactions.TransactionScope.Complete%2A> método é invocado, que compromete a transação apenas se nenhuma exceção tiver sido lançada. Se uma exceção tiver sido <xref:System.Transactions.TransactionScope> lançada `Complete` em qualquer ponto do bloco, não será <xref:System.Transactions.TransactionScope> chamada, e a `using` transação distribuída será revirada quando a eliminação for descartada no final de seu bloco.  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2
                // only when there is a chance that the transaction can commit.
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2
                ' only when there is a chance that the transaction can commit.
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a>Confira também

- [Transações e simultaneidade](transactions-and-concurrency.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
