---
title: Usando soquetes de cliente
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
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3df78be14da96d0bb7b8875a5c7532c003d1dbc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-client-sockets"></a><span data-ttu-id="f4d36-102">Usando soquetes de cliente</span><span class="sxs-lookup"><span data-stu-id="f4d36-102">Using Client Sockets</span></span>
<span data-ttu-id="f4d36-103">Antes de iniciar uma conversa por meio de um <xref:System.Net.Sockets.Socket>, crie um pipe de dados entre o aplicativo e o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="f4d36-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="f4d36-104">Embora existam outros protocolos e famílias de endereços de rede, este exemplo mostra como criar uma conexão TCP/IP com um serviço remoto.</span><span class="sxs-lookup"><span data-stu-id="f4d36-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="f4d36-105">O TCP/IP usa um endereço de rede e um número da porta de serviço para identificar um serviço exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="f4d36-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="f4d36-106">O endereço de rede identifica um dispositivo específico na rede; o número da porta identifica o serviço específico nesse dispositivo ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="f4d36-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="f4d36-107">A combinação do endereço de rede e da porta de serviço é chamada de um ponto de extremidade, que é representado no .NET Framework pela classe <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="f4d36-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="f4d36-108">Um descendente de **EndPoint** está definido para cada família de endereços com suporte; para a família de endereços IP, a classe é <xref:System.Net.IPEndPoint>.</span><span class="sxs-lookup"><span data-stu-id="f4d36-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="f4d36-109">A classe <xref:System.Net.Dns> fornece serviços de nome de domínio para aplicativos que usam os serviços TCP/IP da Internet.</span><span class="sxs-lookup"><span data-stu-id="f4d36-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="f4d36-110">O método <xref:System.Net.Dns.Resolve%2A> consulta um servidor DNS para mapear um nome de domínio amigável (como “host.contoso.com”) para um endereço numérico na Internet (por exemplo, 192.168.1.1).</span><span class="sxs-lookup"><span data-stu-id="f4d36-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="f4d36-111">**Resolve** retorna um <xref:System.Net.IPHostEntry> que contém uma lista de endereços e aliases para o nome solicitado.</span><span class="sxs-lookup"><span data-stu-id="f4d36-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="f4d36-112">Na maioria dos casos, é possível usar o primeiro endereço retornado na matriz <xref:System.Net.IPHostEntry.AddressList%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4d36-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="f4d36-113">O código a seguir obtém um <xref:System.Net.IPAddress> que contém o endereço IP do servidor host.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="f4d36-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="f4d36-114">A IANA (Internet Assigned Numbers Authority) define os números da porta de serviços comuns (para obter mais informações, consulte www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="f4d36-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="f4d36-115">Outros serviços podem ter números de porta registrados no intervalo de 1.024 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="f4d36-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="f4d36-116">O código a seguir combina o endereço IP de host.contoso.com com um número da porta para criar um ponto de extremidade remoto para uma conexão.</span><span class="sxs-lookup"><span data-stu-id="f4d36-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="f4d36-117">Depois de determinar o endereço do dispositivo remoto e escolher uma porta a ser usada para a conexão, o aplicativo pode tentar estabelecer uma conexão com o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="f4d36-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="f4d36-118">O exemplo a seguir usa um **IPEndPoint** existente para se conectar a um dispositivo remoto e captura todas as exceções geradas.</span><span class="sxs-lookup"><span data-stu-id="f4d36-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4d36-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4d36-119">See Also</span></span>  
 [<span data-ttu-id="f4d36-120">Usando um soquete do cliente síncrona</span><span class="sxs-lookup"><span data-stu-id="f4d36-120">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [<span data-ttu-id="f4d36-121">Usando um soquete do cliente assíncrono</span><span class="sxs-lookup"><span data-stu-id="f4d36-121">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="f4d36-122">Como criar um soquete</span><span class="sxs-lookup"><span data-stu-id="f4d36-122">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="f4d36-123">Soquetes</span><span class="sxs-lookup"><span data-stu-id="f4d36-123">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
