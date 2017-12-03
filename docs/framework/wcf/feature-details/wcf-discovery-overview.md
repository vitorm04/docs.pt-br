---
title: "Visão geral de descoberta do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb9fc13d7facf3bdc3f9da43297a47fd1cf4af65
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="12962-102">Visão geral de descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="12962-102">WCF Discovery Overview</span></span>
<span data-ttu-id="12962-103">As APIs de descoberta fornecem um modelo de programação unificado para a publicação dinâmica e a descoberta de serviços da Web usando o protocolo WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="12962-103">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="12962-104">Essas APIs permitem que os serviços publicar a mesmos e clientes para localizar os serviços publicados.</span><span class="sxs-lookup"><span data-stu-id="12962-104">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="12962-105">Depois que um serviço é feito detectável, o serviço tem a capacidade de enviar mensagens de aviso, bem como ouvir e responder às solicitações de descoberta.</span><span class="sxs-lookup"><span data-stu-id="12962-105">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="12962-106">Serviços detectáveis podem enviar mensagens de saudação de anunciar sua chegada em uma rede e Bye anunciar sua saída de uma rede.</span><span class="sxs-lookup"><span data-stu-id="12962-106">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="12962-107">Para localizar um serviço, os clientes enviam uma `Probe` solicitação que contém critérios específicos, como o tipo de contrato de serviço, as palavras-chave e escopo na rede.</span><span class="sxs-lookup"><span data-stu-id="12962-107">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="12962-108">Serviços de recebem o `Probe` solicitar e determinar se eles correspondem aos critérios.</span><span class="sxs-lookup"><span data-stu-id="12962-108">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="12962-109">Se corresponder a um serviço, ele responde enviando um `ProbeMatch` mensagem de volta para o cliente com as informações necessárias para entrar em contato com o serviço.</span><span class="sxs-lookup"><span data-stu-id="12962-109">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="12962-110">Os clientes também podem enviar `Resolve` solicitações que permita localizar os serviços que alteraram seu endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="12962-110">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="12962-111">Serviços correspondentes respondem às `Resolve` solicitações enviando um `ResolveMatch` mensagem de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="12962-111">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="12962-112">Modos gerenciados e Ad Hoc</span><span class="sxs-lookup"><span data-stu-id="12962-112">Ad-Hoc and Managed Modes</span></span>  
 <span data-ttu-id="12962-113">A API de descoberta oferece suporte a dois modos diferentes: gerenciados e Ad Hoc.</span><span class="sxs-lookup"><span data-stu-id="12962-113">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="12962-114">No modo gerenciado, há um servidor centralizado chamado um proxy de descoberta que mantém informações sobre serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="12962-114">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="12962-115">O proxy de descoberta pode ser populado com informações sobre os serviços em uma variedade de maneiras.</span><span class="sxs-lookup"><span data-stu-id="12962-115">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="12962-116">Por exemplo, serviços podem enviar mensagens de aviso durante a inicialização, até o proxy de descoberta ou o proxy pode ler os dados de um banco de dados ou um arquivo de configuração para determinar quais serviços estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="12962-116">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="12962-117">Como o proxy de descoberta é populado completamente é responsabilidade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="12962-117">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="12962-118">Os clientes usam o proxy de descoberta para recuperar informações sobre serviços disponíveis.</span><span class="sxs-lookup"><span data-stu-id="12962-118">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="12962-119">Quando um cliente procura por um serviço ele envia um `Probe` mensagem para o proxy de descoberta e o proxy determina se qualquer um dos serviços que ele conheça corresponder ao serviço que o cliente está procurando.</span><span class="sxs-lookup"><span data-stu-id="12962-119">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="12962-120">Se não houver correspondências o Descoberta proxy envia um `ProbeMatch` resposta de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="12962-120">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="12962-121">O cliente, em seguida, pode contatar o serviço diretamente usando as informações do serviço retornadas do proxy.</span><span class="sxs-lookup"><span data-stu-id="12962-121">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="12962-122">O modo gerenciado princípio chave é que as solicitações de descoberta são enviadas de forma unicast para uma autoridade, o proxy de descoberta.</span><span class="sxs-lookup"><span data-stu-id="12962-122">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="12962-123">O .NET Framework contém componentes-chave que permitem que você crie seus próprios proxy.</span><span class="sxs-lookup"><span data-stu-id="12962-123">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="12962-124">Clientes e serviços podem localizar o proxy de diversos métodos:</span><span class="sxs-lookup"><span data-stu-id="12962-124">Clients and services can locate the proxy by multiple methods:</span></span>  
  
-   <span data-ttu-id="12962-125">O proxy pode responder a mensagens ad hoc.</span><span class="sxs-lookup"><span data-stu-id="12962-125">The proxy can respond to ad-hoc messages.</span></span>  
  
-   <span data-ttu-id="12962-126">O proxy pode enviar uma mensagem de aviso durante a inicialização do.</span><span class="sxs-lookup"><span data-stu-id="12962-126">The proxy can send an announcement message during start up.</span></span>  
  
-   <span data-ttu-id="12962-127">Os clientes e serviços podem ser gravados para procurar por um ponto de extremidade específico bem conhecido.</span><span class="sxs-lookup"><span data-stu-id="12962-127">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="12962-128">No modo Ad Hoc, não há nenhum servidor centralizado.</span><span class="sxs-lookup"><span data-stu-id="12962-128">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="12962-129">Todas as mensagens de descoberta, como anúncios de serviço e solicitações de cliente são enviadas de forma seletiva.</span><span class="sxs-lookup"><span data-stu-id="12962-129">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="12962-130">Por padrão o .NET Framework contém suporte para a descoberta do Ad-Hoc através do protocolo UDP.</span><span class="sxs-lookup"><span data-stu-id="12962-130">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="12962-131">Por exemplo, se um serviço estiver configurado para enviar um anúncio Olá durante a inicialização, ele envia um endereço de multicast, bem conhecidas, usando o protocolo UDP.</span><span class="sxs-lookup"><span data-stu-id="12962-131">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="12962-132">Os clientes precisam ativamente escutar esses anúncios e processá-las adequadamente.</span><span class="sxs-lookup"><span data-stu-id="12962-132">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="12962-133">Quando um cliente envia um `Probe` mensagem para um serviço que são enviados pela rede usando um protocolo de multicast.</span><span class="sxs-lookup"><span data-stu-id="12962-133">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="12962-134">Cada serviço que recebe a solicitação determina se ele corresponde aos critérios no `Probe` de mensagem e responde diretamente para o cliente com um `ProbeMatch` mensagem se o serviço corresponde aos critérios especificados a `Probe` mensagem.</span><span class="sxs-lookup"><span data-stu-id="12962-134">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="12962-135">Benefícios de usar a descoberta do WCF</span><span class="sxs-lookup"><span data-stu-id="12962-135">Benefits of Using WCF Discovery</span></span>  
 <span data-ttu-id="12962-136">Como a descoberta de WCF é implementada usando o protocolo WS-Discovery é interoperável com outros clientes, serviços e proxies que implementa o WS-Discovery também.</span><span class="sxs-lookup"><span data-stu-id="12962-136">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="12962-137">Descoberta do WCF é construída as APIs existentes do WCF, que torna mais fácil adicionar a funcionalidade de descoberta para seus serviços e clientes existentes.</span><span class="sxs-lookup"><span data-stu-id="12962-137">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="12962-138">Descoberta de serviço pode ser adicionada facilmente por meio de parâmetros de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="12962-138">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="12962-139">Além disso, descoberta de WCF também oferece suporte usando o protocolo de descoberta sobre outros transportes como rede ponto a ponto, sobreposição de nomenclatura e HTTP.</span><span class="sxs-lookup"><span data-stu-id="12962-139">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="12962-140">Descoberta de WCF fornece suporte para um modo de operação onde um proxy de descoberta é usado com gerenciado.</span><span class="sxs-lookup"><span data-stu-id="12962-140">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="12962-141">Isso pode reduzir o tráfego de rede, como as mensagens são enviadas diretamente para o proxy de descoberta em vez de enviar mensagens de multicast para toda a rede.</span><span class="sxs-lookup"><span data-stu-id="12962-141">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="12962-142">Descoberta do WCF também permite mais flexibilidade ao trabalhar com serviços Web.</span><span class="sxs-lookup"><span data-stu-id="12962-142">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="12962-143">Por exemplo, você pode alterar o endereço de um serviço sem precisar reconfigurar o cliente ou o serviço.</span><span class="sxs-lookup"><span data-stu-id="12962-143">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="12962-144">Quando um cliente deve acessar o serviço pode emitir um `Probe` mensagem por meio de um `Find` solicitar e esperar que o serviço responder com seu endereço atual.</span><span class="sxs-lookup"><span data-stu-id="12962-144">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="12962-145">Descoberta de WCF permite que um cliente procurar um serviço com base em critérios diferentes, incluindo tipos de contrato, elementos de associação, namespace, escopo e as palavras-chave ou números de versão.</span><span class="sxs-lookup"><span data-stu-id="12962-145">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="12962-146">Descoberta de WCF permite que a descoberta de tempo de design e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="12962-146">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="12962-147">Descoberta de adição para seu aplicativo pode ser usada para habilitar outros cenários, como a tolerância a falhas e a configuração automática.</span><span class="sxs-lookup"><span data-stu-id="12962-147">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="12962-148">Publicação de serviço</span><span class="sxs-lookup"><span data-stu-id="12962-148">Service Publication</span></span>  
 <span data-ttu-id="12962-149">Para tornar um serviço detectável, um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> devem ser adicionados para o host de serviço e a descoberta de uma ponto de extremidade deve ser adicionado para especificar onde a escutar mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="12962-149">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="12962-150">O exemplo de código a seguir mostra como um serviço auto-hospedado pode ser modificado para torná-lo detectável.</span><span class="sxs-lookup"><span data-stu-id="12962-150">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <span data-ttu-id="12962-151">Um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância deve ser adicionada a uma descrição de serviço para o serviço seja detectável.</span><span class="sxs-lookup"><span data-stu-id="12962-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="12962-152">Um <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instância deve ser adicionada para o host de serviço para indicar onde escutar as solicitações de descoberta de serviço.</span><span class="sxs-lookup"><span data-stu-id="12962-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="12962-153">Neste exemplo, um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (que é derivada de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) é adicionada para especificar que o serviço deve escutar solicitações de descoberta pelo UDP multicast de transporte.</span><span class="sxs-lookup"><span data-stu-id="12962-153">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="12962-154">O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é usado para a descoberta do Ad-Hoc porque todas as mensagens são enviadas de forma seletiva.</span><span class="sxs-lookup"><span data-stu-id="12962-154">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="12962-155">Anúncio</span><span class="sxs-lookup"><span data-stu-id="12962-155">Announcement</span></span>  
 <span data-ttu-id="12962-156">Por padrão, publicação de serviço não envia mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="12962-156">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="12962-157">O serviço deve ser configurado para enviar mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="12962-157">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="12962-158">Isso proporciona flexibilidade adicional para os autores do serviço porque ele podem anunciar o serviço separadamente de escuta de mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="12962-158">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="12962-159">Anúncio de serviço também pode ser usado como um mecanismo para registrar os serviços com um proxy de descoberta ou outros registros de serviço.</span><span class="sxs-lookup"><span data-stu-id="12962-159">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="12962-160">O código a seguir mostra como configurar um serviço para enviar mensagens de aviso sobre uma associação de UDP.</span><span class="sxs-lookup"><span data-stu-id="12962-160">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a><span data-ttu-id="12962-161">Descoberta de serviço</span><span class="sxs-lookup"><span data-stu-id="12962-161">Service Discovery</span></span>  
 <span data-ttu-id="12962-162">Um aplicativo cliente pode usar o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe para localizar serviços.</span><span class="sxs-lookup"><span data-stu-id="12962-162">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="12962-163">O desenvolvedor cria uma instância do <xref:System.ServiceModel.Discovery.DiscoveryClient> classe passa em um ponto de extremidade de descoberta que especifica o local enviar `Probe` ou `Resolve` mensagens.</span><span class="sxs-lookup"><span data-stu-id="12962-163">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="12962-164">O cliente, em seguida, chama <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> que especifica os critérios de pesquisa em um <xref:System.ServiceModel.Discovery.FindCriteria> instância.</span><span class="sxs-lookup"><span data-stu-id="12962-164">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="12962-165">Se os serviços correspondentes forem encontrados, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> retorna uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span><span class="sxs-lookup"><span data-stu-id="12962-165">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="12962-166">O código a seguir mostra como chamar o `Find` método e, em seguida, conecte-se a um serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="12962-166">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService()) 
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =   
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =   
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="12962-167">Descoberta e segurança em nível de mensagem</span><span class="sxs-lookup"><span data-stu-id="12962-167">Discovery and Message Level Security</span></span>  
 <span data-ttu-id="12962-168">Ao usar a segurança em nível de mensagem é necessário especificar um <xref:System.ServiceModel.EndpointIdentity> em uma correspondência e o ponto de extremidade de descoberta de serviço <xref:System.ServiceModel.EndpointIdentity> no ponto de extremidade de descoberta de cliente.</span><span class="sxs-lookup"><span data-stu-id="12962-168">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="12962-169">segurança em nível de mensagem, consulte [segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="12962-169"> message level security, see [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="12962-170">Web e descoberta de serviços hospedados</span><span class="sxs-lookup"><span data-stu-id="12962-170">Discovery and Web Hosted Services</span></span>  
 <span data-ttu-id="12962-171">Para serviços WCF seja detectável eles devem estar em execução.</span><span class="sxs-lookup"><span data-stu-id="12962-171">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="12962-172">Os serviços WCF hospedados em IIS ou o WAS não são executados até que o IIS / WAS recebe uma mensagem associada para o serviço, eles não podem ser descobertos por padrão.</span><span class="sxs-lookup"><span data-stu-id="12962-172">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="12962-173">Há duas opções para tornar os serviços Web hospedados detectável:</span><span class="sxs-lookup"><span data-stu-id="12962-173">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1.  <span data-ttu-id="12962-174">Use o recurso Auto-Start do Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="12962-174">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2.  <span data-ttu-id="12962-175">Usar um proxy de descoberta para se comunicar em nome do serviço</span><span class="sxs-lookup"><span data-stu-id="12962-175">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="12962-176">Windows Server AppFabric tem um recurso de início automático que permitirá que um serviço a ser iniciado antes de receber todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="12962-176">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="12962-177">Com essa Auto-Start definido, um IIS / WAS hospedado serviço pode ser configurado para ser descoberto.</span><span class="sxs-lookup"><span data-stu-id="12962-177">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="12962-178">Consulte o recurso Auto-Start, [recurso Auto-Start do Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=205545).</span><span class="sxs-lookup"><span data-stu-id="12962-178"> the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](http://go.microsoft.com/fwlink/?LinkId=205545).</span></span> <span data-ttu-id="12962-179">Junto com a ativar o recurso Auto-Start, você deve configurar o serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="12962-179">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="12962-180">[Como: adicionar programaticamente a capacidade de descoberta para um serviço WCF e um cliente](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configurando a descoberta em um arquivo de configuração](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="12962-180"> [How to: Programmatically Add Discoverability to a WCF Service and Client](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="12962-181">Um proxy de descoberta pode ser usado para se comunicar em nome do serviço WCF, quando o serviço não está em execução.</span><span class="sxs-lookup"><span data-stu-id="12962-181">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="12962-182">O proxy pode escutar para investigação ou resolver mensagens e responder ao cliente.</span><span class="sxs-lookup"><span data-stu-id="12962-182">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="12962-183">O cliente pode, em seguida, enviar mensagens diretamente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="12962-183">The client can then send messages directly to the service.</span></span> <span data-ttu-id="12962-184">Quando o cliente envia uma mensagem para o serviço que serão instanciado para responder à mensagem.</span><span class="sxs-lookup"><span data-stu-id="12962-184">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="12962-185">Implementando um proxy de descoberta consulte, [implementando um Proxy de descoberta](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="12962-185"> implementing a discovery proxy see, [Implementing a Discovery Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12962-186">Para a descoberta de WCF funcionar corretamente, todas as NICs (controlador de Interface de rede) devem ter apenas 1 endereço IP.</span><span class="sxs-lookup"><span data-stu-id="12962-186">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>
