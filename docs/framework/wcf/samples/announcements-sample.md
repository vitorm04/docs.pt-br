---
title: Exemplo de anúncios
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 1acf51ebe36872424be1e0fdda65a7d18aa737f2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045792"
---
# <a name="announcements-sample"></a><span data-ttu-id="35fa7-102">Exemplo de anúncios</span><span class="sxs-lookup"><span data-stu-id="35fa7-102">Announcements Sample</span></span>

<span data-ttu-id="35fa7-103">Este exemplo mostra como usar a funcionalidade de anúncio do recurso de descoberta.</span><span class="sxs-lookup"><span data-stu-id="35fa7-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="35fa7-104">Os anúncios permitem que os serviços enviem mensagens de comunicado que contêm metadados sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="35fa7-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="35fa7-105">Por padrão, um comunicado de saudação é enviado quando o serviço é iniciado e um comunicado de adeus é enviado quando o serviço é desligado.</span><span class="sxs-lookup"><span data-stu-id="35fa7-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="35fa7-106">Esses comunicados podem ser multicast ou podem ser enviados ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="35fa7-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="35fa7-107">Este exemplo consiste em dois projetos serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="35fa7-107">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="35fa7-108">Serviço</span><span class="sxs-lookup"><span data-stu-id="35fa7-108">Service</span></span>

<span data-ttu-id="35fa7-109">Este projeto contém um serviço de calculadora auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="35fa7-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="35fa7-110">`Main` No método, um host de serviço é criado e um ponto de extremidade de serviço é adicionado a ele.</span><span class="sxs-lookup"><span data-stu-id="35fa7-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="35fa7-111">Em seguida, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> um é criado.</span><span class="sxs-lookup"><span data-stu-id="35fa7-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="35fa7-112">Para habilitar anúncios, um ponto de extremidade de anúncio deve ser adicionado <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>ao.</span><span class="sxs-lookup"><span data-stu-id="35fa7-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="35fa7-113">Nesse caso, um ponto de extremidade padrão, usando o multicast UDP, é adicionado como o ponto de extremidade do anúncio.</span><span class="sxs-lookup"><span data-stu-id="35fa7-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="35fa7-114">Isso transmite os anúncios por um endereço UDP conhecido.</span><span class="sxs-lookup"><span data-stu-id="35fa7-114">This broadcasts the announcements over a well-known UDP address.</span></span>

```csharp
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);

     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();

     // Announce the availability of the service over UDP multicast
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());

    // Make the service discoverable over UDP multicast.
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());
    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="35fa7-115">Cliente</span><span class="sxs-lookup"><span data-stu-id="35fa7-115">Client</span></span>

<span data-ttu-id="35fa7-116">Neste projeto, observe que o cliente hospeda um <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="35fa7-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="35fa7-117">Além disso, dois delegados são registrados com eventos.</span><span class="sxs-lookup"><span data-stu-id="35fa7-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="35fa7-118">Esses eventos ditam o que o cliente faz quando anúncios online e offline são recebidos.</span><span class="sxs-lookup"><span data-stu-id="35fa7-118">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="35fa7-119">Os `OnOnlineEvent` métodos `OnOfflineEvent` e lidam com as mensagens de anúncio de saudação e adeus, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="35fa7-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="35fa7-120">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="35fa7-120">To use this sample</span></span>

1. <span data-ttu-id="35fa7-121">Este exemplo usa pontos de extremidade HTTP e para executar esse exemplo, as ACLs de URL adequadas devem ser adicionadas consulte Configurando [http e HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="35fa7-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="35fa7-122">A execução do comando a seguir em um privilégio elevado deve adicionar as ACLs apropriadas.</span><span class="sxs-lookup"><span data-stu-id="35fa7-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="35fa7-123">Talvez você queira substituir seu domínio e nome de usuário pelos argumentos a seguir se o comando não funcionar como está.</span><span class="sxs-lookup"><span data-stu-id="35fa7-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="35fa7-124">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="35fa7-124">Build the solution.</span></span>

3. <span data-ttu-id="35fa7-125">Execute o aplicativo Client. exe.</span><span class="sxs-lookup"><span data-stu-id="35fa7-125">Run the client.exe application.</span></span>

4. <span data-ttu-id="35fa7-126">Execute o aplicativo Service. exe.</span><span class="sxs-lookup"><span data-stu-id="35fa7-126">Run the service.exe application.</span></span> <span data-ttu-id="35fa7-127">Observação o cliente recebe um comunicado online.</span><span class="sxs-lookup"><span data-stu-id="35fa7-127">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="35fa7-128">Feche o aplicativo Service. exe.</span><span class="sxs-lookup"><span data-stu-id="35fa7-128">Close the service.exe application.</span></span> <span data-ttu-id="35fa7-129">Observação o cliente recebe um anúncio offline.</span><span class="sxs-lookup"><span data-stu-id="35fa7-129">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35fa7-130">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="35fa7-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="35fa7-131">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="35fa7-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="35fa7-132">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="35fa7-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="35fa7-133">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="35fa7-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
