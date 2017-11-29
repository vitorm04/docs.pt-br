---
title: Soquetes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de5778e398a9a7205e99cc810d0b672ac247da08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sockets"></a><span data-ttu-id="f388e-102">Soquetes</span><span class="sxs-lookup"><span data-stu-id="f388e-102">Sockets</span></span>
<span data-ttu-id="f388e-103">O namespace <xref:System.Net.Sockets> contém uma implementação gerenciada da interface do Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="f388e-103">The <xref:System.Net.Sockets> namespace contains a managed implementation of the Windows Sockets interface.</span></span> <span data-ttu-id="f388e-104">Todas as outras classes de acesso à rede no namespace <xref:System.Net> são criadas com base nessa implementação de soquetes.</span><span class="sxs-lookup"><span data-stu-id="f388e-104">All other network-access classes in the <xref:System.Net> namespace are built on top of this implementation of sockets.</span></span>  
  
 <span data-ttu-id="f388e-105">A classe <xref:System.Net.Sockets.Socket> do .NET Framework é uma versão de código gerenciado dos serviços de soquete fornecidos pela API do Winsock32.</span><span class="sxs-lookup"><span data-stu-id="f388e-105">The .NET Framework <xref:System.Net.Sockets.Socket> class is a managed-code version of the socket services provided by the Winsock32 API.</span></span> <span data-ttu-id="f388e-106">Na maioria dos casos, os métodos da classe **Socket** simplesmente realizam marshaling dos dados em seus equivalentes nativos do Win32 e manipulam as verificações de segurança necessárias.</span><span class="sxs-lookup"><span data-stu-id="f388e-106">In most cases, the **Socket** class methods simply marshal data into their native Win32 counterparts and handle any necessary security checks.</span></span>  
  
 <span data-ttu-id="f388e-107">A classe **Socket** dá suporte a dois modos básicos: síncrono e assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f388e-107">The **Socket** class supports two basic modes, synchronous and asynchronous.</span></span> <span data-ttu-id="f388e-108">No modo síncrono, as chamadas a funções que executam operações de rede (como <xref:System.Net.Sockets.Socket.Send%2A> e <xref:System.Net.Sockets.Socket.Receive%2A>) aguardam até que a operação seja concluída antes de retornar o controle ao programa de chamada.</span><span class="sxs-lookup"><span data-stu-id="f388e-108">In synchronous mode, calls to functions that perform network operations (such as <xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.Receive%2A>) wait until the operation completes before returning control to the calling program.</span></span> <span data-ttu-id="f388e-109">No modo assíncrono, essas chamadas são retornadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="f388e-109">In asynchronous mode, these calls return immediately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f388e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f388e-110">See Also</span></span>  
 [<span data-ttu-id="f388e-111">Como criar um soquete</span><span class="sxs-lookup"><span data-stu-id="f388e-111">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [<span data-ttu-id="f388e-112">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f388e-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
