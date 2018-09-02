---
title: Visão geral de descoberta do WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 24d758502e360a8368be25c506b8648b12a3eb20
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468333"
---
# <a name="wcf-discovery-overview"></a>Visão geral de descoberta do WCF
As APIs de descoberta fornecem um modelo de programação unificado para a publicação dinâmica e a descoberta de serviços da Web usando o protocolo WS-Discovery. Essas APIs permitem que os serviços publicar em si e os clientes localizem serviços publicados. Depois que um serviço é feito detectável, o serviço tem a capacidade de enviar mensagens de comunicado, bem como ouvir e responder às solicitações de descoberta. Serviços podem ser descobertos podem enviar mensagens de saudação anunciar sua chegada em uma rede e Bye anunciar sua saída de uma rede. Para localizar um serviço, os clientes enviam uma `Probe` solicitação que contém critérios específicos, como o tipo de contrato de serviço, as palavras-chave e o escopo na rede. Serviços de recebem o `Probe` solicitar e determinar se eles correspondem aos critérios. Se corresponder a um serviço, ele responde enviando um `ProbeMatch` mensagem de volta para o cliente com as informações necessárias para contatar o serviço. Os clientes também podem enviar `Resolve` solicitações que lhes permitem encontrar os serviços que podem ter sido alteradas seu endereço de ponto de extremidade. Serviços correspondentes respondem às `Resolve` solicitações enviando um `ResolveMatch` mensagem de volta ao cliente.  
  
## <a name="ad-hoc-and-managed-modes"></a>Modos gerenciados e Ad Hoc  
 A descoberta de API dá suporte a dois modos diferentes: gerenciados e Ad Hoc. No modo gerenciado, há um servidor centralizado chamado um proxy de descoberta que mantém informações sobre os serviços disponíveis. O proxy de descoberta pode ser preenchido com informações sobre os serviços em uma variedade de formas. Por exemplo, os serviços podem enviar mensagens de comunicado durante o início até o proxy de descoberta ou o proxy pode ler os dados de um banco de dados ou um arquivo de configuração para determinar quais serviços estão disponíveis. Como o proxy de descoberta é preenchido completamente é responsabilidade do desenvolvedor. Clientes usam o proxy de descoberta para recuperar informações sobre os serviços disponíveis. Quando um cliente pesquisa um serviço ele envia um `Probe` mensagem para o proxy de descoberta e o proxy determina se qualquer um dos serviços que ele sabe sobre correspondem ao serviço que o cliente está procurando. Se não houver correspondências dos envios de proxy de descoberta uma `ProbeMatch` resposta de volta ao cliente. O cliente pode, em seguida, entre em contato com o serviço diretamente usando as informações de serviço retornadas do proxy. O princípio fundamental por trás de modo gerenciado é que as solicitações de descoberta são enviadas de uma maneira de unicast para uma autoridade, o proxy de descoberta. O .NET Framework contém componentes-chave que permitem que você crie seus próprios proxy. Os clientes e serviços podem localizar o proxy por vários métodos:  
  
-   O proxy pode responder a mensagens ad hoc.  
  
-   O proxy pode enviar uma mensagem de comunicado durante o início do.  
  
-   Os clientes e serviços podem ser gravados para procurar um ponto de extremidade conhecido específico.  
  
 No modo Ad Hoc, não há nenhum servidor centralizado. Todas as mensagens de descoberta, como anúncios de serviço e solicitações de cliente são enviadas de forma seletiva. Por padrão o .NET Framework contém suporte para a descoberta de Ad-Hoc através do protocolo UDP. Por exemplo, se um serviço estiver configurado para enviar um anúncio Hello durante a inicialização, ele envia-lo ao longo de um endereço de multicast, bem conhecido, usando o protocolo UDP. Os clientes precisam ouvir esses anúncios ativamente e processá-las adequadamente. Quando um cliente envia um `Probe` mensagem para um serviço que ela seja enviada pela rede usando um protocolo de multicast. Cada serviço que recebe a solicitação determina se ele corresponde aos critérios de `Probe` da mensagem e responde diretamente ao cliente com um `ProbeMatch` da mensagem se o serviço corresponder aos critérios especificados no `Probe` mensagem.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Benefícios de usar a descoberta do WCF  
 Como a descoberta de WCF é implementada usando o protocolo WS-Discovery é interoperável com outros clientes, serviços e proxies que implementam o WS-Discovery também. Descoberta do WCF baseia-se se as APIs de WCF existente, o que torna mais fácil adicionar a funcionalidade de descoberta para seus serviços e clientes existentes. Descoberta de serviço pode ser facilmente adicionada por meio das definições de configuração do aplicativo. Além disso, a descoberta de WCF também oferece suporte usando o protocolo de descoberta sobre outros transportes como HTTP, sobreposição de nomenclatura e rede ponto a ponto. Descoberta do WCF fornece suporte para um modo gerenciado da operação em que um proxy de descoberta é usado. Isso pode reduzir o tráfego de rede, como as mensagens são enviadas diretamente para o proxy de descoberta em vez de enviar mensagens de multicast para toda a rede. Descoberta do WCF também permite mais flexibilidade ao trabalhar com serviços da Web. Por exemplo, você pode alterar o endereço de um serviço sem precisar reconfigurar o cliente ou o serviço. Quando um cliente deve acessar o serviço, ele pode emitir uma `Probe` da mensagem por meio de um `Find` solicitar e esperar que o serviço responder com seu endereço atual. Descoberta do WCF permite que um cliente procurar por um serviço com base em critérios diferentes, incluindo tipos de contrato, elementos de associação, namespace, escopo e as palavras-chave ou números de versão. Descoberta do WCF permite a descoberta de tempo de design e tempo de execução. Descoberta de adição ao seu aplicativo pode ser usada para habilitar outros cenários, como a tolerância a falhas e a configuração automática.  
  
## <a name="service-publication"></a>Publicação de serviço  
 Para tornar um serviço detectável, um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> deve ser adicionado para o host de serviço e uma descoberta de ponto de extremidade deve ser adicionado para especificar onde escutar as mensagens de descoberta. O exemplo de código a seguir mostra como um serviço auto-hospedado pode ser modificado para torná-lo detectável.  
  
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
  
 Um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância deve ser adicionada a uma descrição de serviço para o serviço seja detectável. Um <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instância deve ser adicionada ao host de serviço para informar o serviço onde escutar solicitações de descoberta. Neste exemplo, uma <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (que é derivado de <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) é adicionada para especificar que o serviço deve escutar para solicitações de descoberta sobre o UDP multicast de transporte. O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é usado para a descoberta de Ad-Hoc, porque todas as mensagens são enviadas de forma seletiva.  
  
## <a name="announcement"></a>Comunicado  
 Por padrão, publicação de serviço não envie mensagens de comunicado. O serviço deve ser configurado para enviar mensagens de comunicado. Isso fornece flexibilidade adicional para gravadores de serviço porque eles podem anunciar o serviço separadamente de ouvir as mensagens de descoberta. Comunicado do serviço também pode ser usado como um mecanismo para registrar os serviços com um proxy de descoberta ou outros registros de serviço. O código a seguir mostra como configurar um serviço para enviar mensagens de comunicado por uma associação de UDP.  
  
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
 Um aplicativo cliente pode usar o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe para localizar os serviços. O desenvolvedor cria uma instância das <xref:System.ServiceModel.Discovery.DiscoveryClient> classe passa em um ponto de extremidade de descoberta que especifica para onde enviar `Probe` ou `Resolve` mensagens. O cliente, em seguida, chama <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> que especifica os critérios de pesquisa dentro de um <xref:System.ServiceModel.Discovery.FindCriteria> instância. Se os serviços correspondentes forem encontrados, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> retorna uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. O código a seguir mostra como chamar o `Find` método e, em seguida, conecte-se a um serviço de descoberta.  
  
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
 Ao usar a segurança em nível de mensagem é necessário especificar uma <xref:System.ServiceModel.EndpointIdentity> sobre o ponto de extremidade de descoberta de serviço e encontrar uma correspondência <xref:System.ServiceModel.EndpointIdentity> no ponto de extremidade de descoberta de cliente. Para obter mais informações sobre a segurança em nível de mensagem, consulte [segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Serviços hospedados de descoberta e Web  
 Para serviços do WCF seja detectável eles devem estar em execução. Os serviços WCF hospedados em IIS ou WAS não são executados até que o IIS / WAS recebe uma mensagem associada para o serviço, portanto, eles não podem ser detectáveis por padrão.  Há duas opções para tornar os serviços hospedados na Web podem ser descobertos:  
  
1.  Use o recurso Auto-Start do Windows Server AppFabric  
  
2.  Usar um proxy de descoberta para se comunicar em nome do serviço  
  
 O Windows Server AppFabric tem um recurso de início automático que permitirá que um serviço a ser iniciado antes de receber todas as mensagens. Com essa Auto-Start definido, um IIS / WAS hospedado serviço pode ser configurado para ser descoberto. Para obter mais informações sobre o Auto-Start recurso, consulte [recurso de início automático do Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=205545). Junto com a ativar o recurso Auto-Start, você deve configurar o serviço para descoberta. Para obter mais informações, consulte [como: programaticamente adicionar capacidade de descoberta para um cliente e serviço do WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery em um arquivo de configuração](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Um proxy de descoberta pode ser usado para comunicar-se em nome do serviço WCF quando o serviço não está em execução. O proxy pode escutar investigação ou resolver mensagens e responder ao cliente. O cliente pode enviar mensagens diretamente para o serviço. Quando o cliente envia uma mensagem para o serviço, ele será instanciado para responder à mensagem. Para obter mais informações sobre como implementar uma descoberta proxy, consulte [implementando um Proxy de descoberta](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
>  Para a descoberta do WCF funcionar corretamente, todas as NICs (controlador de Interface de rede) devem ter apenas 1 endereço IP.
