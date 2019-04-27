---
title: Anúncios de descoberta e cliente de anúncio
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: c32aca5e6deab01423d61c516ee924d00bc041ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856577"
---
# <a name="discovery-announcements-and-announcement-client"></a>Anúncios de descoberta e cliente de anúncio
O recurso de descoberta do WCF permite que componentes anunciaremos sua disponibilidade. Se configurado para fazer isso, um serviço envia anúncios de saudação e até logo. Os clientes ou outros componentes podem escutar essas mensagens de anúncio e agir sobre eles. Isso fornece um método alternativo para os clientes para estar ciente dos serviços. Funcionalidade de comunicado tem vários usos, por exemplo, se os serviços de inserir e saiam de uma rede com frequência, anúncios podem ser uma alternativa melhor que a pesquisa de serviços. Com essa abordagem, o tráfego de rede é reduzido, e o cliente pode aprender sobre a presença ou a saída do serviço assim que os anúncios são recebidos.  
  
## <a name="discovery-announcements"></a>Anúncios de descoberta  
 Quando um serviço configurado para anúncios ingressa em uma rede e se tornará detectável, ele envia uma mensagem de saudação informando sua disponibilidade para clientes de escutando. A mensagem contém informações relacionadas sobre o serviço, como seu contrato, o endereço do ponto de extremidade de descoberta e associados escopos. Você pode especificar onde a mensagem de anúncio é enviada com o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> classe. Se o ponto de extremidade de comunicado um <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> e em seguida, a saudação e Bye são multicast adequadamente, ou se o ponto de extremidade de comunicado é unicast, as mensagens são enviadas diretamente para o ponto de extremidade especificado.  
  
> [!NOTE]
>  Anúncios são enviados quando o host de serviço abre e fecha. Se essas chamadas não forem concluídos corretamente a mensagem de comunicado pode não ser enviada. Por exemplo, se o serviço de falhas, em seguida, a mensagem de comunicado Bye não será enviada.  
  
> [!TIP]
>  Você pode personalizar a funcionalidade de anúncio, permitindo que você envie anúncios sempre que você escolher.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Define o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> e <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> como pontos de extremidade padrão para permitir que serviços e clientes para enviar facilmente anúncios de saudação e até logo.  
  
### <a name="announcements-on-the-service"></a>Anúncios no serviço  
 Para configurar o serviço para enviar comunicados, adicione um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> com um ponto de extremidade de comunicado. O exemplo a seguir mostra como adicionar programaticamente esse comportamento ao host de serviço. Este exemplo usa o `UdpAnnouncementEndpoint`, que significa que os anúncios são multicast para um local especificado por esse ponto de extremidade padrão.  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 O comportamento pode ser configurado no arquivo de configuração e também, conforme mostrado no exemplo a seguir.  
  
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
  
 Os exemplos anteriores configuram um serviço para enviar automaticamente mensagens de comunicado. Você também pode enviar mensagens de comunicado explicitamente usando o <xref:System.ServiceModel.Discovery.AnnouncementClient> classe.  
  
### <a name="announcements-on-the-client"></a>Anúncios no cliente  
 Um aplicativo cliente deve hospedar um serviço de anúncio para responder às mensagens de saudação e Bye e inscrever-se para o <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> e <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> eventos. O exemplo a seguir mostra como fazer isso.  
  
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
