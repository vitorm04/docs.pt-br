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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1afd3d94ceb3389a7d87528371925120f3c92764
ms.sourcegitcommit: e99dfadbca1992c187179b6a3b42bef44534ebb6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2017
---
# <a name="wcf-discovery-overview"></a>Visão geral de descoberta do WCF
As APIs de descoberta fornecem um modelo de programação unificado para a publicação dinâmica e a descoberta de serviços da Web usando o protocolo WS-Discovery. Essas APIs permitem que os serviços publicar a mesmos e clientes para localizar os serviços publicados. Depois que um serviço é feito detectável, o serviço tem a capacidade de enviar mensagens de aviso, bem como ouvir e responder às solicitações de descoberta. Serviços detectáveis podem enviar mensagens de saudação de anunciar sua chegada em uma rede e Bye anunciar sua saída de uma rede. Para localizar um serviço, os clientes enviam uma `Probe` solicitação que contém critérios específicos, como o tipo de contrato de serviço, as palavras-chave e escopo na rede. Serviços de recebem o `Probe` solicitar e determinar se eles correspondem aos critérios. Se corresponder a um serviço, ele responde enviando um `ProbeMatch` mensagem de volta para o cliente com as informações necessárias para entrar em contato com o serviço. Os clientes também podem enviar `Resolve` solicitações que permita localizar os serviços que alteraram seu endereço de ponto de extremidade. Serviços correspondentes respondem às `Resolve` solicitações enviando um `ResolveMatch` mensagem de volta ao cliente.  
  
## <a name="ad-hoc-and-managed-modes"></a>Modos gerenciados e Ad Hoc  
 A API de descoberta oferece suporte a dois modos diferentes: gerenciados e Ad Hoc. No modo gerenciado, há um servidor centralizado chamado um proxy de descoberta que mantém informações sobre serviços disponíveis. O proxy de descoberta pode ser populado com informações sobre os serviços em uma variedade de maneiras. Por exemplo, serviços podem enviar mensagens de aviso durante a inicialização, até o proxy de descoberta ou o proxy pode ler os dados de um banco de dados ou um arquivo de configuração para determinar quais serviços estão disponíveis. Como o proxy de descoberta é populado completamente é responsabilidade do desenvolvedor. Os clientes usam o proxy de descoberta para recuperar informações sobre serviços disponíveis. Quando um cliente procura por um serviço ele envia um `Probe` mensagem para o proxy de descoberta e o proxy determina se qualquer um dos serviços que ele conheça corresponder ao serviço que o cliente está procurando. Se não houver correspondências o Descoberta proxy envia um `ProbeMatch` resposta de volta ao cliente. O cliente, em seguida, pode contatar o serviço diretamente usando as informações do serviço retornadas do proxy. O modo gerenciado princípio chave é que as solicitações de descoberta são enviadas de forma unicast para uma autoridade, o proxy de descoberta. O .NET Framework contém componentes-chave que permitem que você crie seus próprios proxy. Clientes e serviços podem localizar o proxy de diversos métodos:  
  
-   O proxy pode responder a mensagens ad hoc.  
  
-   O proxy pode enviar uma mensagem de aviso durante a inicialização do.  
  
-   Os clientes e serviços podem ser gravados para procurar por um ponto de extremidade específico bem conhecido.  
  
 No modo Ad Hoc, não há nenhum servidor centralizado. Todas as mensagens de descoberta, como anúncios de serviço e solicitações de cliente são enviadas de forma seletiva. Por padrão o .NET Framework contém suporte para a descoberta do Ad-Hoc através do protocolo UDP. Por exemplo, se um serviço estiver configurado para enviar um anúncio Olá durante a inicialização, ele envia um endereço de multicast, bem conhecidas, usando o protocolo UDP. Os clientes precisam ativamente escutar esses anúncios e processá-las adequadamente. Quando um cliente envia um `Probe` mensagem para um serviço que são enviados pela rede usando um protocolo de multicast. Cada serviço que recebe a solicitação determina se ele corresponde aos critérios no `Probe` de mensagem e responde diretamente para o cliente com um `ProbeMatch` mensagem se o serviço corresponde aos critérios especificados a `Probe` mensagem.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Benefícios de usar a descoberta do WCF  
 Como a descoberta de WCF é implementada usando o protocolo WS-Discovery é interoperável com outros clientes, serviços e proxies que implementa o WS-Discovery também. Descoberta do WCF é construída as APIs existentes do WCF, que torna mais fácil adicionar a funcionalidade de descoberta para seus serviços e clientes existentes. Descoberta de serviço pode ser adicionada facilmente por meio de parâmetros de configuração do aplicativo. Além disso, descoberta de WCF também oferece suporte usando o protocolo de descoberta sobre outros transportes como rede ponto a ponto, sobreposição de nomenclatura e HTTP. Descoberta de WCF fornece suporte para um modo de operação onde um proxy de descoberta é usado com gerenciado. Isso pode reduzir o tráfego de rede, como as mensagens são enviadas diretamente para o proxy de descoberta em vez de enviar mensagens de multicast para toda a rede. Descoberta do WCF também permite mais flexibilidade ao trabalhar com serviços Web. Por exemplo, você pode alterar o endereço de um serviço sem precisar reconfigurar o cliente ou o serviço. Quando um cliente deve acessar o serviço pode emitir um `Probe` mensagem por meio de um `Find` solicitar e esperar que o serviço responder com seu endereço atual. Descoberta de WCF permite que um cliente procurar um serviço com base em critérios diferentes, incluindo tipos de contrato, elementos de associação, namespace, escopo e as palavras-chave ou números de versão. Descoberta de WCF permite que a descoberta de tempo de design e tempo de execução. Descoberta de adição para seu aplicativo pode ser usada para habilitar outros cenários, como a tolerância a falhas e a configuração automática.  
  
## <a name="service-publication"></a>Publicação de serviço  
 Para tornar um serviço detectável, um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> devem ser adicionados para o host de serviço e a descoberta de uma ponto de extremidade deve ser adicionado para especificar onde a escutar mensagens de descoberta. O exemplo de código a seguir mostra como um serviço auto-hospedado pode ser modificado para torná-lo detectável.  
  
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
  
 Um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância deve ser adicionada a uma descrição de serviço para o serviço seja detectável. Um <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instância deve ser adicionada para o host de serviço para indicar onde escutar as solicitações de descoberta de serviço. Neste exemplo, um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (que é derivada de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) é adicionada para especificar que o serviço deve escutar solicitações de descoberta pelo UDP multicast de transporte. O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é usado para a descoberta do Ad-Hoc porque todas as mensagens são enviadas de forma seletiva.  
  
## <a name="announcement"></a>Anúncio  
 Por padrão, publicação de serviço não envia mensagens de aviso. O serviço deve ser configurado para enviar mensagens de aviso. Isso proporciona flexibilidade adicional para os autores do serviço porque ele podem anunciar o serviço separadamente de escuta de mensagens de descoberta. Anúncio de serviço também pode ser usado como um mecanismo para registrar os serviços com um proxy de descoberta ou outros registros de serviço. O código a seguir mostra como configurar um serviço para enviar mensagens de aviso sobre uma associação de UDP.  
  
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
  
## <a name="service-discovery"></a>Descoberta de serviço  
 Um aplicativo cliente pode usar o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe para localizar serviços. O desenvolvedor cria uma instância do <xref:System.ServiceModel.Discovery.DiscoveryClient> classe passa em um ponto de extremidade de descoberta que especifica o local enviar `Probe` ou `Resolve` mensagens. O cliente, em seguida, chama <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> que especifica os critérios de pesquisa em um <xref:System.ServiceModel.Discovery.FindCriteria> instância. Se os serviços correspondentes forem encontrados, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> retorna uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. O código a seguir mostra como chamar o `Find` método e, em seguida, conecte-se a um serviço de descoberta.  
  
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
  
## <a name="discovery-and-message-level-security"></a>Descoberta e segurança em nível de mensagem  
 Ao usar a segurança em nível de mensagem é necessário especificar um <xref:System.ServiceModel.EndpointIdentity> em uma correspondência e o ponto de extremidade de descoberta de serviço <xref:System.ServiceModel.EndpointIdentity> no ponto de extremidade de descoberta de cliente. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]segurança em nível de mensagem, consulte [segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Web e descoberta de serviços hospedados  
 Para serviços WCF seja detectável eles devem estar em execução. Os serviços WCF hospedados em IIS ou o WAS não são executados até que o IIS / WAS recebe uma mensagem associada para o serviço, eles não podem ser descobertos por padrão.  Há duas opções para tornar os serviços Web hospedados detectável:  
  
1.  Use o recurso Auto-Start do Windows Server AppFabric  
  
2.  Usar um proxy de descoberta para se comunicar em nome do serviço  
  
 Windows Server AppFabric tem um recurso de início automático que permitirá que um serviço a ser iniciado antes de receber todas as mensagens. Com essa Auto-Start definido, um IIS / WAS hospedado serviço pode ser configurado para ser descoberto. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Consulte o recurso Auto-Start, [recurso Auto-Start do Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=205545). Junto com a ativar o recurso Auto-Start, você deve configurar o serviço de descoberta. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Como: adicionar programaticamente a capacidade de descoberta para um serviço WCF e um cliente](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configurando a descoberta em um arquivo de configuração](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Um proxy de descoberta pode ser usado para se comunicar em nome do serviço WCF, quando o serviço não está em execução. O proxy pode escutar para investigação ou resolver mensagens e responder ao cliente. O cliente pode, em seguida, enviar mensagens diretamente para o serviço. Quando o cliente envia uma mensagem para o serviço que serão instanciado para responder à mensagem. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Implementando um proxy de descoberta consulte, [implementando um Proxy de descoberta](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
>  Para a descoberta de WCF funcionar corretamente, todas as NICs (controlador de Interface de rede) devem ter apenas 1 endereço IP.
