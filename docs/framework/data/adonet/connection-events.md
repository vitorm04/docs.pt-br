---
title: Eventos de conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: e958c96e304962dace72e90b9266b57943f01ac9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785740"
---
# <a name="connection-events"></a>Eventos de conexão
Todos os provedores de dados de .NET Framework têm objetos de **conexão** com dois eventos que você pode usar para recuperar mensagens informativas de uma fonte de dados ou para determinar se o estado de uma **conexão** foi alterado. A tabela a seguir descreve os eventos do objeto de **conexão** .  
  
|evento|Descrição|  
|-----------|-----------------|  
|**InfoMessage**|Ocorre quando uma mensagem informativa é retornada de uma fonte de dados. As mensagens informativas são as mensagens de uma fonte de dados que não resultam em uma exceção sendo lançada.|  
|**StateChange**|Ocorre quando o estado da **conexão** é alterado.|  
  
## <a name="working-with-the-infomessage-event"></a>Trabalhando com o evento InfoMessage  
 Você pode recuperar avisos e mensagens informativas de uma fonte de dados do SQL Server usando o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> do objeto <xref:System.Data.SqlClient.SqlConnection>. Os erros retornados da fonte de dados com um nível de severidade de 11 a 16 geram uma exceção. No entanto, o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> pode ser usado para obter as mensagens da fonte de dados que não estão associadas a um erro. No caso do Microsoft SQL Server, qualquer erro com uma severidade de 10 ou menos é considerado uma mensagem informativa e podem ser capturado usando o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>. Para obter mais informações, consulte o artigo [mecanismo de banco de dados severidades de erro](/sql/relational-databases/errors-events/database-engine-error-severities) .
  
 O <xref:System.Data.SqlClient.SqlConnection.InfoMessage> evento recebe um <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objeto contendo, em sua propriedade **Errors** , uma coleção das mensagens da fonte de dados. Você pode consultar os objetos de **erro** nesta coleção para obter o número do erro e o texto da mensagem, bem como a origem do erro. O provedor de dados .NET Framework para SQL Server também inclui detalhes sobre o banco de dados, o procedimento armazenado e o número da linha da qual a mensagem veio.  
  
### <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como adicionar um manipulador de eventos para o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a>Tratando erros como InfoMessages  
 O evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> acionará normalmente apenas para mensagens informativas e de aviso que são enviadas do servidor. No entanto, quando ocorre um erro real, a execução do método **ExecuteNonQuery** ou **ExecuteReader** que iniciou a operação do servidor é interrompida e uma exceção é lançada.  
  
 Se você quiser continuar a processar o restante das instruções em um comando independentemente de qualquer erro gerado pelo servidor, defina a propriedade <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> do <xref:System.Data.SqlClient.SqlConnection> como `true`. Isso faz a conexão acionar o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> para erros em vez de gerar uma exceção e interromper o processamento. O aplicativo cliente pode, em seguida, manipular esse evento e responder às condições de erro.  
  
> [!NOTE]
> Um erro com um nível de severidade de 17 ou acima disso faz o servidor parar de processar o comando e deve ser tratado como uma exceção. Nesse caso, uma exceção é gerada independentemente de como o erro é tratado no evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.  
  
## <a name="working-with-the-statechange-event"></a>Trabalhando com o evento StateChange  
 O evento **StateChange** ocorre quando o estado de uma **conexão** é alterado. O evento **StateChange** recebe <xref:System.Data.StateChangeEventArgs> que permite que você determine a alteração no estado da **conexão** usando as propriedades **OriginalState** e **CurrentState** . A propriedade **OriginalState** é uma <xref:System.Data.ConnectionState> enumeração que indica o estado da **conexão** antes de ela ser alterada. **CurrentState** é uma <xref:System.Data.ConnectionState> enumeração que indica o estado da **conexão** após sua alteração.  
  
 O exemplo de código a seguir usa o evento **StateChange** para gravar uma mensagem no console quando o estado da **conexão** é alterado.  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Conectando a uma fonte de dados](connecting-to-a-data-source.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
