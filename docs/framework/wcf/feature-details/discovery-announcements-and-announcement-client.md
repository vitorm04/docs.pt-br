---
title: Anúncios de descoberta e cliente de anúncio
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: c32aca5e6deab01423d61c516ee924d00bc041ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="discovery-announcements-and-announcement-client"></a>Anúncios de descoberta e cliente de anúncio
O recurso de descoberta do WCF permite que os componentes de anunciar a disponibilidade. Se configurado para fazer isso, um serviço envia Hello e Bye anúncios. Os clientes ou outros componentes podem escutar essas mensagens de aviso e agir sobre eles. Isso fornece um método alternativo para os clientes estar ciente dos serviços. Funcionalidade de notificação tem vários usos, por exemplo, se os serviços de entrar e saiam de uma rede com frequência, anúncios podem ser uma alternativa melhor que a pesquisa de serviços. Com essa abordagem, o tráfego de rede é reduzido e o cliente pode aprender sobre a presença ou a saída do serviço, assim como anúncios são recebidos.  
  
## <a name="discovery-announcements"></a>Anúncios de descoberta  
 Quando um serviço configurado para anúncios une uma rede e se torna detectável, ele envia uma mensagem de saudação anunciando sua disponibilidade para clientes de escutando. A mensagem contém informações relacionadas sobre o serviço, como seu contrato, o endereço do ponto de extremidade de descoberta e associados escopos. Você pode especificar onde a mensagem de notificação é enviada com o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> classe. Se o ponto de extremidade de anúncio é um <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> o Hello e Bye são multicast adequadamente, ou se o ponto de extremidade de anúncio é unicast, as mensagens são enviadas diretamente para o ponto de extremidade especificado.  
  
> [!NOTE]
>  Anúncios são enviados quando o host de serviço para abre e fecha. Se essas chamadas não são concluídos corretamente a mensagem de aviso pode não ser enviada. Por exemplo, se o serviço de falhas, em seguida, a mensagem de aviso Bye não é enviada.  
  
> [!TIP]
>  Você pode personalizar a funcionalidade de anúncio, permitindo que você envie anúncios sempre que você escolher.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Define o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> e <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> como pontos de extremidade padrão para permitir que serviços e clientes para enviar facilmente Hello e Bye anúncios.  
  
### <a name="announcements-on-the-service"></a>Anúncios no serviço  
 Para configurar o serviço para enviar anúncios, adicione um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> com um ponto de extremidade de anúncio. O exemplo a seguir mostra como adicionar programaticamente esse comportamento para o host de serviço. Este exemplo usa o `UdpAnnouncementEndpoint`, que significa que os anúncios são multicast para um local especificado por esse ponto de extremidade padrão.  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 O comportamento pode ser configurado no arquivo de configuração bem, conforme mostrado no exemplo a seguir.  
  
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
  
 Os exemplos anteriores configuram um serviço para enviar automaticamente mensagens de aviso. Você também pode enviar mensagens de aviso explicitamente usando o <xref:System.ServiceModel.Discovery.AnnouncementClient> classe.  
  
### <a name="announcements-on-the-client"></a>Anúncios no cliente  
 Um aplicativo cliente deve hospedar um serviço de notificação para responder às mensagens de saudação e Bye e assinar o <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> e <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> eventos. O exemplo a seguir mostra como fazer isso.  
  
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
  
 Quando uma mensagem de saudação ou Bye é recebida, você pode acessar os metadados de descoberta do ponto de extremidade por meio de <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> conforme mostrado no exemplo a seguir.  
  
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
