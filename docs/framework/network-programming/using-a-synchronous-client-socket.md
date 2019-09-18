---
title: Usando um soquete de cliente síncrono
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: fdecd18dc5975cd469e49de0eb0b55081e738cd8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047069"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="0a8d1-102">Usando um soquete de cliente síncrono</span><span class="sxs-lookup"><span data-stu-id="0a8d1-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="0a8d1-103">Um soquete de cliente síncrona suspende o programa de aplicativo enquanto a operação de rede é concluída.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="0a8d1-104">Soquetes síncronos não são adequados para aplicativos que fazem uso intenso da rede para sua operação, mas podem permitir o acesso simples aos serviços de rede para outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="0a8d1-105">Para enviar dados, passe uma matriz de bytes para um dos métodos de envio de dados da classe <xref:System.Net.Sockets.Socket> (<xref:System.Net.Sockets.Socket.Send%2A> e <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="0a8d1-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="0a8d1-106">O exemplo a seguir codifica uma cadeia de caracteres em um buffer de matriz de bytes usando a propriedade <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> e, em seguida, transmite o buffer para o dispositivo de rede usando o método **Send**.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="0a8d1-107">O método **Send** retorna o número de bytes enviados para o dispositivo de rede.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="0a8d1-108">O método **Send** remove os bytes do buffer e coloca-os na fila com o adaptador de rede a ser enviado para o dispositivo de rede.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="0a8d1-109">O adaptador de rede pode não enviar os dados imediatamente, mas ele os enviará no final, desde que a conexão seja fechada normalmente com o método <xref:System.Net.Sockets.Socket.Shutdown%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="0a8d1-110">Para receber dados de um dispositivo de rede, passe um buffer para um dos métodos de recebimento de dados da classe **Socket** (<xref:System.Net.Sockets.Socket.Receive%2A> e <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span><span class="sxs-lookup"><span data-stu-id="0a8d1-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="0a8d1-111">Os soquetes síncronos suspenderão o aplicativo até que os bytes sejam recebidos da rede ou até que o soquete seja fechado.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="0a8d1-112">O exemplo a seguir recebe dados da rede e, em seguida, exibe-o no console.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="0a8d1-113">O exemplo supõe que os dados provenientes da rede são um texto codificado em ASCII.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="0a8d1-114">O método **Receive** retorna o número de bytes recebidos da rede.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 <span data-ttu-id="0a8d1-115">Quando o soquete não for mais necessário, você precisará liberá-lo chamando o método <xref:System.Net.Sockets.Socket.Shutdown%2A> e, em seguida, chamando o método **Close**.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="0a8d1-116">O exemplo a seguir libera um **Socket**.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="0a8d1-117">A enumeração <xref:System.Net.Sockets.SocketShutdown> define constantes que indicam se o soquete deve ser fechado para envio, recebimento ou para ambos.</span><span class="sxs-lookup"><span data-stu-id="0a8d1-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a8d1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a8d1-118">See also</span></span>

- [<span data-ttu-id="0a8d1-119">Usando um soquete de cliente assíncrono</span><span class="sxs-lookup"><span data-stu-id="0a8d1-119">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="0a8d1-120">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="0a8d1-120">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="0a8d1-121">Exemplo de soquete de cliente síncrono</span><span class="sxs-lookup"><span data-stu-id="0a8d1-121">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
