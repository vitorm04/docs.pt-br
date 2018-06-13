---
title: Como testar o proxy de descoberta
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 35edbd03e912ae2d9c491afb28dee1c4a3055d14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491216"
---
# <a name="how-to-test-the-discovery-proxy"></a>Como testar o proxy de descoberta
Esta é a quarta de quatro tópicos que mostra como implementar um proxy de descoberta. No tópico anterior, [como: implementar um aplicativo cliente que usa o Proxy de descoberta para localizar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), implementado um aplicativo de cliente do WCF que usa o proxy de descoberta para localizar um serviço e, em seguida, chama o serviço. Este tópico descreve como verificar o proxy de descoberta, o serviço e o trabalho de aplicativo cliente, conforme o esperado.  
  
### <a name="run-the-discovery-proxy"></a>Executar o Proxy de descoberta  
  
1.  Abra um prompt de comando como administrador.  
  
2.  Você verá um diálogo que informa: Firewall do Windows bloqueou alguns recursos deste programa. Se você vir essa mensagem, clique no **desbloquear** botão.  
  
3.  No prompt de comando, execute o proxy de descoberta, DiscoveryProxy.exe.  
  
4.  O aplicativo deve exibir o seguinte texto: `Proxy started. Hit Enter to exit`.  
  
### <a name="run-the-discoverable-service"></a>Executar o serviço de descoberta  
  
1.  Abra um prompt de comando como administrador.  
  
2.  No prompt de comando, execute o serviço detectável Service.exe.  
  
3.  O DiscoveryProxy.exe devem exibir o seguinte texto: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Executar o aplicativo cliente  
  
1.  Abra um prompt de comando.  
  
2.  No prompt de comando, execute o aplicativo client.exe.  
  
3.  Depois de alguns segundos, o aplicativo cliente exibe o seguinte texto: conectar-se a [serviço de ponto de extremidade].  
  
4.  O service.exe deve exibir o seguinte texto: saudação solicitação recebida, I responderá.  
  
5.  O client.exe deve exibir o seguinte texto: cliente Olá!  
  
### <a name="shut-down-the-applications"></a>Desligar os aplicativos  
  
1.  Desligar o aplicativo cliente.  
  
2.  Desligar o serviço. O proxy de descoberta exibe o seguinte texto: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Desligar o proxy de descoberta.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Como implementar um proxy de descoberta](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [Como implementar um serviço de descoberta que registra usando o proxy de descoberta](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [Como implementar um aplicativo cliente que usa o proxy de descoberta para localizar um serviço](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
