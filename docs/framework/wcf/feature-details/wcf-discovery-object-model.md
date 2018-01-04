---
title: Modelo de objeto de descoberta do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 68d6e156612ce707aa678b6589510b710b73e38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-discovery-object-model"></a>Modelo de objeto de descoberta do WCF
Descoberta de WCF consiste em um conjunto de tipos que fornecem um modelo de programação unificado que permite que você escreva serviços que podem ser descobertos no tempo de execução e os clientes que encontrarem e usam esses serviços.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Tornar um serviço detectável e serviços de localização  
 Para tornar um serviço WCF detectável, adicione um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> para o <xref:System.ServiceModel.Description.ServiceDescription> do serviço de host e adicione um ponto de extremidade de descoberta. Se um serviço estiver configurado para enviar mensagens de aviso (adicionando um <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) a notificação é enviada quando o host de serviço é aberto e fechado.  
  
 Um cliente que deseja escutar mensagens de notificação de serviço hospeda um serviço de notificação e adiciona um ou mais pontos de extremidade de anúncio. O serviço de anúncio recebe mensagens de aviso e gera eventos de aviso.  
  
 Um cliente usa o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe para procurar serviços disponíveis. O aplicativo cliente instancia o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe, passando em um ponto de extremidade de descoberta que especifica o local enviar mensagens de descoberta. O cliente chama o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método, que envia um `Probe` solicitação. Serviços de escuta de recebem de mensagens de descoberta isso `Probe` solicitação. Se o serviço corresponde aos critérios especificados a `Probe`, ele envia um `ProbeMatch` mensagem de volta ao cliente.  
  
## <a name="object-model"></a>Modelo de objeto  
 A API de descoberta do WCF define as classes a seguir:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
-   <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria>  
  
-   <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
-   <xref:System.ServiceModel.Discovery.FindResponse>  
  
-   <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
-   <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  
  
-   <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 O <xref:System.ServiceModel.Discovery.AnnouncementClient> classe fornece métodos síncronos e assíncronos para enviar mensagens de aviso. Há dois tipos de mensagens de aviso, Hello e Bye. Uma mensagem de saudação é enviada para indicar que um serviço se tornou disponível e uma mensagem Bye é enviada para indicar que um serviço existente se tornou indisponível. O desenvolvedor cria um <xref:System.ServiceModel.Discovery.AnnouncementClient> instância, passando uma instância do <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> como um parâmetro de construtor.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>representa um ponto de extremidade padrão com um contrato de anúncio fixo. Ele é usado por um serviço ou cliente para enviar e receber mensagens de aviso. Por padrão, o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> classe está definida para usar a versão do protocolo WS_Discovery 11.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService>é uma implementação fornecido pelo sistema de um serviço de notificação que recebe e processa mensagens de aviso. Quando uma mensagem de saudação ou Bye é recebida, o <xref:System.ServiceModel.Discovery.AnnouncementService> instância chama o método virtual apropriado <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> ou <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, que gera eventos de aviso.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 O <xref:System.ServiceModel.Discovery.DiscoveryClient> classe é usada por um aplicativo cliente para localizar e resolver os serviços disponíveis. Fornece métodos síncronos e assíncronos para localizar e resolver os serviços com base em especificado <xref:System.ServiceModel.Discovery.FindCriteria> e <xref:System.ServiceModel.Discovery.ResolveCriteria> respectivamente. O desenvolvedor cria um <xref:System.ServiceModel.Discovery.DiscoveryClient> instância e fornece uma instância de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> como um parâmetro de construtor.  
  
 Para localizar um serviço, o desenvolvedor invoca síncronas ou assíncronas `Find` método, que fornece um <!--zz <xref:System.ServiceModel.Discription.FindCriteria> --> `FindCriteria` instância que contém os critérios de pesquisa para usar. O <xref:System.ServiceModel.Discovery.DiscoveryClient> cria um `Probe` mensagem com os cabeçalhos apropriados e envia a solicitação de localização. Como pode haver mais de um excelente `Find` solicitar a qualquer momento, o cliente se correlaciona as respostas recebidas e valida a resposta. Em seguida, distribui os resultados para o chamador do `Find` operação usando <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Para resolver um serviço conhecido, o desenvolvedor invoca síncronas ou assíncronas `Resolve` método que fornece uma instância de <!--zz <xref:System.ServiceModel.ResolveCriteria>--> `ResolveCriteria` que contém o <xref:System.ServiceModel.EndpointAddress> do serviço conhecido. O <xref:System.ServiceModel.Discovery.DiscoveryClient> cria o `Resolve` mensagem com os cabeçalhos apropriados e envia a solicitação de resolver. A resposta recebida é correlacionada contra as solicitações pendentes resolver e o resultado é fornecido para o chamador do `Resolve` operação usando <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Se houver um proxy de descoberta na rede e o <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` envia solicitações a descoberta de forma seletiva, o proxy de descoberta pode responder com a mensagem de saudação de supressão multicast. O <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` gera o `ProxyAvailable` evento quando ele recebe mensagens de saudação em resposta a pendentes `Find` ou `Resolve` solicitações. O `ProxyAvailable` evento contém o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> sobre o proxy de descoberta. É responsabilidade do desenvolvedor para usar essas informações para alternar do Ad-hoc para modo gerenciado.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>representa um ponto de extremidade padrão com um contrato de correção da descoberta. Ele é usado por um cliente ou serviço enviar ou receber mensagens de descoberta. Por padrão, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> está definido para usar <!--zz <xref:System.ServiceModel.Discovery.DiscoveryMode.Managed>--> `Managed` modo e a versão de WSDiscovery11 WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>é usado para gerar um <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> quando o serviço envia mensagens de descoberta ou anúncio.  
  
## <a name="discoveryservice"></a>DiscoveryService  
 O <xref:System.ServiceModel.Discovery.DiscoveryService> classe abstrata fornece uma estrutura para recebimento e processamento `Probe` e `Resolve` mensagens. Quando um `Probe` mensagem é recebida, <xref:System.ServiceModel.Discovery.DiscoveryService> cria uma instância de <xref:System.ServiceModel.Discovery.FindRequestContext> com base na mensagem de entrada e chama o <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> método virtual. Quando um `Resolve` mensagem é recebida, <xref:System.ServiceModel.Discovery.DiscoveryService> invoca o <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> método virtual. É possível herdar desta classe para fornecer uma implementação personalizada do serviço de descoberta.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 O <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe abstrata fornece uma estrutura para receber e processar mensagens de descoberta e o anúncio. Herdar desta classe quando você estiver implementando um proxy de descoberta personalizado. Quando um `Probe` mensagem é recebida por meio de multicast, o <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe chama o `BeginShouldRedirectFind` método virtual para determinar se uma mensagem de supressão multicast deve ser enviado. Se o desenvolvedor decidir por não enviar uma mensagem de supressão multicast ou se o `Probe` mensagem foi recebida por meio de unicast, ele cria uma instância do <xref:System.ServiceModel.Discovery.FindRequestContext> classe com base na mensagem de entrada e chama o `OnBeginFind` método virtual. Quando um `Resolve` mensagem é recebida por meio de multicast, o <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe chama o `ShouldRedirectResolve` método virtual para determinar se uma mensagem de supressão multicast deve ser enviado. Se o desenvolvedor decidir por não enviar uma mensagem de supressão multicast ou se o `Resolve` mensagem foi recebida por meio de unicast, ele cria uma instância do <xref:System.ServiceModel.Discovery.ResolveCriteria> classe com base na mensagem de entrada e chama o `OnBeginResolve` método virtual. Quando uma mensagem de saudação ou Bye é recebida, <xref:System.ServiceModel.Discovery.DiscoveryProxy> chama o método virtual apropriado (`OnBeginOnlineAnnouncement` ou `OnBeingOfflineAnnouncement`), que gera eventos de aviso.  
  
## <a name="discoveryversion"></a>discoveryVersion  
 O <xref:System.ServiceModel.Discovery.DiscoveryVersion> classe representa a versão do protocolo de descoberta para usar.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 O <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> classe é usada para controlar a capacidade de descoberta de um ponto de extremidade, especifique os nomes de tipo de contrato adicionais, extensões. e os escopos associados a esse ponto de extremidade. Esse comportamento é adicionado a um ponto de extremidade de aplicativo para configurar seu <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Quando <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> é adicionada para o host de serviço, todos os pontos de aplicativo hospedados pelo host de serviço por padrão ser descobertos. O desenvolvedor pode desativar a descoberta para um ponto de extremidade específico, definindo o <!--zz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enable%2A>--> `Enable` propriedade `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 O <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> classe fornece uma representação de versão independente de um ponto de extremidade publicado pelo serviço. Ele contém os endereços de ponto de extremidade, escutar URIs, nomes de tipo de contrato, escopos, versão de metadados e extensões especificadas pelo desenvolvedor de serviço. O <xref:System.ServiceModel.Discovery.FindCriteria> enviado pelo cliente durante um `Probe` operação é comparada com o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Se os critérios de correspondência, o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> é retornado ao cliente. O endereço de ponto de extremidade no <xref:System.ServiceModel.Discovery.ResolveCriteria> é comparado com o endereço de ponto de extremidade do <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Se os critérios de correspondência, o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> é retornado ao cliente.  
  
## <a name="findcriteria"></a>FindCriteria  
 O <xref:System.ServiceModel.Discovery.FindCriteria> classe é uma classe independentes de versão usada para especificar os critérios usados ao localizar um serviço. Suporte completo para os critérios definidos para descoberta WS para correspondência de serviços. Ele também tem extensões que os desenvolvedores podem usar para especificar valores personalizados que podem ser usados durante o processo de correspondência. O desenvolvedor pode fornecer os critérios de encerramento para o `Find` operação, especificando o <!--zz <xref:System.ServiceModel.Discovery.FindCriteria.MaxResult%2A>--> `MaxResult`, que especifica o número total de serviços de desenvolvedor está procurando ou que especifica o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, que é o valor que especifica quanto tempo o cliente aguarda para respostas.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 O <xref:System.ServiceModel.Discovery.FindRequestContext> classe é instanciada pelo serviço de descoberta com base no `Probe` mensagem recebida quando um cliente inicia uma `Find` operação. Ele contém uma instância de <xref:System.ServiceModel.Discovery.FindCriteria> que foi especificado pelo cliente.  
  
## <a name="findresponse"></a>FindResponse  
 O <xref:System.ServiceModel.Discovery.FindResponse> classe é retornada ao chamador de <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> com as respostas do `Find` operação. Ele também está presente no <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Ele contém uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, que é a coleção de pontos de extremidade descoberta e um dicionário de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> e <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 O <xref:System.ServiceModel.Discovery.ResolveCriteria> classe é uma classe independentes de versão usada para especificar os critérios usados durante a resolução de um serviço já conhecido. Ele contém o endereço do ponto de extremidade do serviço conhecido. O desenvolvedor pode fornecer os critérios de encerramento para a operação resolver especificando o <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, que especifica quanto tempo o cliente aguarda para respostas.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 O <xref:System.ServiceModel.Discovery.ResolveResponse> é retornado ao chamador do <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> método com a resposta do `Resolve` operação. Ele também está presente no <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Ele contém uma instância de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, que é a extremidade descobertos e uma instância do <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> classe permite que o desenvolvedor adicionar o recurso de descoberta a um serviço. Adicione esse comportamento para o <xref:System.ServiceModel.ServiceHost>. O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> classe itera sobre os pontos de extremidade do aplicativo adicionados para o host de serviço e cria uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> de pontos de extremidade podem ser descobertos. Todos os pontos de extremidade são detectáveis por padrão. A capacidade de descoberta de um ponto de extremidade específico pode ser controlada pela adição de <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> ao ponto de extremidade específico. Se os pontos de extremidade do anúncio forem adicionados ao <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> o anúncio de todos os pontos de extremidade descobertos é enviado em cada um dos pontos de extremidade de aviso quando o host de serviço é aberto ou fechado.  
  
## <a name="servicediscoveryextension"></a>ServiceDiscoveryExtension  
 O <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension` classe é criada pelo <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> classe. Os pontos de extremidade que ficam detectáveis podem ser obtidos <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`. Essa classe também é usada para especificar uma implementação de serviço personalizado de descoberta.  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 O <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> classe é um ponto de extremidade de lançamento padrão que é pré-configurado para aviso sobre um UDP associação multicast. Por padrão, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> está definido para usar a versão de WSApril2005 WS_Discovery.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> classe é um ponto de extremidade de descoberta padrão que é pré-configurado para descoberta por um UDP associação multicast. Por padrão, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> está definido para usar a versão do WS-Discovery WSDiscovery11 e <!--zz <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.Adhoc>--> `Adhoc` modo.
