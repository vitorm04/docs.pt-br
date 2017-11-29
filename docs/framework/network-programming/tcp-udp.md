---
title: TCP-UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 04a3bb1c7499a60175aaaa9715e780ea5ddceb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="tcp-udp"></a>TCP-UDP
Os aplicativos podem usar os serviços dos protocolos TCP e UDP com as classes <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> e <xref:System.Net.Sockets.UdpClient>. Essas classes de protocolo são criadas com base na classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> e cuidam dos detalhes da transferência de dados.  
  
 As classes de protocolo usam os métodos síncronos da classe **Socket** para fornecer acesso simples e direto aos serviços de rede, sem a sobrecarga de manter informações de estado ou de conhecer os detalhes da configuração de soquetes específicos ao protocolo. Para usar métodos **Socket** assíncronos, use os métodos assíncronos fornecidos pela classe <xref:System.Net.Sockets.NetworkStream>. Para acessar os recursos da classe **Socket** não expostos pelas classes de protocolo, use a classe **Socket**.  
  
 **TcpClient** e **TcpListener** representam a rede que usa a classe **NetworkStream**. Use o método <xref:System.Net.Sockets.TcpClient.GetStream%2A> para retornar o fluxo de rede e, em seguida, chamar os métodos <xref:System.Net.Sockets.NetworkStream.Read%2A> e <xref:System.Net.Sockets.NetworkStream.Write%2A> do fluxo. O **NetworkStream** não possui o soquete subjacente das classes de protocolo e, portanto, seu fechamento não afeta o soquete.  
  
 A classe **UdpClient** usa uma matriz de bytes para armazenar o datagrama UDP. Use o método <xref:System.Net.Sockets.UdpClient.Send%2A> para enviar os dados para a rede e o método <xref:System.Net.Sockets.UdpClient.Receive%2A> para receber um datagrama de entrada.  
  
## <a name="see-also"></a>Consulte também  
 [Usando os serviços de TCP](../../../docs/framework/network-programming/using-tcp-services.md)  
 [Usando os serviços de UDP](../../../docs/framework/network-programming/using-udp-services.md)  
 [O uso de fluxos na rede](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Usando um soquete assíncrono de servidor](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Usando um soquete do cliente assíncrono](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md)
