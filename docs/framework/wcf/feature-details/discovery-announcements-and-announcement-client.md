---
title: Anúncios de descoberta e cliente de anúncio
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 74362343dc1fd5df6d1b91537f7fed5bc08f8fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968824"
---
# <a name="discovery-announcements-and-announcement-client"></a>Anúncios de descoberta e cliente de anúncio
O recurso de descoberta do WCF permite que os componentes anunciem sua disponibilidade. Se estiver configurado para fazer isso, um serviço enviará anúncios de saudação e até mesmo. Clientes ou outros componentes podem escutar essas mensagens de anúncio e agir sobre elas. Isso fornece um método alternativo para que os clientes estejam cientes dos serviços. A funcionalidade de anúncio tem vários usos, por exemplo, se os serviços entram e deixam uma rede com frequência, os anúncios podem ser uma alternativa melhor do que Pesquisar serviços. Com essa abordagem, o tráfego de rede é reduzido e o cliente pode saber mais sobre a presença ou a saída do serviço assim que os anúncios são recebidos.  
  
## <a name="discovery-announcements"></a>Anúncios de descoberta  
 Quando um serviço configurado para anúncios ingressar em uma rede e se tornar detectável, ele enviará uma mensagem de saudação anunciando sua disponibilidade para clientes de escuta. A mensagem contém informações relacionadas à descoberta sobre o serviço, como seu contrato, o endereço do ponto de extremidade e os escopos associados. Você pode especificar onde a mensagem de anúncio é enviada com <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> a classe. Se o ponto de extremidade do <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> comunicado for um, as saudações e as outras são multicast adequadamente, ou se o ponto de extremidade do anúncio for unicast, as mensagens serão enviadas diretamente para o ponto de extremidade especificado.  
  
> [!NOTE]
> Os anúncios são enviados quando o host de serviço abre e fecha. Se essas chamadas não forem concluídas corretamente, a mensagem de anúncio não poderá ser enviada. Por exemplo, se o serviço falhar, a mensagem de anúncio de adeus não será enviada.  
  
> [!TIP]
>  Você pode personalizar a funcionalidade do comunicado, permitindo que você envie anúncios sempre que escolher.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]define o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> e <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> como pontos de extremidade padrão para permitir que serviços e clientes enviem anúncios de saudação e adeus.  
  
### <a name="announcements-on-the-service"></a>Anúncios no serviço  
 Para configurar o serviço para enviar anúncios, adicione um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> com um ponto de extremidade de anúncio. O exemplo a seguir mostra como adicionar esse comportamento programaticamente ao host de serviço. Este exemplo usa o `UdpAnnouncementEndpoint`, que implica que os anúncios são multicast para um local especificado por esse ponto de extremidade padrão.  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 O comportamento também pode ser configurado no arquivo de configuração, conforme mostrado no exemplo a seguir.  
  
```xml  
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
 Os exemplos anteriores configuram um serviço para enviar automaticamente mensagens de comunicado. Você também pode enviar mensagens de anúncio explicitamente usando a <xref:System.ServiceModel.Discovery.AnnouncementClient> classe.  
  
### <a name="announcements-on-the-client"></a>Anúncios no cliente  
 Um aplicativo cliente deve hospedar um serviço de anúncio para responder às mensagens de saudação e de adeus e <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> assinar <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> os eventos e. O exemplo a seguir mostra como fazer isso.  
  
```  
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();
  
// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
  
// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{  
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();
  
    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}  
```  
  
 Quando uma mensagem Hello ou adeus for recebida, você poderá acessar os metadados de descoberta do <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> ponto de extremidade por meio do, conforme mostrado no exemplo a seguir.  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}
```
