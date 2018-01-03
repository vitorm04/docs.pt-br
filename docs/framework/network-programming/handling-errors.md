---
title: Manipulando erros
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c7d9c08e38c2d82381c94e8813ef0312806bd010
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="handling-errors"></a><span data-ttu-id="bced7-102">Manipulando erros</span><span class="sxs-lookup"><span data-stu-id="bced7-102">Handling Errors</span></span>
<span data-ttu-id="bced7-103">As classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> geram exceções do sistema (como <xref:System.ArgumentException>) e exceções específicas à Web (que são <xref:System.Net.WebException> geradas pelo método <xref:System.Net.WebRequest.GetResponse%2A>).</span><span class="sxs-lookup"><span data-stu-id="bced7-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
 <span data-ttu-id="bced7-104">Cada **WebException** inclui uma propriedade <xref:System.Net.WebException.Status%2A> que contém um valor da enumeração <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="bced7-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="bced7-105">Examine a propriedade **Status** para determinar o erro ocorrido e execute as etapas apropriadas para resolver o erro.</span><span class="sxs-lookup"><span data-stu-id="bced7-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
 <span data-ttu-id="bced7-106">A tabela a seguir descreve os possíveis valores para a propriedade **Status**.</span><span class="sxs-lookup"><span data-stu-id="bced7-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="bced7-107">Status</span><span class="sxs-lookup"><span data-stu-id="bced7-107">Status</span></span>|<span data-ttu-id="bced7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="bced7-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="bced7-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-109">ConnectFailure</span></span>|<span data-ttu-id="bced7-110">O serviço remoto não pôde ser contatado no nível do transporte.</span><span class="sxs-lookup"><span data-stu-id="bced7-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="bced7-111">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="bced7-111">ConnectionClosed</span></span>|<span data-ttu-id="bced7-112">A conexão foi fechada prematuramente.</span><span class="sxs-lookup"><span data-stu-id="bced7-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="bced7-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-113">KeepAliveFailure</span></span>|<span data-ttu-id="bced7-114">O servidor fechou uma conexão estabelecida com o conjunto de cabeçalhos Keep-alive.</span><span class="sxs-lookup"><span data-stu-id="bced7-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="bced7-115">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-115">NameResolutionFailure</span></span>|<span data-ttu-id="bced7-116">O serviço de nomes não pôde resolver o nome do host.</span><span class="sxs-lookup"><span data-stu-id="bced7-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="bced7-117">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="bced7-117">ProtocolError</span></span>|<span data-ttu-id="bced7-118">A resposta recebida do servidor estava completa, mas indicava um erro no nível do protocolo.</span><span class="sxs-lookup"><span data-stu-id="bced7-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="bced7-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-119">ReceiveFailure</span></span>|<span data-ttu-id="bced7-120">Não foi recebida uma resposta completa do servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="bced7-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="bced7-121">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="bced7-121">RequestCanceled</span></span>|<span data-ttu-id="bced7-122">A solicitação foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="bced7-122">The request was canceled.</span></span>|  
|<span data-ttu-id="bced7-123">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-123">SecureChannelFailure</span></span>|<span data-ttu-id="bced7-124">Ocorreu um erro em um link de canal seguro.</span><span class="sxs-lookup"><span data-stu-id="bced7-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="bced7-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-125">SendFailure</span></span>|<span data-ttu-id="bced7-126">Não foi possível enviar uma solicitação completa para o servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="bced7-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="bced7-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="bced7-127">ServerProtocolViolation</span></span>|<span data-ttu-id="bced7-128">A resposta do servidor não era uma resposta HTTP válida.</span><span class="sxs-lookup"><span data-stu-id="bced7-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="bced7-129">Êxito</span><span class="sxs-lookup"><span data-stu-id="bced7-129">Success</span></span>|<span data-ttu-id="bced7-130">Nenhum erro foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="bced7-130">No error was encountered.</span></span>|  
|<span data-ttu-id="bced7-131">Tempo limite</span><span class="sxs-lookup"><span data-stu-id="bced7-131">Timeout</span></span>|<span data-ttu-id="bced7-132">Nenhuma resposta foi recebida no tempo limite definido para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="bced7-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="bced7-133">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-133">TrustFailure</span></span>|<span data-ttu-id="bced7-134">Não foi possível validar um certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="bced7-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="bced7-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="bced7-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="bced7-136">Foi recebida uma mensagem que ultrapassa o limite especificado ao enviar uma solicitação ou receber uma resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="bced7-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="bced7-137">Pendente</span><span class="sxs-lookup"><span data-stu-id="bced7-137">Pending</span></span>|<span data-ttu-id="bced7-138">Uma solicitação assíncrona interna está pendente.</span><span class="sxs-lookup"><span data-stu-id="bced7-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="bced7-139">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-139">PipelineFailure</span></span>|<span data-ttu-id="bced7-140">Esse valor dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no código.</span><span class="sxs-lookup"><span data-stu-id="bced7-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="bced7-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="bced7-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="bced7-142">O serviço de resolvedor de nome não pôde resolver o nome de host do proxy.</span><span class="sxs-lookup"><span data-stu-id="bced7-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="bced7-143">UnknownError</span><span class="sxs-lookup"><span data-stu-id="bced7-143">UnknownError</span></span>|<span data-ttu-id="bced7-144">Ocorreu uma exceção de tipo desconhecido.</span><span class="sxs-lookup"><span data-stu-id="bced7-144">An exception of unknown type has occurred.</span></span>|  
  
 <span data-ttu-id="bced7-145">Quando a propriedade **Status** é **WebExceptionStatus.ProtocolError**, uma **WebResponse** que contém a resposta do servidor está disponível.</span><span class="sxs-lookup"><span data-stu-id="bced7-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="bced7-146">Examine essa resposta para determinar a origem real do erro de protocolo.</span><span class="sxs-lookup"><span data-stu-id="bced7-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
 <span data-ttu-id="bced7-147">O exemplo a seguir mostra como capturar uma **WebException**.</span><span class="sxs-lookup"><span data-stu-id="bced7-147">The following example shows how to catch a **WebException**.</span></span>  
  
```csharp  
try   
{  
    // Create a request instance.  
    WebRequest myRequest =   
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.   
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )   
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)   
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,   
    //   there has been a protocol error and a WebResponse   
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)   
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.   
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer      
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,   
    '   there has been a protocol error and a WebResponse   
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
 <span data-ttu-id="bced7-148">Os aplicativos que usam a classe <xref:System.Net.Sockets.Socket> geram <xref:System.Net.Sockets.SocketException> quando ocorrem erros no soquete do Windows.</span><span class="sxs-lookup"><span data-stu-id="bced7-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="bced7-149">As classes <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> e <xref:System.Net.Sockets.UdpClient> são criadas com base na classe **Socket** e geram **SocketExceptions** também.</span><span class="sxs-lookup"><span data-stu-id="bced7-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
 <span data-ttu-id="bced7-150">Quando uma **SocketException** é gerada, a classe **SocketException** define a propriedade <xref:System.Net.Sockets.SocketException.ErrorCode%2A> com o último erro de soquete do sistema operacional ocorrido.</span><span class="sxs-lookup"><span data-stu-id="bced7-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="bced7-151">Para obter mais informações sobre códigos de erro de soquete, consulte a documentação de códigos de erro da API do Winsock 2.0 no MSDN.</span><span class="sxs-lookup"><span data-stu-id="bced7-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bced7-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bced7-152">See Also</span></span>  
 [<span data-ttu-id="bced7-153">Fundamentos do tratamento de exceções</span><span class="sxs-lookup"><span data-stu-id="bced7-153">Exception Handling Fundamentals</span></span>](../../../docs/standard/exceptions/exception-handling-fundamentals.md)  
 [<span data-ttu-id="bced7-154">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="bced7-154">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
