---
title: Eventos de conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: c1ef9ff9cc4d77e4951e99ed74c96cf78eb71506
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465519"
---
# <a name="connection-events"></a><span data-ttu-id="72a2e-102">Eventos de conexão</span><span class="sxs-lookup"><span data-stu-id="72a2e-102">Connection Events</span></span>
<span data-ttu-id="72a2e-103">Todos os provedores de dados .NET Framework possuem **Conexão** objetos com dois eventos que você pode usar para recuperar mensagens informativas de uma fonte de dados ou para determinar se o estado de uma **Conexão** tem alterado.</span><span class="sxs-lookup"><span data-stu-id="72a2e-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="72a2e-104">A tabela a seguir descreve os eventos do **Conexão** objeto.</span><span class="sxs-lookup"><span data-stu-id="72a2e-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="72a2e-105">evento</span><span class="sxs-lookup"><span data-stu-id="72a2e-105">Event</span></span>|<span data-ttu-id="72a2e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="72a2e-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="72a2e-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="72a2e-107">**InfoMessage**</span></span>|<span data-ttu-id="72a2e-108">Ocorre quando uma mensagem informativa é retornada de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="72a2e-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="72a2e-109">As mensagens informativas são as mensagens de uma fonte de dados que não resultam em uma exceção sendo lançada.</span><span class="sxs-lookup"><span data-stu-id="72a2e-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="72a2e-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="72a2e-110">**StateChange**</span></span>|<span data-ttu-id="72a2e-111">Ocorre quando o estado do **Conexão** alterações.</span><span class="sxs-lookup"><span data-stu-id="72a2e-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="72a2e-112">Trabalhando com o evento InfoMessage</span><span class="sxs-lookup"><span data-stu-id="72a2e-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="72a2e-113">Você pode recuperar avisos e mensagens informativas de uma fonte de dados do SQL Server usando o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> do objeto <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="72a2e-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="72a2e-114">Os erros retornados da fonte de dados com um nível de severidade de 11 a 16 geram uma exceção.</span><span class="sxs-lookup"><span data-stu-id="72a2e-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="72a2e-115">No entanto, o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> pode ser usado para obter as mensagens da fonte de dados que não estão associadas a um erro.</span><span class="sxs-lookup"><span data-stu-id="72a2e-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="72a2e-116">No caso do Microsoft SQL Server, qualquer erro com uma severidade de 10 ou menos é considerado uma mensagem informativa e podem ser capturado usando o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="72a2e-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="72a2e-117">Para obter mais informações, consulte o [severidade de erro de mecanismo de banco de dados](/sql/relational-databases/errors-events/database-engine-error-severities) artigo.</span><span class="sxs-lookup"><span data-stu-id="72a2e-117">For more information, see the [Database Engine Error Severities](/sql/relational-databases/errors-events/database-engine-error-severities) article.</span></span>
  
 <span data-ttu-id="72a2e-118">O <xref:System.Data.SqlClient.SqlConnection.InfoMessage> evento recebe um <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> objeto que contém, em seus **erros** propriedade, uma coleção das mensagens da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="72a2e-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="72a2e-119">Você pode consultar a **erro** objetos nesta coleção para o texto de número e a mensagem de erro, bem como a origem do erro.</span><span class="sxs-lookup"><span data-stu-id="72a2e-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="72a2e-120">O provedor de dados .NET Framework para SQL Server também inclui detalhes sobre o banco de dados, o procedimento armazenado e o número da linha da qual a mensagem veio.</span><span class="sxs-lookup"><span data-stu-id="72a2e-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="72a2e-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72a2e-121">Example</span></span>  
 <span data-ttu-id="72a2e-122">O exemplo de código a seguir mostra como adicionar um manipulador de eventos para o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="72a2e-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
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
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="72a2e-123">Tratando erros como InfoMessages</span><span class="sxs-lookup"><span data-stu-id="72a2e-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="72a2e-124">O evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> acionará normalmente apenas para mensagens informativas e de aviso que são enviadas do servidor.</span><span class="sxs-lookup"><span data-stu-id="72a2e-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="72a2e-125">No entanto, quando ocorre um erro real, a execução do **ExecuteNonQuery** ou **ExecuteReader** método que iniciou a operação do servidor é interrompido e uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="72a2e-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="72a2e-126">Se você quiser continuar a processar o restante das instruções em um comando independentemente de qualquer erro gerado pelo servidor, defina a propriedade <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> do <xref:System.Data.SqlClient.SqlConnection> como `true`.</span><span class="sxs-lookup"><span data-stu-id="72a2e-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="72a2e-127">Isso faz a conexão acionar o evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage> para erros em vez de gerar uma exceção e interromper o processamento.</span><span class="sxs-lookup"><span data-stu-id="72a2e-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="72a2e-128">O aplicativo cliente pode, em seguida, manipular esse evento e responder às condições de erro.</span><span class="sxs-lookup"><span data-stu-id="72a2e-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72a2e-129">Um erro com um nível de severidade de 17 ou acima disso faz o servidor parar de processar o comando e deve ser tratado como uma exceção.</span><span class="sxs-lookup"><span data-stu-id="72a2e-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="72a2e-130">Nesse caso, uma exceção é gerada independentemente de como o erro é tratado no evento <xref:System.Data.SqlClient.SqlConnection.InfoMessage>.</span><span class="sxs-lookup"><span data-stu-id="72a2e-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="72a2e-131">Trabalhando com o evento StateChange</span><span class="sxs-lookup"><span data-stu-id="72a2e-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="72a2e-132">O **StateChange** evento ocorre quando o estado de uma **Conexão** alterações.</span><span class="sxs-lookup"><span data-stu-id="72a2e-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="72a2e-133">O **StateChange** evento recebe <xref:System.Data.StateChangeEventArgs> que permitem que você determine a alteração no estado dos **Conexão** usando o **OriginalState** e **CurrentState** propriedades.</span><span class="sxs-lookup"><span data-stu-id="72a2e-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="72a2e-134">O **OriginalState** propriedade é um <xref:System.Data.ConnectionState> enumeração que indica o estado do **Conexão** antes que ele é alterado.</span><span class="sxs-lookup"><span data-stu-id="72a2e-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="72a2e-135">**CurrentState** é um <xref:System.Data.ConnectionState> enumeração que indica o estado do **Conexão** depois que ele é alterado.</span><span class="sxs-lookup"><span data-stu-id="72a2e-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="72a2e-136">O seguinte exemplo de código usa o **StateChange** eventos para gravar uma mensagem no console quando o estado do **Conexão** alterações.</span><span class="sxs-lookup"><span data-stu-id="72a2e-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72a2e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72a2e-137">See Also</span></span>  
 [<span data-ttu-id="72a2e-138">Conectando a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="72a2e-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="72a2e-139">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="72a2e-139">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
