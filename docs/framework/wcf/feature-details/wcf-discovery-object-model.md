---
title: Modelo de objeto de descoberta do WCF
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: debcb08802894a34e16d9aa65bbbb1b0282794f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184219"
---
# <a name="wcf-discovery-object-model"></a>Modelo de objeto de descoberta do WCF
O WCF Discovery consiste em um conjunto de tipos que fornecem um modelo de programação unificado que permite escrever serviços que são descobertos em tempo de execução e clientes que encontram e usam esses serviços.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Fazendo um serviço de serviço sustal e encontrando serviços  
 Para tornar um serviço WCF <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> despositivo, adicione um ao host <xref:System.ServiceModel.Description.ServiceDescription> de serviço e adicione um ponto final de descoberta. Se um serviço estiver configurado para enviar <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>mensagens de anúncio (adicionando um ) o anúncio será enviado quando o host de serviço for aberto e fechado.  
  
 Um cliente que deseja ouvir mensagens de anúncio de serviço hospeda um serviço de anúncio e adiciona um ou mais pontos finais de anúncio. O serviço de anúnciorecebe mensagens de anúncio e levanta eventos de anúncio.  
  
 Um cliente <xref:System.ServiceModel.Discovery.DiscoveryClient> usa a classe para procurar serviços disponíveis. O aplicativo do cliente <xref:System.ServiceModel.Discovery.DiscoveryClient> instancia a classe, passando em um ponto final de descoberta que especifica para onde enviar mensagens de descoberta. O cliente <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> chama o método, que envia uma `Probe` solicitação. Os serviços que ouvem mensagens de descoberta recebem essa `Probe` solicitação. Se o serviço corresponder aos `Probe`critérios especificados `ProbeMatch` no , ele envia uma mensagem de volta para o cliente.  
  
## <a name="object-model"></a>Modelo de Objeto  
 A API de descoberta do WCF define as seguintes classes:  
  
- <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
- <xref:System.ServiceModel.Discovery.FindCriteria>  
  
- <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
- <xref:System.ServiceModel.Discovery.FindResponse>  
  
- <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
- <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>Announcementclient  
 A <xref:System.ServiceModel.Discovery.AnnouncementClient> classe fornece métodos síncronos e assíncronos para enviar mensagens de anúncio. Existem dois tipos de mensagens de anúncio, Hello e Bye. Uma mensagem hello é enviada para indicar que um serviço está disponível e uma mensagem Te é enviada para indicar que um serviço existente ficou indisponível. O desenvolvedor <xref:System.ServiceModel.Discovery.AnnouncementClient> cria uma instância, <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> passando uma instância de como parâmetro de construtor.  
  
## <a name="announcementendpoint"></a>Announcementendpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>representa um ponto final padrão com um contrato de anúncio fixo. Ele é usado por um serviço ou cliente para enviar e receber mensagens de anúncio. Por padrão, <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> a classe está definida para usar a versão do protocolo WS_Discovery 11.  
  
## <a name="announcementservice"></a>Announcementservice  
 <xref:System.ServiceModel.Discovery.AnnouncementService>é uma implementação fornecida pelo sistema de um serviço de anúncio que recebe e processa mensagens de anúncio. Quando uma mensagem Hello ou <xref:System.ServiceModel.Discovery.AnnouncementService> Bye é recebida, a instância chama o método <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> virtual apropriado ou <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, o que levanta eventos de anúncio.  
  
## <a name="discoveryclient"></a>Discoveryclient  
 A <xref:System.ServiceModel.Discovery.DiscoveryClient> classe é usada por um aplicativo cliente para encontrar e resolver os serviços disponíveis. Fornece métodos síncronos e assíncronos para encontrar e <xref:System.ServiceModel.Discovery.FindCriteria> <xref:System.ServiceModel.Discovery.ResolveCriteria> resolver serviços com base no especificado e respectivamente. O desenvolvedor <xref:System.ServiceModel.Discovery.DiscoveryClient> cria uma instância <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> e fornece uma instância de como parâmetro de construção.  
  
 Para encontrar um serviço, o desenvolvedor invoca o método `Find` síncrono <xref:System.ServiceModel.Discovery.FindCriteria> ou assíncrono, que fornece uma instância que contém os critérios de pesquisa a serem usados. O <xref:System.ServiceModel.Discovery.DiscoveryClient> cria `Probe` uma mensagem com os cabeçalhos apropriados e envia a solicitação de encontrar. Como pode haver mais `Find` de uma solicitação pendente a qualquer momento, o cliente correlaciona as respostas recebidas e valida a resposta. Em seguida, ele entrega os `Find` resultados <xref:System.ServiceModel.Discovery.FindResponse>para o chamador da operação usando .  
  
 Para resolver um serviço conhecido, o desenvolvedor invoca o `Resolve` método síncrono <xref:System.ServiceModel.Discovery.ResolveCriteria> ou <xref:System.ServiceModel.EndpointAddress> assíncrono que fornece uma instância que contém o do serviço conhecido. O <xref:System.ServiceModel.Discovery.DiscoveryClient> cria `Resolve` a mensagem com os cabeçalhos apropriados e envia a solicitação de resolução. A resposta recebida está correlacionada com as solicitações de resolução `Resolve` pendentes <xref:System.ServiceModel.Discovery.ResolveResponse>e o resultado é entregue ao chamador da operação utilizando.  
  
 Se um proxy de descoberta estiver <xref:System.ServiceModel.Discovery.DiscoveryClient> presente na rede e enviar a solicitação de descoberta de forma multicast, o proxy de descoberta pode responder com a mensagem Hello de supressão multicast. O <xref:System.ServiceModel.Discovery.DiscoveryClient> evento `ProxyAvailable` levanta quando recebe mensagens de `Find` `Resolve` Olá em resposta a solicitações pendentes ou pendentes. O `ProxyAvailable` evento <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> contém o proxy sobre a descoberta. Cabe ao desenvolvedor usar essas informações para mudar de Modo Ad hoc para Gerenciado.  
  
## <a name="discoveryendpoint"></a>Discoveryendpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>representa um ponto final padrão com um contrato de descoberta fixo. Ele é usado por um serviço ou cliente para enviar ou receber mensagens de descoberta. Por padrão, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> está <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> definido para usar o modo e a versão WSDiscovery11 WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>Discoverymessagesequencegenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>é usado para <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> gerar um quando o serviço está enviando mensagens de Discovery ou Anúncio.  
  
## <a name="discoveryservice"></a>Discoveryservice  
 A <xref:System.ServiceModel.Discovery.DiscoveryService> classe abstrata fornece uma estrutura `Probe` `Resolve` para recebimento e processamento e mensagens. Quando `Probe` uma mensagem <xref:System.ServiceModel.Discovery.DiscoveryService> é recebida, cria uma instância de <xref:System.ServiceModel.Discovery.FindRequestContext> <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> base na mensagem recebida e invoca o método virtual. Quando `Resolve` uma mensagem <xref:System.ServiceModel.Discovery.DiscoveryService> é <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> recebida, invoca o método virtual. Você pode herdar desta classe para fornecer uma implementação personalizada do Discovery Service.  
  
## <a name="discoveryproxy"></a>Discoveryproxy  
 A <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe abstrata fornece uma estrutura para receber e processar mensagens de descoberta e anúncio. Você herda desta classe quando está implementando um proxy de descoberta personalizado. Quando `Probe` uma mensagem é recebida <xref:System.ServiceModel.Discovery.DiscoveryProxy> em `BeginShouldRedirectFind` multicast, a classe chama o método virtual para determinar se uma mensagem de supressão multicast deve ser enviada. Se o desenvolvedor decidir não enviar uma mensagem `Probe` de supressão de multicast ou <xref:System.ServiceModel.Discovery.FindRequestContext> se a mensagem foi recebida `OnBeginFind` por unicast, ela criará uma instância da classe com base na mensagem recebida e invoca o método virtual. Quando `Resolve` uma mensagem é recebida <xref:System.ServiceModel.Discovery.DiscoveryProxy> em `ShouldRedirectResolve` multicast, a classe chama o método virtual para determinar se uma mensagem de supressão multicast deve ser enviada. Se o desenvolvedor decidir não enviar uma mensagem `Resolve` de supressão de multicast ou <xref:System.ServiceModel.Discovery.ResolveCriteria> se a mensagem foi recebida `OnBeginResolve` por unicast, ela criará uma instância da classe com base na mensagem recebida e invoca o método virtual. Quando uma mensagem Hello or <xref:System.ServiceModel.Discovery.DiscoveryProxy> Bye é`OnBeginOnlineAnnouncement` recebida, chama o método virtual apropriado (ou), `OnBeingOfflineAnnouncement`que levanta eventos de anúncio.  
  
## <a name="discoveryversion"></a>Discoveryversion  
 A <xref:System.ServiceModel.Discovery.DiscoveryVersion> classe representa a versão do protocolo de descoberta a ser usada.  
  
## <a name="endpointdiscoverybehavior"></a>Endpointdiscoverybehavior  
 A <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> classe é usada para controlar a capacidade de descoberta de um ponto final, especificar as extensões, nomes adicionais de tipo de contrato. e os escopos associados a esse ponto final. Esse comportamento é adicionado a um ponto <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>final do aplicativo para configurar seu . Quando <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> é adicionado ao host de serviço, todos os pontos finais do aplicativo hospedados pelo host de serviço por padrão tornam-se descobertos. O desenvolvedor pode desativar a descoberta para <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> um `false`ponto final específico definindo a propriedade para .  
  
## <a name="endpointdiscoverymetadata"></a>Endpointdiscoverymetadata  
 A <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> classe fornece uma representação independente de versão de um ponto final publicado pelo serviço. Ele contém endereços de ponto final, ouvir URIs, nomes de tipos de contrato, escopos, versão de metadados e extensões especificadas pelo desenvolvedor do serviço. O <xref:System.ServiceModel.Discovery.FindCriteria> enviado pelo cliente `Probe` durante uma operação <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>é compatível com o . Se os critérios corresponderem, o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> é devolvido ao cliente. O endereço de <xref:System.ServiceModel.Discovery.ResolveCriteria> ponto final é compatível <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>com o endereço de ponto final de . Se os critérios corresponderem, o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> é devolvido ao cliente.  
  
## <a name="findcriteria"></a>Findcriteria  
 A <xref:System.ServiceModel.Discovery.FindCriteria> classe é uma classe independente de versão usada para especificar os critérios usados ao encontrar um serviço. Ele suporta totalmente os critérios definidos pelo WS-Discovery para serviços de correspondência. Ele também tem extensões que os desenvolvedores podem usar para especificar valores personalizados que podem ser usados durante o processo de correspondência. O desenvolvedor pode fornecer os `Find` critérios de <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>término da operação especificando o , que especifica o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>número total de serviços que o desenvolvedor está procurando ou que especifica o , que é o valor que especifica quanto tempo o cliente espera por respostas.  
  
## <a name="findrequestcontext"></a>Findrequestcontext  
 A <xref:System.ServiceModel.Discovery.FindRequestContext> classe é instanciada pelo serviço `Probe` de descoberta com base `Find` na mensagem que recebe quando um cliente inicia uma operação. Ele contém uma <xref:System.ServiceModel.Discovery.FindCriteria> instância que foi especificada pelo cliente.  
  
## <a name="findresponse"></a>Findresponse  
 A <xref:System.ServiceModel.Discovery.FindResponse> classe é devolvida ao <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> interlocutor com as `Find` respostas da operação. Também está presente <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>em . Contém uma coleção <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>de , que é a coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>pontos finais descobertos e um dicionário de e .  
  
## <a name="resolvecriteria"></a>Resolvecriteria  
 A <xref:System.ServiceModel.Discovery.ResolveCriteria> classe é uma classe independente de versão usada para especificar os critérios usados ao resolver um serviço já conhecido. Ele contém o endereço final do serviço conhecido. O desenvolvedor pode fornecer os critérios de rescisão para a operação de resolução especificando o <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, que especifica quanto tempo o cliente espera por respostas.  
  
## <a name="resolveresponse"></a>Resolveresponse  
 O <xref:System.ServiceModel.Discovery.ResolveResponse> é devolvido ao chamador do <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> método `Resolve` com a resposta da operação. Também está presente <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>em . Ele contém uma <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>instância de , que são os <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>pontos finais descobertos e uma instância de .  
  
## <a name="servicediscoverybehavior"></a>Servicediscoverybehavior  
 A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> classe permite que o desenvolvedor adicione o recurso de descoberta a um serviço. Você adiciona esse <xref:System.ServiceModel.ServiceHost>comportamento ao . A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> classe itera sobre os pontos finais do aplicativo adicionados ao host de serviço e cria uma coleção dos <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> pontos finais descobertos. Todos os pontos finais são descobertos por padrão. A descoberta de um ponto final específico <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> pode ser controlada adicionando-o a esse ponto final em particular. Se os pontos finais <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> do anúncio forem adicionados, o anúncio de todos os pontos finais descobertos será enviado sobre cada um dos pontos finais do anúncio quando o host de serviço for aberto ou fechado.  
  
## <a name="udpannouncementendpoint"></a>Udpannouncementendpoint  
 A <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> classe é um ponto final de anúncio padrão pré-configurado para anúncio sobre uma vinculação multicast UDP. Por padrão, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> está definido para usar a versão wsapril2005 WS_Discovery.  
  
## <a name="udpdiscoveryendpoint"></a>Udpdiscoveryendpoint  
 A <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> classe é um ponto final de detecção padrão pré-configurado para detecção sobre uma vinculação multicast UDP. Por padrão, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> está definido para usar a versão e <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> o modo WSDiscovery11 WS-Discovery do WSDiscovery.
