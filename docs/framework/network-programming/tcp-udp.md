---
title: TCP-UDP
description: Saiba como as classes TcpClient, TcpListener e UdpClient lidam com os serviços TCP e UDP, que cuidam dos detalhes da transferência de dados no .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
ms.openlocfilehash: ae6d2f9ced2235aa1b9b8fada8064d7e4be970a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502087"
---
# <a name="tcp-udp"></a><span data-ttu-id="1cf56-103">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="1cf56-103">TCP-UDP</span></span>
<span data-ttu-id="1cf56-104">Os aplicativos podem usar os serviços dos protocolos TCP e UDP com as classes <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> e <xref:System.Net.Sockets.UdpClient>.</span><span class="sxs-lookup"><span data-stu-id="1cf56-104">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="1cf56-105">Essas classes de protocolo são criadas com base na classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> e cuidam dos detalhes da transferência de dados.</span><span class="sxs-lookup"><span data-stu-id="1cf56-105">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="1cf56-106">As classes de protocolo usam os métodos síncronos da classe **Socket** para fornecer acesso simples e direto aos serviços de rede, sem a sobrecarga de manter informações de estado ou de conhecer os detalhes da configuração de soquetes específicos ao protocolo.</span><span class="sxs-lookup"><span data-stu-id="1cf56-106">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="1cf56-107">Para usar métodos **Socket** assíncronos, use os métodos assíncronos fornecidos pela classe <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="1cf56-107">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="1cf56-108">Para acessar os recursos da classe **Socket** não expostos pelas classes de protocolo, use a classe **Socket**.</span><span class="sxs-lookup"><span data-stu-id="1cf56-108">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="1cf56-109">**TcpClient** e **TcpListener** representam a rede que usa a classe **NetworkStream**.</span><span class="sxs-lookup"><span data-stu-id="1cf56-109">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="1cf56-110">Use o método <xref:System.Net.Sockets.TcpClient.GetStream%2A> para retornar o fluxo de rede e, em seguida, chamar os métodos <xref:System.Net.Sockets.NetworkStream.Read%2A> e <xref:System.Net.Sockets.NetworkStream.Write%2A> do fluxo.</span><span class="sxs-lookup"><span data-stu-id="1cf56-110">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="1cf56-111">O **NetworkStream** não possui o soquete subjacente das classes de protocolo e, portanto, seu fechamento não afeta o soquete.</span><span class="sxs-lookup"><span data-stu-id="1cf56-111">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="1cf56-112">A classe **UdpClient** usa uma matriz de bytes para armazenar o datagrama UDP.</span><span class="sxs-lookup"><span data-stu-id="1cf56-112">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="1cf56-113">Use o método <xref:System.Net.Sockets.UdpClient.Send%2A> para enviar os dados para a rede e o método <xref:System.Net.Sockets.UdpClient.Receive%2A> para receber um datagrama de entrada.</span><span class="sxs-lookup"><span data-stu-id="1cf56-113">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf56-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="1cf56-114">See also</span></span>

- [<span data-ttu-id="1cf56-115">Usando serviços de TCP</span><span class="sxs-lookup"><span data-stu-id="1cf56-115">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="1cf56-116">Usando serviços de UDP</span><span class="sxs-lookup"><span data-stu-id="1cf56-116">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="1cf56-117">Usando fluxos na rede</span><span class="sxs-lookup"><span data-stu-id="1cf56-117">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="1cf56-118">Usando um soquete de servidor assíncrono</span><span class="sxs-lookup"><span data-stu-id="1cf56-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="1cf56-119">Usando um soquete de cliente assíncrono</span><span class="sxs-lookup"><span data-stu-id="1cf56-119">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="1cf56-120">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="1cf56-120">Using Application Protocols</span></span>](using-application-protocols.md)
