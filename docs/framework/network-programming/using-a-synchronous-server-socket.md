---
title: Usando um soquete de servidor síncrono
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
ms.openlocfilehash: 2a4fd2f903f96a14d4a256ea68240e942ccd59eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614270"
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="fe31d-102">Usando um soquete de servidor síncrono</span><span class="sxs-lookup"><span data-stu-id="fe31d-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="fe31d-103">Os soquetes de servidor síncrono suspendem a execução do aplicativo até que uma solicitação de conexão seja recebida no soquete.</span><span class="sxs-lookup"><span data-stu-id="fe31d-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="fe31d-104">Os soquetes de servidor síncrono não são adequados para aplicativos que fazem uso intenso da rede em sua operação, mas podem ser adequados para aplicativos de rede simples.</span><span class="sxs-lookup"><span data-stu-id="fe31d-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="fe31d-105">Depois que um <xref:System.Net.Sockets.Socket> for definido para escutar em um ponto de extremidade usando os métodos <xref:System.Net.Sockets.Socket.Bind%2A> e <xref:System.Net.Sockets.Socket.Listen%2A>, ele estará pronto para aceitar solicitações de conexão de entrada usando o método <xref:System.Net.Sockets.Socket.Accept%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe31d-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="fe31d-106">O aplicativo é suspenso até que uma solicitação de conexão seja recebida quando o método **Accept** é chamado.</span><span class="sxs-lookup"><span data-stu-id="fe31d-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="fe31d-107">Quando uma solicitação de conexão é recebida, **Accept** retorna uma nova instância de **Socket** associada ao cliente que se conecta.</span><span class="sxs-lookup"><span data-stu-id="fe31d-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="fe31d-108">O exemplo a seguir lê os dados do cliente, exibe-os no console e retorna os dados ao cliente.</span><span class="sxs-lookup"><span data-stu-id="fe31d-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="fe31d-109">O **Socket** não especifica nenhum protocolo de mensagens e, portanto, a cadeia de caracteres “\<EOF>” marca o fim dos dados da mensagem.</span><span class="sxs-lookup"><span data-stu-id="fe31d-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="fe31d-110">Ele supõe que um **Socket** chamado `listener` foi inicializado e associado a um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fe31d-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe31d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe31d-111">See also</span></span>
- [<span data-ttu-id="fe31d-112">Usando um soquete de servidor assíncrono</span><span class="sxs-lookup"><span data-stu-id="fe31d-112">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="fe31d-113">Exemplo de soquete de servidor síncrono</span><span class="sxs-lookup"><span data-stu-id="fe31d-113">Synchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-server-socket-example.md)
- [<span data-ttu-id="fe31d-114">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="fe31d-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
