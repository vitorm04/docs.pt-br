---
title: Visão geral de descoberta do WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 449d54e0dd1948885a7298fb4da46067de3eb9d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184207"
---
# <a name="wcf-discovery-overview"></a>Visão geral de descoberta do WCF
As APIs do Discovery fornecem um modelo de programação unificado para a publicação dinâmica e a descoberta de serviços da Web usando o protocolo WS-Discovery. Essas APIs permitem que os serviços publiquem a si mesmos e aos clientes para encontrar serviços publicados. Uma vez que um serviço é descoberto, o serviço tem a capacidade de enviar mensagens de anúncio, bem como ouvir e responder às solicitações de descoberta. Os serviços descobertos podem enviar mensagens hello para anunciar sua chegada em uma rede e mensagens Te para anunciar sua saída de uma rede. Para encontrar um serviço, `Probe` os clientes enviam uma solicitação que contém critérios específicos, como tipo de contrato de serviço, palavras-chave e escopo na rede. Os serviços recebem a `Probe` solicitação e determinam se correspondem aos critérios. Se um serviço corresponder, ele `ProbeMatch` responde enviando uma mensagem de volta ao cliente com as informações necessárias para entrar em contato com o serviço. Os clientes `Resolve` também podem enviar solicitações que lhes permitam encontrar serviços que possam ter alterado seu endereço de ponto final. Os serviços `Resolve` correspondentes `ResolveMatch` respondem às solicitações enviando uma mensagem de volta ao cliente.  
  
## <a name="ad-hoc-and-managed-modes"></a>Modos Ad-Hoc e Gerenciados  
 A API do Discovery suporta dois modos diferentes: Gerenciado e Ad-Hoc. No modo Gerenciado há um servidor centralizado chamado proxy de detecção que mantém informações sobre serviços disponíveis. O proxy de descoberta pode ser preenchido com informações sobre serviços de várias maneiras. Por exemplo, os serviços podem enviar mensagens de anúncio durante a inicialinicialidade para o proxy de detecção ou o proxy pode ler dados de um banco de dados ou de um arquivo de configuração para determinar quais serviços estão disponíveis. A forma como o proxy de detecção é preenchido depende completamente do desenvolvedor. Os clientes usam o proxy de descoberta para recuperar informações sobre os serviços disponíveis. Quando um cliente procura por `Probe` um serviço, ele envia uma mensagem para o proxy de descoberta e o proxy determina se algum dos serviços que ele conhece corresponde ao serviço que o cliente está procurando. Se houver correspondências, o `ProbeMatch` proxy de descoberta envia uma resposta de volta ao cliente. O cliente pode então entrar em contato diretamente com o serviço usando as informações de serviço devolvidas do proxy. O princípio-chave por trás do modo Gerenciado é que as solicitações de detecção são enviadas de forma unicast para uma autoridade, o proxy de descoberta. O .NET Framework contém componentes-chave que permitem construir seu próprio proxy. Clientes e serviços podem localizar o proxy por vários métodos:  
  
- O proxy pode responder a mensagens ad-hoc.  
  
- O proxy pode enviar uma mensagem de anúncio durante a inicialinicialismo.  
  
- Clientes e serviços podem ser escritos para procurar um ponto final específico e bem conhecido.  
  
 No modo Ad-Hoc, não há servidor centralizado. Todas as mensagens de descoberta, como anúncios de serviços e solicitações de clientes, são enviadas de forma multicast. Por padrão, o .NET Framework contém suporte para detecção de Ad-Hoc sobre o protocolo UDP. Por exemplo, se um serviço estiver configurado para enviar um anúncio Hello na inicialinicial, ele o enviará por um endereço multicast conhecido usando o protocolo UDP. Os clientes têm que ouvir ativamente esses anúncios e processá-los de acordo. Quando um cliente `Probe` envia uma mensagem para um serviço, ele é enviado pela rede usando um protocolo multicast. Cada serviço que recebe a solicitação determina se `Probe` ele corresponde aos critérios da `ProbeMatch` mensagem e responde diretamente ao `Probe` cliente com uma mensagem se o serviço corresponder aos critérios especificados na mensagem.  
  
## <a name="benefits-of-using-wcf-discovery"></a>Benefícios do uso do WCF Discovery  
 Como o WCF Discovery é implementado usando o protocolo WS-Discovery, ele é interoperável com outros clientes, serviços e proxies que implementam o WS-Discovery também. O WCF Discovery é construído sobre as APIs WCF existentes, o que facilita a adição da funcionalidade Discovery aos seus serviços e clientes existentes. A capacidade de descoberta de serviço pode ser facilmente adicionada através das configurações de configuração do aplicativo. Além disso, o WCF Discovery também suporta o uso do protocolo de descoberta em outros transportes, como peer net, nomenclatura de nomes e HTTP. O WCF Discovery oferece suporte para um modo de operação gerenciado onde um proxy de detecção é usado. Isso pode reduzir o tráfego de rede à medida que as mensagens são enviadas diretamente para o proxy de detecção, em vez de enviar mensagens multicast para toda a rede. O WCF Discovery também permite mais flexibilidade ao trabalhar com serviços web. Por exemplo, você pode alterar o endereço de um serviço sem ter que reconfigurar o cliente ou o serviço. Quando um cliente deve acessar o `Probe` serviço, `Find` ele pode emitir uma mensagem através de uma solicitação e esperar que o serviço responda com seu endereço atual. O WCF Discovery permite que um cliente procure por um serviço com base em diferentes critérios, incluindo tipos de contrato, elementos de vinculação, namespace, escopo e palavras-chave ou números de versão. O WCF Discovery permite a descoberta de tempo de execução e de design. Adicionar a detecção ao aplicativo pode ser usado para permitir outros cenários, como tolerância a falhas e configuração automática.  
  
## <a name="service-publication"></a>Publicação do serviço  
 Para tornar um serviço <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> despositivo, um deve ser adicionado ao host de serviço e um ponto final de descoberta deve ser adicionado para especificar onde ouvir mensagens de descoberta. O exemplo de código a seguir mostra como um serviço auto-hospedado pode ser modificado para torná-lo descoberto.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

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
  
 Uma <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instância deve ser adicionada a uma descrição do serviço para que o serviço seja descoberto. Uma <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instância deve ser adicionada ao host de serviço para dizer ao serviço onde ouvir as solicitações de descoberta. Neste exemplo, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a (que é <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>derivado ) é adicionada para especificar que o serviço deve ouvir solicitações de detecção sobre o transporte multicast UDP. O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é usado para a descoberta do Ad-Hoc porque todas as mensagens são enviadas de forma multicast.  
  
## <a name="announcement"></a>Anúncio  
 Por padrão, a publicação do serviço não envia mensagens de anúncio. O serviço deve ser configurado para enviar mensagens de anúncio. Isso fornece flexibilidade adicional para os escritores de serviço, porque eles podem anunciar o serviço separadamente de ouvir mensagens de descoberta. O anúncio do serviço também pode ser usado como um mecanismo para registrar serviços com um proxy de descoberta ou outros registros de serviços. O código a seguir mostra como configurar um serviço para enviar mensagens de anúncio por uma vinculação UDP.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

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
  
## <a name="service-discovery"></a>Descoberta de Serviços  
 Um aplicativo cliente <xref:System.ServiceModel.Discovery.DiscoveryClient> pode usar a classe para encontrar serviços. O desenvolvedor cria uma <xref:System.ServiceModel.Discovery.DiscoveryClient> instância da classe que passa em um `Probe` `Resolve` ponto final de descoberta que especifica para onde enviar ou mensagens. Em seguida, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> o cliente liga <xref:System.ServiceModel.Discovery.FindCriteria> para o que especifica os critérios de pesquisa dentro de uma instância. Se os serviços <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> correspondentes <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>forem encontrados, retorna uma coleção de . O código a seguir `Find` mostra como chamar o método e, em seguida, conectar-se a um serviço descoberto.  
  
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
  
## <a name="discovery-and-message-level-security"></a>Segurança do nível de descoberta e de mensagens  
 Ao usar a segurança do nível <xref:System.ServiceModel.EndpointIdentity> de mensagem, é <xref:System.ServiceModel.EndpointIdentity> necessário especificar um ponto final de detecção de serviço e uma correspondência no ponto final da descoberta do cliente. Para obter mais informações sobre segurança no nível de mensagem, consulte [Segurança de mensagens](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Serviços hospedados em descobertas e web  
 Para que os serviços wcf sejam descobertos, eles devem estar em execução. Os serviços WCF hospedados no IIS ou WAS não são executados até que o IIS/WAS receba uma mensagem vinculada ao serviço, de modo que eles não podem ser descobertos por padrão.  Existem duas opções para tornar os serviços hospedados na Web descobertos:  
  
1. Use o recurso De inicialção automática do Windows Server AppFabric  
  
2. Use um proxy de descoberta para se comunicar em nome do serviço  
  
 O Windows Server AppFabric possui um recurso de Início Automático que permitirá que um serviço seja iniciado antes de receber qualquer mensagem. Com este conjunto De Inicializar automaticamente, um serviço hospedado iIS/WAS pode ser configurado para ser descoberto. Para obter mais informações sobre o recurso De inicialção automática, consulte o [recurso de inicialinicializador automático do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677260(v=azure.10)). Além de ligar o recurso Auto-Start, você deve configurar o serviço para detecção. Para obter mais informações, consulte Como: Adicionar programação a uma descoberta [de serviço wcf e configuração de cliente](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)em um arquivo de[configuração](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Um proxy de descoberta pode ser usado para se comunicar em nome do serviço WCF quando o serviço não está sendo executado. O proxy pode ouvir mensagens de sonda ou resolver e responder ao cliente. O cliente pode então enviar mensagens diretamente para o serviço. Quando o cliente envia uma mensagem para o serviço, ele será instanciado para responder à mensagem. Para obter mais informações sobre a implementação de um proxy de descoberta, [consulte, implementando um Proxy de descoberta](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
> Para que o WCF Discovery funcione corretamente, todos os NICs (Network Interface Controller) devem ter apenas 1 endereço IP.
