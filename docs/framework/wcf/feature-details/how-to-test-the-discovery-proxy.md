---
title: 'Como: O Proxy de descoberta de teste'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 3c159481813266386706b34d172bbf9614a8253d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590507"
---
# <a name="how-to-test-the-discovery-proxy"></a>Como: O Proxy de descoberta de teste
Esta é a quarta de quatro tópicos que mostra como implementar um proxy de descoberta. No tópico anterior, [como: Implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), você implementou um aplicativo de cliente do WCF que usa o proxy de descoberta para localizar um serviço e, em seguida, chama o serviço. Este tópico descreve como verificar o proxy de descoberta, o serviço e o trabalho do aplicativo cliente, conforme o esperado.  
  
### <a name="run-the-discovery-proxy"></a>Executar o Proxy de descoberta  
  
1.  Abra um prompt de comando como administrador.  
  
2.  Você poderá ver uma caixa de diálogo que diz: Firewall do Windows bloqueou alguns recursos deste programa. Se você vir essa mensagem, clique o **Unblock** botão.  
  
3.  No prompt de comando, execute o proxy de descoberta, DiscoveryProxy.exe.  
  
4.  O aplicativo deve exibir o seguinte texto: `Proxy started. Hit Enter to exit`.  
  
### <a name="run-the-discoverable-service"></a>Executar o serviço de descoberta  
  
1.  Abra um prompt de comando como administrador.  
  
2.  No prompt de comando, execute o serviço de descoberta Service.exe.  
  
3.  O DiscoveryProxy.exe deve exibir o seguinte texto: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Executar o aplicativo cliente  
  
1.  Abra um prompt de comando.  
  
2.  No prompt de comando, execute o aplicativo de client.exe.  
  
3.  Depois de alguns segundos, o aplicativo cliente exibe o texto a seguir: Conectar-se no [serviço de ponto de extremidade].  
  
4.  O service.exe deve, em seguida, exibir o texto a seguir: Solicitação recebida a saudação, responderá.  
  
5.  O client.exe deve, em seguida, exibir o texto a seguir: Cliente de Olá!  
  
### <a name="shut-down-the-applications"></a>Desligue os aplicativos  
  
1.  Desligar o aplicativo cliente.  
  
2.  Desligamento do serviço. O proxy de descoberta exibe o seguinte texto: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Desligue o proxy de descoberta.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Como: Implementar um Proxy de descoberta](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [Como: Implementar um serviço de descoberta que registra com o Proxy de descoberta](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [Como: Implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
