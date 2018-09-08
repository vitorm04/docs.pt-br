---
title: Eventos de conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: c1ef9ff9cc4d77e4951e99ed74c96cf78eb71506
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139834"
---
# <a name="connection-events"></a>Eventos de conexão
Todos os provedores de dados .NET Framework possuem **Conexão** objetos com dois eventos que você pode usar para recuperar mensagens informativas de uma fonte de dados ou para determinar se o estado de uma **Conexão** tem alterado. A tabela a seguir descreve os eventos do **Conexão** objeto.  
  
|evento|Descrição|  
|-----------|-----------------|  
|**InfoMessage**|Ocorre quando uma mensagem informativa é retornada de uma fonte de dados. As mensagens informativas são as mensagens de uma fonte de dados que não resultam em uma exceção sendo lançada.|  
|**StateChange**|Ocorre quando o estado do **Conexão** alterações.|  
  
## <a name="working-with-the-infomessage-event"></a>Trabalhando com o evento InfoMessage  
 Você pode recuperar avisos e mensagens informativas de uma fonte de dados do SQL Server usando o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> do objeto <xref:System.Data.SqlClient.SqlConnection>. Os erros retornados da fonte de dados com um nível de severidade de 11 a 16 geram uma exceção. No entanto, o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> pode ser usado para obter as mensagens da fonte de dados que não estão associadas a um erro. No caso do Microsoft SQL Server, qualquer erro com uma severidade de 10 ou menos é considerado uma mensagem informativa e podem ser capturado usando o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>. Para obter mais informações, consulte o [severidade de erro de mecanismo de banco de dados](/sql/relational-databases/errors-events/database-engine-error-severities) artigo.
  
 O <xref:System.Data.SqlClient.SqlConnection.InfoMessage> evento recebe um <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objeto que contém, em seus **erros** propriedade, uma coleção das mensagens da fonte de dados. Você pode consultar a **erro** objetos nesta coleção para o texto de número e a mensagem de erro, bem como a origem do erro. O provedor de dados .NET Framework para SQL Server também inclui detalhes sobre o banco de dados, o procedimento armazenado e o número da linha da qual a mensagem veio.  
  
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
 O evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> acionará normalmente apenas para mensagens informativas e de aviso que são enviadas do servidor. No entanto, quando ocorre um erro real, a execução do **ExecuteNonQuery** ou **ExecuteReader** método que iniciou a operação do servidor é interrompido e uma exceção será lançada.  
  
 Se você quiser continuar a processar o restante das instruções em um comando independentemente de qualquer erro gerado pelo servidor, defina a propriedade <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> do <xref:System.Data.SqlClient.SqlConnection> como `true`. Isso faz a conexão acionar o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> para erros em vez de gerar uma exceção e interromper o processamento. O aplicativo cliente pode, em seguida, manipular esse evento e responder às condições de erro.  
  
> [!NOTE]
>  Um erro com um nível de severidade de 17 ou acima disso faz o servidor parar de processar o comando e deve ser tratado como uma exceção. Nesse caso, uma exceção é gerada independentemente de como o erro é tratado no evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.  
  
## <a name="working-with-the-statechange-event"></a>Trabalhando com o evento StateChange  
 O **StateChange** evento ocorre quando o estado de uma **Conexão** alterações. O **StateChange** evento recebe <xref:System.Data.StateChangeEventArgs> que permitem que você determine a alteração no estado dos **Conexão** usando o **OriginalState** e **CurrentState** propriedades. O **OriginalState** propriedade é um <xref:System.Data.ConnectionState> enumeração que indica o estado do **Conexão** antes que ele é alterado. **CurrentState** é um <xref:System.Data.ConnectionState> enumeração que indica o estado do **Conexão** depois que ele é alterado.  
  
 O seguinte exemplo de código usa o **StateChange** eventos para gravar uma mensagem no console quando o estado do **Conexão** alterações.  
  
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
 [Conectando a uma fonte de dados](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
