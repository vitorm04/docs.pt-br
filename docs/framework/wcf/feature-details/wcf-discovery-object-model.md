---
title: Modelo de objeto de descoberta do WCF
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: b337eda40fc70a6d0e7b3aeccfc125e6e6bacf8f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070871"
---
# <a name="wcf-discovery-object-model"></a>Modelo de objeto de descoberta do WCF
Descoberta do WCF consiste em um conjunto de tipos que fornecem um modelo de programação unificado que permite que você escreva os serviços que são descobertos no tempo de execução e os clientes que localizarem e usam esses serviços.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Tornando um serviço detectável e serviços de localização  
 Para um serviço WCF que podem ser descobertos, adicione uma <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> para o <xref:System.ServiceModel.Description.ServiceDescription> do serviço de host e adicione um ponto de extremidade de descoberta. Se um serviço estiver configurado para enviar mensagens de comunicado (adicionando um <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) o comunicado é enviado quando o host de serviço é aberto e fechado.  
  
 Um cliente que queira escutar mensagens de comunicado de serviço hospeda um serviço de anúncio e adiciona um ou mais pontos de extremidade de comunicado. O serviço de comunicado recebe mensagens de comunicado e gera eventos de lançamento.  
  
 Um cliente usa o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe para procurar serviços disponíveis. O aplicativo cliente instancia o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe, passando em um ponto de extremidade de descoberta que especifica o local enviar mensagens de descoberta. O cliente chama o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método, que envia um `Probe` solicitação. Serviços de escuta para mensagens de descoberta de recebimento isso `Probe` solicitação. Se o serviço corresponder aos critérios especificados na `Probe`, ele envia um `ProbeMatch` mensagem de volta ao cliente.  
  
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
 
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 O <xref:System.ServiceModel.Discovery.AnnouncementClient> classe fornece métodos síncronos e assíncronos para enviar mensagens de comunicado. Há dois tipos de mensagens de comunicado de saudação e até logo. Uma mensagem de saudação é enviada para indicar que um serviço se tornou disponível e uma mensagem Bye é enviada para indicar que um serviço existente se tornou indisponível. O desenvolvedor cria um <xref:System.ServiceModel.Discovery.AnnouncementClient> instância, passando uma instância do <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> como um parâmetro de construtor.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> representa um ponto de extremidade padrão com um contrato de anúncio fixo. Ele é usado por um serviço ou cliente para enviar e receber mensagens de comunicado. Por padrão, o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> classe é definida para usar a versão do protocolo WS_Discovery 11.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService> é uma implementação fornecida pelo sistema de um serviço de anúncio que recebe e processa mensagens de comunicado. Quando uma mensagem de saudação ou Bye é recebida, o <xref:System.ServiceModel.Discovery.AnnouncementService> instância chama o método virtual apropriado <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> ou <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, que gera eventos de lançamento.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 O <xref:System.ServiceModel.Discovery.DiscoveryClient> classe é usada por um aplicativo cliente para localizar e resolver os serviços disponíveis. Ele fornece métodos síncronos e assíncronos para localizar e resolver os serviços com base em especificado <xref:System.ServiceModel.Discovery.FindCriteria> e <xref:System.ServiceModel.Discovery.ResolveCriteria> , respectivamente. O desenvolvedor cria um <xref:System.ServiceModel.Discovery.DiscoveryClient> da instância e fornece uma instância de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> como um parâmetro de construtor.  
  
 Para localizar um serviço, o desenvolvedor invoca síncronas ou assíncronas `Find` método, que fornece um <xref:System.ServiceModel.Discovery.FindCriteria> instância que contém os critérios de pesquisa para usar. O <xref:System.ServiceModel.Discovery.DiscoveryClient> cria um `Probe` mensagem com os cabeçalhos apropriados e envia a solicitação de localização. Como pode haver mais de um excelente `Find` solicitar a qualquer momento, o cliente se correlaciona as respostas recebidas e valida a resposta. Ele oferece, em seguida, os resultados para o chamador do `Find` operação usando <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Para resolver um serviço conhecido, o desenvolvedor invoca síncronas ou assíncronas `Resolve` método que fornece uma instância do <xref:System.ServiceModel.Discovery.ResolveCriteria> que contém o <xref:System.ServiceModel.EndpointAddress> do serviço conhecido. O <xref:System.ServiceModel.Discovery.DiscoveryClient> cria o `Resolve` mensagem com os cabeçalhos apropriados e envia a solicitação de resolução. A resposta recebida é correlacionada com base nas solicitações de resolução pendentes e o resultado é entregue ao chamador do `Resolve` operação usando <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Se um proxy de descoberta está presente na rede e o <xref:System.ServiceModel.Discovery.DiscoveryClient> envia solicitações a descoberta de forma seletiva, o proxy de descoberta pode responder com a mensagem de saudação de supressão multicast. O <xref:System.ServiceModel.Discovery.DiscoveryClient> gera a `ProxyAvailable` eventos quando ele recebe mensagens de saudação em resposta a pendentes `Find` ou `Resolve` solicitações. O `ProxyAvailable` evento contém o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> sobre o proxy de descoberta. Cabe ao desenvolvedor usar essas informações para alternar do Ad hoc para modo gerenciado.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> representa um ponto de extremidade padrão com um contrato de correção da descoberta. Ele é usado por um serviço ou cliente para enviar ou receber mensagens de descoberta. Por padrão, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> está definido para usar <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> modo e a versão de WSDiscovery11 WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator> é usado para gerar um <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> quando o serviço envia mensagens de descoberta ou anúncio.  
  
## <a name="discoveryservice"></a>DiscoveryService  
 O <xref:System.ServiceModel.Discovery.DiscoveryService> classe abstrata fornece uma estrutura para recebimento e processamento `Probe` e `Resolve` mensagens. Quando um `Probe` mensagem é recebida, <xref:System.ServiceModel.Discovery.DiscoveryService> cria uma instância de <xref:System.ServiceModel.Discovery.FindRequestContext> com base na mensagem de entrada e invoca o <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> método virtual. Quando um `Resolve` mensagem é recebida, <xref:System.ServiceModel.Discovery.DiscoveryService> invoca o <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> método virtual. É possível herdar desta classe para fornecer uma implementação personalizada do serviço de descoberta.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 O <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe abstrata fornece uma estrutura para receber e processar mensagens de descoberta e o anúncio. Herdam dessa classe quando você estiver implementando um proxy de descoberta personalizada. Quando um `Probe` mensagem é recebida por meio de multicast, o <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe chamadas a `BeginShouldRedirectFind` método virtual para determinar se uma mensagem de supressão multicast deve ser enviada. Se o desenvolvedor decide por não enviar uma mensagem de supressão multicast ou se o `Probe` mensagem foi recebida em unicast, ele cria uma instância das <xref:System.ServiceModel.Discovery.FindRequestContext> classe com base na mensagem de entrada e invoca o `OnBeginFind` método virtual. Quando um `Resolve` mensagem é recebida por meio de multicast, o <xref:System.ServiceModel.Discovery.DiscoveryProxy> classe chamadas a `ShouldRedirectResolve` método virtual para determinar se uma mensagem de supressão multicast deve ser enviada. Se o desenvolvedor decide por não enviar uma mensagem de supressão multicast ou se o `Resolve` mensagem foi recebida em unicast, ele cria uma instância das <xref:System.ServiceModel.Discovery.ResolveCriteria> classe com base na mensagem de entrada e invoca o `OnBeginResolve` método virtual. Quando é recebida uma mensagem de saudação ou Bye, <xref:System.ServiceModel.Discovery.DiscoveryProxy> chama o método virtual apropriado (`OnBeginOnlineAnnouncement` ou `OnBeingOfflineAnnouncement`), que gera eventos de lançamento.  
  
## <a name="discoveryversion"></a>DiscoveryVersion  
 O <xref:System.ServiceModel.Discovery.DiscoveryVersion> classe representa a versão do protocolo de descoberta para usar.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 O <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> classe é usada para controlar a capacidade de descoberta de um ponto de extremidade, especifique as extensões, nomes de tipo de contrato adicionais. e os escopos associados a esse ponto de extremidade. Esse comportamento é adicionado a um ponto de extremidade do aplicativo para configurar seu <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Quando <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> é adicionado ao host de serviço, todos os aplicativos pontos de extremidade hospedados pelo host de serviço por padrão ser descobertos. O desenvolvedor pode desativar a descoberta para um ponto de extremidade específico definindo o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> propriedade para `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 O <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> classe fornece uma representação independente de versão de um ponto de extremidade publicado pelo serviço. Ele contém os endereços de ponto de extremidade, URIs, nomes de tipo de contrato, escopos, versão de metadados e as extensões especificadas pelo desenvolvedor do serviço de escuta. O <xref:System.ServiceModel.Discovery.FindCriteria> enviado pelo cliente durante uma `Probe` operação é comparada com o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Se os critérios de corresponder, o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> é retornada ao cliente. O endereço do ponto de extremidade na <xref:System.ServiceModel.Discovery.ResolveCriteria> é comparado com o endereço do ponto de extremidade do <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Se os critérios de corresponder, o <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> é retornada ao cliente.  
  
## <a name="findcriteria"></a>FindCriteria  
 O <xref:System.ServiceModel.Discovery.FindCriteria> é uma classe independente de versão usada para especificar os critérios usados quando a localização de um serviço. Ele totalmente compatível com os critérios definidos por WS-Discovery para serviços de correspondência. Ele também tem extensões que os desenvolvedores podem usar para especificar valores personalizados que podem ser usados durante o processo de correspondência. O desenvolvedor pode fornecer os critérios de encerramento para o `Find` operação, especificando as <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>, que especifica o número total de serviços de desenvolvedor está procurando ou que especifica o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, que é o valor que Especifica quanto tempo o cliente aguarda para respostas.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 O <xref:System.ServiceModel.Discovery.FindRequestContext> classe é instanciada pelo serviço de descoberta com base em de `Probe` mensagem recebida quando um cliente inicia uma `Find` operação. Ele contém uma instância de <xref:System.ServiceModel.Discovery.FindCriteria> que foi especificado pelo cliente.  
  
## <a name="findresponse"></a>FindResponse  
 O <xref:System.ServiceModel.Discovery.FindResponse> classe é retornado ao chamador do <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> com as respostas do `Find` operação. Ele também está presente no <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Ele contém uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, que é a coleção de pontos de extremidade de descoberta e um dicionário de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> e <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 O <xref:System.ServiceModel.Discovery.ResolveCriteria> é uma classe independente de versão usada para especificar os critérios usados ao resolver um serviço já conhecido. Ele contém o endereço do ponto de extremidade do serviço conhecido. O desenvolvedor pode fornecer os critérios de encerramento para a operação de resolução, especificando o <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, que especifica quanto tempo o cliente aguarda para respostas.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 O <xref:System.ServiceModel.Discovery.ResolveResponse> é retornado ao chamador do <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> método com a resposta do `Resolve` operação. Ele também está presente no <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Ele contém uma instância do <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, que é descobertos pontos de extremidade e uma instância de <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> classe permite que o desenvolvedor adicione o recurso de descoberta a um serviço. Você adiciona esse comportamento para o <xref:System.ServiceModel.ServiceHost>. O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> classe itera sobre os pontos de extremidade de aplicativo adicionados ao host de serviço e cria uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> dos pontos de extremidade podem ser descoberta. Todos os pontos de extremidade são detectáveis por padrão. A capacidade de descoberta de um determinado ponto de extremidade pode ser controlada adicionando o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> ao ponto de extremidade específico. Se os pontos de extremidade de comunicado são adicionados ao <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e em seguida, o anúncio de todos os pontos de extremidade podem ser descobertos é enviado por cada um dos pontos de extremidade de comunicado quando o host de serviço é aberto ou fechado.  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 O <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> classe é um ponto de extremidade de comunicado padrão que é pré-configurada para o comunicado sobre um UDP multicast de associação. Por padrão, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> está configurado para usar a versão WSApril2005 WS_Discovery.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> classe é um ponto de extremidade de descoberta padrão que é pré-configurado para a descoberta em um UDP multicast de associação. Por padrão, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> está definido para usar a versão do WS-Discovery WSDiscovery11 e <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> modo.
