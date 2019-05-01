---
title: Exemplo de anúncios
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 895043976fd39ac0057c8dbc1c7daf0394393984
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002749"
---
# <a name="announcements-sample"></a><span data-ttu-id="7b4db-102">Exemplo de anúncios</span><span class="sxs-lookup"><span data-stu-id="7b4db-102">Announcements Sample</span></span>
<span data-ttu-id="7b4db-103">Este exemplo mostra como usar a funcionalidade de lançamento do recurso de descoberta.</span><span class="sxs-lookup"><span data-stu-id="7b4db-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="7b4db-104">Anúncios de permitir que os serviços enviar mensagens de anúncio que contêm metadados sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="7b4db-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="7b4db-105">Por padrão, um anúncio hello é enviado quando o serviço é iniciado e um anúncio bye é enviado quando o serviço é desligado.</span><span class="sxs-lookup"><span data-stu-id="7b4db-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="7b4db-106">Esses anúncios podem ser multicast ou eles podem ser enviados ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="7b4db-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="7b4db-107">Esse exemplo consiste em cliente e o serviço de dois projetos.</span><span class="sxs-lookup"><span data-stu-id="7b4db-107">This sample consists of two projects service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="7b4db-108">Serviço</span><span class="sxs-lookup"><span data-stu-id="7b4db-108">Service</span></span>  
 <span data-ttu-id="7b4db-109">Este projeto contém um serviço de calculadora auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="7b4db-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="7b4db-110">No `Main` método, um host de serviço é criado e um ponto de extremidade de serviço é adicionado a ele.</span><span class="sxs-lookup"><span data-stu-id="7b4db-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="7b4db-111">Em seguida, um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> é criado.</span><span class="sxs-lookup"><span data-stu-id="7b4db-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="7b4db-112">Para habilitar os anúncios, um ponto de extremidade de comunicado deve ser adicionado para o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7b4db-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="7b4db-113">Nesse caso, um ponto de extremidade padrão, usando o UDP multicast é adicionado como o ponto de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="7b4db-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="7b4db-114">Isso transmite os anúncios sobre um endereço conhecido de UDP.</span><span class="sxs-lookup"><span data-stu-id="7b4db-114">This broadcasts the announcements over a well-known UDP address.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="7b4db-115">Cliente</span><span class="sxs-lookup"><span data-stu-id="7b4db-115">Client</span></span>  
 <span data-ttu-id="7b4db-116">Neste projeto, observe que os hosts de cliente um <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="7b4db-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="7b4db-117">Além disso, os dois delegados são registrados com eventos.</span><span class="sxs-lookup"><span data-stu-id="7b4db-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="7b4db-118">Esses eventos determinam o que o cliente faz quando anúncios online e offline são recebidos.</span><span class="sxs-lookup"><span data-stu-id="7b4db-118">These events dictate what the client does when online and offline announcements are received.</span></span>  
  
```csharp
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 <span data-ttu-id="7b4db-119">O `OnOnlineEvent` e `OnOfflineEvent` métodos lidam com as mensagens de comunicado de saudação e bye respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7b4db-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7b4db-120">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="7b4db-120">To use this sample</span></span>  
  
1. <span data-ttu-id="7b4db-121">Este exemplo usa pontos de extremidade HTTP e executar isso URL de exemplo, apropriado ACLs deve ser adicionado ver [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="7b4db-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="7b4db-122">Executando o seguinte comando para um nível de privilégio elevado deve adicionar as ACLs apropriado.</span><span class="sxs-lookup"><span data-stu-id="7b4db-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="7b4db-123">Você talvez queira substituir seu domínio e nome de usuário para os argumentos a seguir, se o comando não funcionar como está.</span><span class="sxs-lookup"><span data-stu-id="7b4db-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="7b4db-124">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="7b4db-124">Build the solution.</span></span>  
  
3. <span data-ttu-id="7b4db-125">Execute o aplicativo client.exe.</span><span class="sxs-lookup"><span data-stu-id="7b4db-125">Run the client.exe application.</span></span>  
  
4. <span data-ttu-id="7b4db-126">Execute o aplicativo service.exe.</span><span class="sxs-lookup"><span data-stu-id="7b4db-126">Run the service.exe application.</span></span> <span data-ttu-id="7b4db-127">Observe que o cliente recebe um comunicado online.</span><span class="sxs-lookup"><span data-stu-id="7b4db-127">Note the client receives an online announcement.</span></span>  
  
5. <span data-ttu-id="7b4db-128">Feche o aplicativo service.exe.</span><span class="sxs-lookup"><span data-stu-id="7b4db-128">Close the service.exe application.</span></span> <span data-ttu-id="7b4db-129">Observe que o cliente recebe um comunicado offline.</span><span class="sxs-lookup"><span data-stu-id="7b4db-129">Note the client receives an offline announcement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b4db-130">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7b4db-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b4db-131">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7b4db-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b4db-132">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7b4db-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b4db-133">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7b4db-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
