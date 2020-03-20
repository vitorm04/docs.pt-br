---
title: Eventos de conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: a7ad0d4d950da71db0aebca872949fa82669c5c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151686"
---
# <a name="connection-events"></a><span data-ttu-id="a8ea4-102">Eventos de conexão</span><span class="sxs-lookup"><span data-stu-id="a8ea4-102">Connection Events</span></span>
<span data-ttu-id="a8ea4-103">Todos os provedores de dados .NET Framework têm objetos **de conexão** com dois eventos que você pode usar para recuperar mensagens informantes de uma fonte de dados ou para determinar se o estado de uma **conexão** foi alterado.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="a8ea4-104">A tabela a seguir descreve os eventos do objeto **Conexão.**</span><span class="sxs-lookup"><span data-stu-id="a8ea4-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="a8ea4-105">Evento</span><span class="sxs-lookup"><span data-stu-id="a8ea4-105">Event</span></span>|<span data-ttu-id="a8ea4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8ea4-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8ea4-107">**Infomessage**</span><span class="sxs-lookup"><span data-stu-id="a8ea4-107">**InfoMessage**</span></span>|<span data-ttu-id="a8ea4-108">Ocorre quando uma mensagem informativa é retornada de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="a8ea4-109">As mensagens informativas são as mensagens de uma fonte de dados que não resultam em uma exceção sendo lançada.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="a8ea4-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="a8ea4-110">**StateChange**</span></span>|<span data-ttu-id="a8ea4-111">Ocorre quando o estado da **conexão** muda.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="a8ea4-112">Trabalhando com o evento InfoMessage</span><span class="sxs-lookup"><span data-stu-id="a8ea4-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="a8ea4-113">Você pode recuperar avisos e mensagens informativas de uma fonte de dados do SQL Server usando o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> do objeto <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="a8ea4-114">Os erros retornados da fonte de dados com um nível de severidade de 11 a 16 geram uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="a8ea4-115">No entanto, o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> pode ser usado para obter as mensagens da fonte de dados que não estão associadas a um erro.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="a8ea4-116">No caso do Microsoft SQL Server, qualquer erro com uma severidade de 10 ou menos é considerado uma mensagem informativa e podem ser capturado usando o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="a8ea4-117">Para obter mais informações, consulte o artigo [Gravidades de erro do mecanismo de banco de](/sql/relational-databases/errors-events/database-engine-error-severities) dados.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="a8ea4-118">O <xref:System.Data.SqlClient.SqlConnection.InfoMessage> evento <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> recebe um objeto contendo, em sua propriedade **Erros,** uma coleta das mensagens da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="a8ea4-119">Você pode consultar os objetos **Erro** nesta coleção para o número de erro e o texto da mensagem, bem como a origem do erro.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="a8ea4-120">O provedor de dados .NET Framework para SQL Server também inclui detalhes sobre o banco de dados, o procedimento armazenado e o número da linha da qual a mensagem veio.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a8ea4-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8ea4-121">Example</span></span>  
 <span data-ttu-id="a8ea4-122">O exemplo de código a seguir mostra como adicionar um manipulador de eventos para o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="a8ea4-123">Tratando erros como InfoMessages</span><span class="sxs-lookup"><span data-stu-id="a8ea4-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="a8ea4-124">O evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> acionará normalmente apenas para mensagens informativas e de aviso que são enviadas do servidor.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="a8ea4-125">No entanto, quando ocorre um erro real, a execução do método **ExecuteNonQuery** ou **ExecuteReader** que iniciou a operação do servidor é interrompida e uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="a8ea4-126">Se você quiser continuar a processar o restante das instruções em um comando independentemente de qualquer erro gerado pelo servidor, defina a propriedade <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> do <xref:System.Data.SqlClient.SqlConnection> como `true`.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="a8ea4-127">Isso faz a conexão acionar o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> para erros em vez de gerar uma exceção e interromper o processamento.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="a8ea4-128">O aplicativo cliente pode, em seguida, manipular esse evento e responder às condições de erro.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8ea4-129">Um erro com um nível de severidade de 17 ou acima disso faz o servidor parar de processar o comando e deve ser tratado como uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="a8ea4-130">Nesse caso, uma exceção é gerada independentemente de como o erro é tratado no evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="a8ea4-131">Trabalhando com o evento StateChange</span><span class="sxs-lookup"><span data-stu-id="a8ea4-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="a8ea4-132">O evento **StateChange** ocorre quando o estado de uma **conexão** muda.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="a8ea4-133">O evento **StateChange** <xref:System.Data.StateChangeEventArgs> recebe o que permite determinar a alteração no estado da **conexão** usando as propriedades **OriginalState** e **CurrentState.**</span><span class="sxs-lookup"><span data-stu-id="a8ea4-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="a8ea4-134">A propriedade **OriginalState** é uma <xref:System.Data.ConnectionState> enumeração que indica o estado da **Conexão** antes de ser alterada.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="a8ea4-135">**CurrentState** é <xref:System.Data.ConnectionState> uma enumeração que indica o estado da **Conexão** depois que ela mudou.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="a8ea4-136">O exemplo de código a seguir usa o evento **StateChange** para escrever uma mensagem no console quando o estado da **conexão for** alterado.</span><span class="sxs-lookup"><span data-stu-id="a8ea4-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8ea4-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8ea4-137">See also</span></span>

- [<span data-ttu-id="a8ea4-138">Conectando a uma Fonte de Dados</span><span class="sxs-lookup"><span data-stu-id="a8ea4-138">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="a8ea4-139">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8ea4-139">ADO.NET Overview</span></span>](ado-net-overview.md)
