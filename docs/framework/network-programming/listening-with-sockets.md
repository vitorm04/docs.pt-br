---
title: Escutando com soquetes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
ms.openlocfilehash: 2eb1174c98cdd88cc519559011659a2a277219b0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047778"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="f96a4-102">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="f96a4-102">Listening with Sockets</span></span>
<span data-ttu-id="f96a4-103">Soquetes de ouvinte ou de servidor abrem uma porta na rede e aguardam até que um cliente se conecte a essa porta.</span><span class="sxs-lookup"><span data-stu-id="f96a4-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="f96a4-104">Embora existam outros protocolos e famílias de endereços de rede, este exemplo mostra como criar um serviço remoto para uma rede TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="f96a4-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="f96a4-105">O endereço exclusivo de um serviço de TCP/IP é definido combinando-se o endereço IP do host com o número da porta do serviço para criar um ponto de extremidade para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f96a4-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="f96a4-106">A classe <xref:System.Net.Dns> fornece métodos que retornam informações sobre os endereços de rede com suporte pelo dispositivo de rede local.</span><span class="sxs-lookup"><span data-stu-id="f96a4-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="f96a4-107">Quando o dispositivo de rede local tem mais de um endereço de rede ou se o sistema local dá suporte a mais de um dispositivo de rede, a classe **Dns** retorna informações sobre todos os endereços de rede e o aplicativo deve escolher o endereço adequado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f96a4-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="f96a4-108">A IANA (Internet Assigned Numbers Authority) define os números da porta de serviços comuns. Para obter mais informações, consulte [Registro de número da porta do protocolo de transporte e nome de serviço](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="f96a4-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="f96a4-109">Outros serviços podem ter números de porta registrados no intervalo de 1.024 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="f96a4-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="f96a4-110">O exemplo a seguir cria um <xref:System.Net.IPEndPoint> para um servidor ao combinar o primeiro endereço IP retornado pelo **Dns** para o computador host com um número da porta escolhido dentre o intervalo de números da porta registrados.</span><span class="sxs-lookup"><span data-stu-id="f96a4-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="f96a4-111">Depois que o ponto de extremidade local é determinado, o <xref:System.Net.Sockets.Socket> deve ser associado a esse ponto de extremidade usando o método <xref:System.Net.Sockets.Socket.Bind%2A> e definido para escutar no ponto de extremidade usando o método <xref:System.Net.Sockets.Socket.Listen%2A>.</span><span class="sxs-lookup"><span data-stu-id="f96a4-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="f96a4-112">**Bind** lança uma exceção se a combinação específica de endereço e porta já está em uso.</span><span class="sxs-lookup"><span data-stu-id="f96a4-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="f96a4-113">O exemplo a seguir demonstra a associação de um **soquete** a um **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="f96a4-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp) 
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="f96a4-114">O método **Listen** usa um único parâmetro que especifica quantas conexões pendentes para o **soquete** são permitidas antes que um erro de servidor ocupado seja retornado para o cliente em processo de conexão.</span><span class="sxs-lookup"><span data-stu-id="f96a4-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="f96a4-115">Nesse caso, até 100 clientes são colocados na fila de conexão antes que uma resposta de servidor ocupado seja retornada ao cliente número 101.</span><span class="sxs-lookup"><span data-stu-id="f96a4-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f96a4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f96a4-116">See also</span></span>

- [<span data-ttu-id="f96a4-117">Usando um soquete de servidor síncrono</span><span class="sxs-lookup"><span data-stu-id="f96a4-117">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="f96a4-118">Usando um soquete de servidor assíncrono</span><span class="sxs-lookup"><span data-stu-id="f96a4-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="f96a4-119">Usando soquetes do cliente</span><span class="sxs-lookup"><span data-stu-id="f96a4-119">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="f96a4-120">Como: Criar um soquete</span><span class="sxs-lookup"><span data-stu-id="f96a4-120">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="f96a4-121">Soquetes</span><span class="sxs-lookup"><span data-stu-id="f96a4-121">Sockets</span></span>](sockets.md)
