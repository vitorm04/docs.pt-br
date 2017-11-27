---
title: "Anúncios de descoberta e cliente de anúncio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36003933a9fb49fe4fe4f0b677ee584066d415ac
ms.sourcegitcommit: ea1fd4ff4c36169fc722ef263e24884c5cd431a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2017
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="4bc2c-102">Anúncios de descoberta e cliente de anúncio</span><span class="sxs-lookup"><span data-stu-id="4bc2c-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="4bc2c-103">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recurso permite que os componentes de anunciar a disponibilidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-103">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="4bc2c-104">Se configurado para fazer isso, um serviço envia Hello e Bye anúncios.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="4bc2c-105">Os clientes ou outros componentes podem escutar essas mensagens de aviso e agir sobre eles.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="4bc2c-106">Isso fornece um método alternativo para os clientes estar ciente dos serviços.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="4bc2c-107">Funcionalidade de notificação tem vários usos, por exemplo, se os serviços de entrar e saiam de uma rede com frequência, anúncios podem ser uma alternativa melhor que a pesquisa de serviços.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="4bc2c-108">Com essa abordagem, o tráfego de rede é reduzido e o cliente pode aprender sobre a presença ou a saída do serviço, assim como anúncios são recebidos.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="4bc2c-109">Anúncios de descoberta</span><span class="sxs-lookup"><span data-stu-id="4bc2c-109">Discovery Announcements</span></span>  
 <span data-ttu-id="4bc2c-110">Quando um serviço configurado para anúncios une uma rede e se torna detectável, ele envia uma mensagem de saudação anunciando sua disponibilidade para clientes de escutando.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="4bc2c-111">A mensagem contém informações relacionadas sobre o serviço, como seu contrato, o endereço do ponto de extremidade de descoberta e associados escopos.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="4bc2c-112">Você pode especificar onde a mensagem de notificação é enviada com o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> classe.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="4bc2c-113">Se o ponto de extremidade de anúncio é um <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> o Hello e Bye são multicast adequadamente, ou se o ponto de extremidade de anúncio é unicast, as mensagens são enviadas diretamente para o ponto de extremidade especificado.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bc2c-114">Anúncios são enviados quando o host de serviço para abre e fecha.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="4bc2c-115">Se essas chamadas não são concluídos corretamente a mensagem de aviso pode não ser enviada. Por exemplo, se o serviço de falhas, em seguida, a mensagem de aviso Bye não é enviada.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="4bc2c-116">Você pode personalizar a funcionalidade de anúncio, permitindo que você envie anúncios sempre que você escolher.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="4bc2c-117">Define o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> e <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> como pontos de extremidade padrão para permitir que serviços e clientes para enviar facilmente Hello e Bye anúncios.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-117"> defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="4bc2c-118">Anúncios no serviço</span><span class="sxs-lookup"><span data-stu-id="4bc2c-118">Announcements on the Service</span></span>  
 <span data-ttu-id="4bc2c-119">Para configurar o serviço para enviar anúncios, adicione um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> com um ponto de extremidade de anúncio.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="4bc2c-120">O exemplo a seguir mostra como adicionar programaticamente esse comportamento para o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="4bc2c-121">Este exemplo usa o `UdpAnnouncementEndpoint`, que significa que os anúncios são multicast para um local especificado por esse ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="4bc2c-122">O comportamento pode ser configurado no arquivo de configuração bem, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="4bc2c-123">Os exemplos anteriores configuram um serviço para enviar automaticamente mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="4bc2c-124">Você também pode enviar mensagens de aviso explicitamente usando o <xref:System.ServiceModel.Discovery.AnnouncementClient> classe.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="4bc2c-125">Anúncios no cliente</span><span class="sxs-lookup"><span data-stu-id="4bc2c-125">Announcements on the Client</span></span>  
 <span data-ttu-id="4bc2c-126">Um aplicativo cliente deve hospedar um serviço de notificação para responder às mensagens de saudação e Bye e assinar o <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> e <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> eventos.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="4bc2c-127">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-127">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="4bc2c-128">Quando uma mensagem de saudação ou Bye é recebida, você pode acessar os metadados de descoberta do ponto de extremidade por meio de <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4bc2c-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
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
