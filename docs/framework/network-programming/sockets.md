---
title: Soquetes
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
ms.openlocfilehash: 3a8e141d79a7f261cd969dc78a656a89ffc8bc30
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196525"
---
# <a name="sockets"></a>Soquetes
O namespace <xref:System.Net.Sockets> contém uma implementação gerenciada da interface do Windows Sockets. Todas as outras classes de acesso à rede no namespace <xref:System.Net> são criadas com base nessa implementação de soquetes.  
  
 A classe <xref:System.Net.Sockets.Socket> do .NET Framework é uma versão de código gerenciado dos serviços de soquete fornecidos pela API do Winsock32. Na maioria dos casos, os métodos da classe **Socket** simplesmente realizam marshaling dos dados em seus equivalentes nativos do Win32 e manipulam as verificações de segurança necessárias.  
  
 A classe **Socket** dá suporte a dois modos básicos: síncrono e assíncrono. No modo síncrono, as chamadas a funções que executam operações de rede (como <xref:System.Net.Sockets.Socket.Send%2A> e <xref:System.Net.Sockets.Socket.Receive%2A>) aguardam até que a operação seja concluída antes de retornar o controle ao programa de chamada. No modo assíncrono, essas chamadas são retornadas imediatamente.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um soquete](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md)
