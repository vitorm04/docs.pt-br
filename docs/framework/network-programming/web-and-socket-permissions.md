---
title: "Permissões da Web e de soquete"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 102d7d92384d77b5fbb56cd8c3eb859ec64bcca0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="web-and-socket-permissions"></a>Permissões da Web e de soquete
A segurança da Internet para aplicativos que usam o namespace <xref:System.Net> é fornecida pelas classes <xref:System.Net.WebPermission> e <xref:System.Net.SocketPermission>. A classe **WebPermission** controla o direito de um aplicativo de solicitar dados de um URI ou de atender a um URI para a Internet. A classe **SocketPermission** controla o direito de um aplicativo de usar um <xref:System.Net.Sockets.Socket> para aceitar dados em uma porta local ou de entrar em contato com dispositivos remotos usando um protocolo de transporte em outro endereço, com base no host, no número da porta e no protocolo de transporte do soquete.  
  
 A classe de permissão usada depende do tipo de aplicativo. Os aplicativos que usam <xref:System.Net.WebRequest> e seus descendentes devem usar a classe **WebPermission** para gerenciar permissões. Os aplicativos que usam o acesso no nível do soquete devem usar a classe **SocketPermission** para gerenciar permissões.  
  
 **WebPermission** e **SocketPermission** definem duas permissões: aceitação e conexão. A aceitação concede ao aplicativo o direito de responder a uma conexão de entrada de outra entidade. Connect concede ao aplicativo o direito de iniciar uma conexão com outra entidade.  
  
 Para instâncias **SocketPermission**, aceitação significa que um aplicativo pode aceitar conexões de entrada em um endereço de transporte local; conexão significa que um aplicativo pode se conectar a um endereço de transporte remoto (ou local).  
  
 Para instâncias **WebPermission**, aceitação significa que um aplicativo pode exportar o URI controlado pela **WebPermission** para o mundo; conexão significa que um aplicativo pode acessar esse URI (seja ele local ou remoto).  
  
## <a name="see-also"></a>Consulte também  
 [Segurança](../../../docs/standard/security/index.md)  
 [Segurança na programação de rede](../../../docs/framework/network-programming/security-in-network-programming.md)
