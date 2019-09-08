---
title: Integração de System.Transactions com o SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 075eea42c65a822fc46ca14f820599567c35d231
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791372"
---
# <a name="systemtransactions-integration-with-sql-server"></a>Integração de System.Transactions com o SQL Server
O .NET Framework versão 2,0 introduziu uma estrutura de transação que pode ser acessada por meio do <xref:System.Transactions> namespace. Essa estrutura expõe transações de uma maneira totalmente integrada no .NET Framework, incluindo ADO.NET.  
  
 Além dos aprimoramentos de programação, <xref:System.Transactions> e o ADO.net pode trabalhar em conjunto para coordenar otimizações quando você trabalha com transações. Uma transação promocionaltable é uma transação leve (local) que pode ser promovida automaticamente para uma transação totalmente distribuída conforme necessário.  
  
 A partir do ADO.NET 2,0 <xref:System.Data.SqlClient> , o oferece suporte a transações de promoção quando você trabalha com SQL Server. Uma transação passível de promoção não chama a sobrecarga adicional de uma transação distribuída a menos que a sobrecarga adicional seja necessária. As transações de promoçãotable são automáticas e não exigem nenhuma intervenção do desenvolvedor.  
  
 As transações de promoçãotable só estão disponíveis quando você usa o .NET Framework provedor de dados para`SqlClient`SQL Server () com SQL Server.  
  
## <a name="creating-promotable-transactions"></a>Criando transações de promotable  
 O provedor de .NET Framework para SQL Server fornece suporte para transações de promoção, que são manipuladas por meio das classes <xref:System.Transactions> no namespace .NET Framework. As transações da promotable otimizam as transações distribuídas por meio da criação de uma transação distribuída até que seja necessária. Se apenas um Gerenciador de recursos for necessário, nenhuma transação distribuída ocorrerá.  
  
> [!NOTE]
> Em um cenário parcialmente confiável, o <xref:System.Transactions.DistributedTransactionPermission> é necessário quando uma transação é promovida para uma transação distribuída.  
  
## <a name="promotable-transaction-scenarios"></a>Cenários de transação de promoção  
 As transações distribuídas normalmente consomem recursos significativos do sistema, sendo gerenciados pelo Microsoft Coordenador de Transações Distribuídas (MS DTC), que integra todos os gerenciadores de recursos acessados na transação. Uma transação promocionaltable é uma forma especial de uma <xref:System.Transactions> transação que delega efetivamente o trabalho a uma transação SQL Server simples. <xref:System.Transactions>, <xref:System.Data.SqlClient>e SQL Server coordenar o trabalho envolvido na manipulação da transação, promovê-la para uma transação distribuída completa, conforme necessário.  
  
 O benefício de usar transações de promoção é que, quando uma conexão é aberta usando uma transação <xref:System.Transactions.TransactionScope> ativa, e não há nenhuma outra conexão aberta, a transação é confirmada como uma transação leve, em vez de incorrer o adicional sobrecarga de uma transação distribuída completa.  
  
### <a name="connection-string-keywords"></a>Palavras-chave da cadeia de conexão  
 A <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Propriedade dá suporte a uma `Enlist`palavra-chave, <xref:System.Data.SqlClient> , que indica se o detectará contextos transacionais e inscreverá automaticamente a conexão em uma transação distribuída. Se `Enlist=true`, a conexão será inscrito automaticamente no contexto de transação atual do thread de abertura. Se `Enlist=false`, a `SqlClient` conexão não interagirá com uma transação distribuída. O valor padrão para `Enlist` é true. Se `Enlist` não for especificado na cadeia de conexão, a conexão será inscrito automaticamente em uma transação distribuída se uma for detectada quando a conexão for aberta.  
  
 As `Transaction Binding` palavras-chave em uma <xref:System.Data.SqlClient.SqlConnection> cadeia de conexão controlam a associação da conexão `System.Transactions` com uma transação enlistada. Ele também está disponível por meio <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> da propriedade de <xref:System.Data.SqlClient.SqlConnectionStringBuilder>a.  
  
 A tabela a seguir descreve os valores possíveis.  
  
|Palavra-chave|Descrição|  
|-------------|-----------------|  
|Desassociar implícito|O padrão. A conexão é desanexada da transação quando termina, voltando para o modo de confirmação automática.|  
|Desassociar explícito|A conexão permanece anexada à transação até que a transação seja fechada. A conexão falhará se a transação associada não estiver ativa ou não corresponder <xref:System.Transactions.Transaction.Current%2A>.|  
  
## <a name="using-transactionscope"></a>Usando TransactionScope  
 A <xref:System.Transactions.TransactionScope> classe torna um bloco de código transacional, informando implicitamente as conexões em uma transação distribuída. Você deve chamar o <xref:System.Transactions.TransactionScope.Complete%2A> método no final <xref:System.Transactions.TransactionScope> do bloco antes de deixá-lo. Deixar o bloco invoca o <xref:System.Transactions.TransactionScope.Dispose%2A> método. Se uma exceção tiver sido gerada que faz com que o código deixe o escopo, a transação será considerada anulada.  
  
 É recomendável que você use `using` um bloco para certificar- <xref:System.Transactions.TransactionScope.Dispose%2A> se de que é <xref:System.Transactions.TransactionScope> chamado no objeto quando o bloco Using é encerrado. A falha na confirmação ou reversão de transações pendentes pode danificar significativamente o desempenho porque o tempo limite <xref:System.Transactions.TransactionScope> padrão para o é de um minuto. Se `using` você não usar uma instrução, deverá executar todo o trabalho em um `Try` bloco e `Finally` chamar explicitamente o <xref:System.Transactions.TransactionScope.Dispose%2A> método no bloco.  
  
 Se ocorrer uma exceção no <xref:System.Transactions.TransactionScope>, a transação será marcada como inconsistente e abandonada. Ele será revertido quando o <xref:System.Transactions.TransactionScope> for descartado. Se nenhuma exceção ocorrer, as transações participantes são confirmadas.  
  
> [!NOTE]
> A `TransactionScope` classe cria uma transação com um <xref:System.Transactions.Transaction.IsolationLevel%2A> de `Serializable` por padrão. Dependendo do seu aplicativo, convém considerar reduzir o nível de isolamento para evitar uma alta contenção em seu aplicativo.  
  
> [!NOTE]
> É recomendável que você execute apenas atualizações, inserções e exclusões em transações distribuídas, pois elas consomem recursos de banco de dados significativos. As instruções SELECT podem bloquear os recursos do banco de dados desnecessariamente e, em alguns cenários, talvez seja necessário usar transações para seleções. Qualquer trabalho que não seja de banco de dados deve ser feito fora do escopo da transação, a menos que envolva outros gerenciadores de recursos transacionados. Embora uma exceção no escopo da transação impeça que a transação seja confirmada, a <xref:System.Transactions.TransactionScope> classe não tem provisão para reverter as alterações que seu código fez fora do escopo da própria transação. Se você precisar executar alguma ação quando a transação for revertida, deverá escrever sua própria implementação da <xref:System.Transactions.IEnlistmentNotification> interface e inscrever-se explicitamente na transação.  
  
## <a name="example"></a>Exemplo  
 Trabalhar com <xref:System.Transactions> o requer que você tenha uma referência a System. Transactions. dll.  
  
 A função a seguir demonstra como criar uma transação promocionaltable em duas instâncias de SQL Server diferentes, representadas por <xref:System.Data.SqlClient.SqlConnection> dois objetos diferentes, que são encapsuladas em um <xref:System.Transactions.TransactionScope> bloco. O código cria o <xref:System.Transactions.TransactionScope> bloco com uma `using` instrução e abre a primeira conexão, que a <xref:System.Transactions.TransactionScope>lista automaticamente no. A transação é inicialmente listada como uma transação leve, não uma transação distribuída completa. A segunda conexão será listada <xref:System.Transactions.TransactionScope> somente se o comando na primeira conexão não lançar uma exceção. Quando a segunda conexão é aberta, a transação é promovida automaticamente para uma transação distribuída completa. O <xref:System.Transactions.TransactionScope.Complete%2A> método é invocado, que confirma a transação somente se nenhuma exceção tiver sido gerada. Se uma exceção tiver sido lançada em <xref:System.Transactions.TransactionScope> qualquer ponto do bloco, `Complete` não será chamada, e a transação distribuída será revertida quando o <xref:System.Transactions.TransactionScope> for descartado no final de seu `using` bloco.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Transações e simultaneidade](transactions-and-concurrency.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
