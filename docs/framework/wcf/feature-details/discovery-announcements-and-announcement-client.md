---
title: Anúncios de descoberta e cliente de anúncio
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 4ad0b3ea5c257fa3117c426391bd59ad7b560d4f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040177"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="0d705-102">Anúncios de descoberta e cliente de anúncio</span><span class="sxs-lookup"><span data-stu-id="0d705-102">Discovery Announcements and Announcement Client</span></span>

<span data-ttu-id="0d705-103">O recurso de descoberta do WCF permite que os componentes anunciem sua disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="0d705-103">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="0d705-104">Se estiver configurado para fazer isso, um serviço enviará anúncios de saudação e até mesmo.</span><span class="sxs-lookup"><span data-stu-id="0d705-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="0d705-105">Clientes ou outros componentes podem escutar essas mensagens de anúncio e agir sobre elas.</span><span class="sxs-lookup"><span data-stu-id="0d705-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="0d705-106">Isso fornece um método alternativo para que os clientes estejam cientes dos serviços.</span><span class="sxs-lookup"><span data-stu-id="0d705-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="0d705-107">A funcionalidade de anúncio tem vários usos, por exemplo, se os serviços entram e deixam uma rede com frequência, os anúncios podem ser uma alternativa melhor do que Pesquisar serviços.</span><span class="sxs-lookup"><span data-stu-id="0d705-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="0d705-108">Com essa abordagem, o tráfego de rede é reduzido e o cliente pode saber mais sobre a presença ou a saída do serviço assim que os anúncios são recebidos.</span><span class="sxs-lookup"><span data-stu-id="0d705-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>

## <a name="discovery-announcements"></a><span data-ttu-id="0d705-109">Anúncios de descoberta</span><span class="sxs-lookup"><span data-stu-id="0d705-109">Discovery Announcements</span></span>

<span data-ttu-id="0d705-110">Quando um serviço configurado para anúncios ingressar em uma rede e se tornar detectável, ele enviará uma mensagem de saudação anunciando sua disponibilidade para clientes de escuta.</span><span class="sxs-lookup"><span data-stu-id="0d705-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="0d705-111">A mensagem contém informações relacionadas à descoberta sobre o serviço, como seu contrato, o endereço do ponto de extremidade e os escopos associados.</span><span class="sxs-lookup"><span data-stu-id="0d705-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="0d705-112">Você pode especificar onde a mensagem de anúncio é enviada com <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> a classe.</span><span class="sxs-lookup"><span data-stu-id="0d705-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="0d705-113">Se o ponto de extremidade do <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> comunicado for um, as saudações e as outras são multicast adequadamente, ou se o ponto de extremidade do anúncio for unicast, as mensagens serão enviadas diretamente para o ponto de extremidade especificado.</span><span class="sxs-lookup"><span data-stu-id="0d705-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="0d705-114">Os anúncios são enviados quando o host de serviço abre e fecha.</span><span class="sxs-lookup"><span data-stu-id="0d705-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="0d705-115">Se essas chamadas não forem concluídas corretamente, a mensagem de anúncio não poderá ser enviada. Por exemplo, se o serviço falhar, a mensagem de anúncio de adeus não será enviada.</span><span class="sxs-lookup"><span data-stu-id="0d705-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>

> [!TIP]
> <span data-ttu-id="0d705-116">Você pode personalizar a funcionalidade do comunicado, permitindo que você envie anúncios sempre que escolher.</span><span class="sxs-lookup"><span data-stu-id="0d705-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="0d705-117">define o <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> e <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> como pontos de extremidade padrão para permitir que serviços e clientes enviem anúncios de saudação e adeus.</span><span class="sxs-lookup"><span data-stu-id="0d705-117">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>

### <a name="announcements-on-the-service"></a><span data-ttu-id="0d705-118">Anúncios no serviço</span><span class="sxs-lookup"><span data-stu-id="0d705-118">Announcements on the Service</span></span>

<span data-ttu-id="0d705-119">Para configurar o serviço para enviar anúncios, adicione um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> com um ponto de extremidade de anúncio.</span><span class="sxs-lookup"><span data-stu-id="0d705-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="0d705-120">O exemplo a seguir mostra como adicionar esse comportamento programaticamente ao host de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d705-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="0d705-121">Este exemplo usa o `UdpAnnouncementEndpoint`, que implica que os anúncios são multicast para um local especificado por esse ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="0d705-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

<span data-ttu-id="0d705-122">O comportamento também pode ser configurado no arquivo de configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0d705-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>

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

<span data-ttu-id="0d705-123">Os exemplos anteriores configuram um serviço para enviar automaticamente mensagens de comunicado.</span><span class="sxs-lookup"><span data-stu-id="0d705-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="0d705-124">Você também pode enviar mensagens de anúncio explicitamente usando a <xref:System.ServiceModel.Discovery.AnnouncementClient> classe.</span><span class="sxs-lookup"><span data-stu-id="0d705-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>

### <a name="announcements-on-the-client"></a><span data-ttu-id="0d705-125">Anúncios no cliente</span><span class="sxs-lookup"><span data-stu-id="0d705-125">Announcements on the Client</span></span>

<span data-ttu-id="0d705-126">Um aplicativo cliente deve hospedar um serviço de anúncio para responder às mensagens de saudação e de adeus e <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> assinar <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> os eventos e.</span><span class="sxs-lookup"><span data-stu-id="0d705-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="0d705-127">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="0d705-127">The following example shows how to do this.</span></span>

```csharp
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

<span data-ttu-id="0d705-128">Quando uma mensagem Hello ou adeus for recebida, você poderá acessar os metadados de descoberta do <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> ponto de extremidade por meio do, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0d705-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>

```csharp
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
