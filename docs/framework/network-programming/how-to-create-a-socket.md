---
title: Como criar um soquete
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
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
caps.latest.revision: 7
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 02b02b2fbc5398d7afda8884a04eafdaee12aef4
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="03b22-102">Como criar um soquete</span><span class="sxs-lookup"><span data-stu-id="03b22-102">How to: Create a Socket</span></span>
<span data-ttu-id="03b22-103">Antes de poder usar um soquete para se comunicar com dispositivos remotos, o soquete deve ser inicializado com as informações de protocolo e endereço de rede.</span><span class="sxs-lookup"><span data-stu-id="03b22-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="03b22-104">O construtor da classe <xref:System.Net.Sockets.Socket> tem parâmetros que especificam a família de endereços, o tipo de soquete e o tipo de protocolo usado pelo soquete para fazer conexões.</span><span class="sxs-lookup"><span data-stu-id="03b22-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03b22-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03b22-105">Example</span></span>  
 <span data-ttu-id="03b22-106">O exemplo a seguir cria um Socket que pode ser usado para se comunicar em uma rede baseada em TCP/IP, como a Internet.</span><span class="sxs-lookup"><span data-stu-id="03b22-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="03b22-107">Para usar o UDP em vez do TCP, altere o tipo de protocolo, como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="03b22-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="03b22-108">A enumeração <xref:System.Net.Sockets.AddressFamily> especifica as famílias de endereços padrão usadas pela classe **Socket** para resolver endereços de rede (por exemplo, o membro **AddressFamily.InterNetwork** especifica a família de endereços IP versão 4).</span><span class="sxs-lookup"><span data-stu-id="03b22-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="03b22-109">A enumeração <xref:System.Net.Sockets.SocketType> especifica o tipo de soquete (por exemplo, o membro **SocketType.Stream** indica um soquete padrão para envio e recebimento de dados com o controle de fluxo).</span><span class="sxs-lookup"><span data-stu-id="03b22-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="03b22-110">A enumeração <xref:System.Net.Sockets.ProtocolType> especifica o protocolo de rede a ser usado ao se comunicar no **Socket** (por exemplo, **ProtocolType.Tcp** indica que o soquete usa TCP; **ProtocolType.Udp** indica que o soquete usa UDP).</span><span class="sxs-lookup"><span data-stu-id="03b22-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="03b22-111">Depois que um **Socket** for criado, ele poderá iniciar uma conexão com um ponto de extremidade remoto ou receber conexões de dispositivos remotos.</span><span class="sxs-lookup"><span data-stu-id="03b22-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b22-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03b22-112">See Also</span></span>  
 <span data-ttu-id="03b22-113">[Usando soquetes de cliente](../../../docs/framework/network-programming/using-client-sockets.md) </span><span class="sxs-lookup"><span data-stu-id="03b22-113">[Using Client Sockets](../../../docs/framework/network-programming/using-client-sockets.md) </span></span>  
 [<span data-ttu-id="03b22-114">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="03b22-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)

