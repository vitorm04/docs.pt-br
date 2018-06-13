---
title: Como criar um soquete
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 600ea82965c332c8620db689abb50965f15f0067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396942"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="020b5-102">Como criar um soquete</span><span class="sxs-lookup"><span data-stu-id="020b5-102">How to: Create a Socket</span></span>
<span data-ttu-id="020b5-103">Antes de poder usar um soquete para se comunicar com dispositivos remotos, o soquete deve ser inicializado com as informações de protocolo e endereço de rede.</span><span class="sxs-lookup"><span data-stu-id="020b5-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="020b5-104">O construtor da classe <xref:System.Net.Sockets.Socket> tem parâmetros que especificam a família de endereços, o tipo de soquete e o tipo de protocolo usado pelo soquete para fazer conexões.</span><span class="sxs-lookup"><span data-stu-id="020b5-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="020b5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="020b5-105">Example</span></span>  
 <span data-ttu-id="020b5-106">O exemplo a seguir cria um Socket que pode ser usado para se comunicar em uma rede baseada em TCP/IP, como a Internet.</span><span class="sxs-lookup"><span data-stu-id="020b5-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="020b5-107">Para usar o UDP em vez do TCP, altere o tipo de protocolo, como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="020b5-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="020b5-108">A enumeração <xref:System.Net.Sockets.AddressFamily> especifica as famílias de endereços padrão usadas pela classe **Socket** para resolver endereços de rede (por exemplo, o membro **AddressFamily.InterNetwork** especifica a família de endereços IP versão 4).</span><span class="sxs-lookup"><span data-stu-id="020b5-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="020b5-109">A enumeração <xref:System.Net.Sockets.SocketType> especifica o tipo de soquete (por exemplo, o membro **SocketType.Stream** indica um soquete padrão para envio e recebimento de dados com o controle de fluxo).</span><span class="sxs-lookup"><span data-stu-id="020b5-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="020b5-110">A enumeração <xref:System.Net.Sockets.ProtocolType> especifica o protocolo de rede a ser usado ao se comunicar no **Socket** (por exemplo, **ProtocolType.Tcp** indica que o soquete usa TCP; **ProtocolType.Udp** indica que o soquete usa UDP).</span><span class="sxs-lookup"><span data-stu-id="020b5-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="020b5-111">Depois que um **Socket** for criado, ele poderá iniciar uma conexão com um ponto de extremidade remoto ou receber conexões de dispositivos remotos.</span><span class="sxs-lookup"><span data-stu-id="020b5-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020b5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="020b5-112">See Also</span></span>  
 [<span data-ttu-id="020b5-113">Usando soquetes do cliente</span><span class="sxs-lookup"><span data-stu-id="020b5-113">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="020b5-114">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="020b5-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
