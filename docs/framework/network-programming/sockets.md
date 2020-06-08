---
title: Soquetes
description: Saiba mais sobre a classe de soquete .NET Framework, que é uma versão de código gerenciado dos serviços de soquete fornecidos pela API Winsock32.
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
ms.openlocfilehash: b44409a0fafc770625be55881ccef3b57045acef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502126"
---
# <a name="sockets"></a><span data-ttu-id="b7667-103">Soquetes</span><span class="sxs-lookup"><span data-stu-id="b7667-103">Sockets</span></span>
<span data-ttu-id="b7667-104">O namespace <xref:System.Net.Sockets> contém uma implementação gerenciada da interface do Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="b7667-104">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="b7667-105">Todas as outras classes de acesso à rede no namespace <xref:System.Net> são criadas com base nessa implementação de soquetes.</span><span class="sxs-lookup"><span data-stu-id="b7667-105">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="b7667-106">A classe <xref:System.Net.Sockets.Socket> do .NET Framework é uma versão de código gerenciado dos serviços de soquete fornecidos pela API do Winsock32.</span><span class="sxs-lookup"><span data-stu-id="b7667-106">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="b7667-107">Na maioria dos casos, os métodos da classe **Socket** simplesmente realizam marshaling dos dados em seus equivalentes nativos do Win32 e manipulam as verificações de segurança necessárias.</span><span class="sxs-lookup"><span data-stu-id="b7667-107">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="b7667-108">A classe **Socket** dá suporte a dois modos básicos: síncrono e assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b7667-108">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="b7667-109">No modo síncrono, as chamadas a funções que executam operações de rede (como <xref:System.Net.Sockets.Socket.Send%2A> e <xref:System.Net.Sockets.Socket.Receive%2A>) aguardam até que a operação seja concluída antes de retornar o controle ao programa de chamada.</span><span class="sxs-lookup"><span data-stu-id="b7667-109">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="b7667-110">No modo assíncrono, essas chamadas são retornadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="b7667-110">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7667-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7667-111">See also</span></span>

- [<span data-ttu-id="b7667-112">Como criar um soquete</span><span class="sxs-lookup"><span data-stu-id="b7667-112">How to: Create a Socket</span></span>](how-to-create-a-socket.md)

- [<span data-ttu-id="b7667-113">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="b7667-113">Using Application Protocols</span></span>](using-application-protocols.md)
