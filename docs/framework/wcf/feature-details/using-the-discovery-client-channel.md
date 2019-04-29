---
title: Usando o canal cliente Discovery
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 298cafe34b20a3644f967acf15f831be5b0b90ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932673"
---
# <a name="using-the-discovery-client-channel"></a>Usando o canal cliente Discovery
Ao escrever um aplicativo de cliente do WCF, você precisa saber o endereço do ponto de extremidade do serviço que você está chamando. Em muitas situações o endereço do ponto de extremidade de um serviço não for conhecido antecipadamente ou o endereço do serviço é alterado ao longo do tempo. O canal cliente Discovery permite que você escreva um aplicativo de cliente do WCF, descrevem o serviço que você deseja chamar, e o canal do cliente automaticamente envia uma solicitação de investigação. Quando um serviço responde, o canal cliente discovery recupera o endereço do ponto de extremidade para o serviço de resposta de investigação e usa-o para chamar o serviço.  
  
## <a name="using-the-discovery-client-channel"></a>Usando o canal cliente Discovery  
 Para usar o canal cliente Discovery, adicione uma instância da <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> para sua pilha de canal do cliente. Como alternativa, você pode usar o <xref:System.ServiceModel.Discovery.DynamicEndpoint> e um <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> é adicionado automaticamente à sua associação se não estiver presente.  
  
> [!CAUTION]
>  É recomendável que o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> é o elemento mais alto à sua pilha de canal do cliente. Qualquer elemento de associação que é adicionado na parte superior da <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Verifique se o <xref:System.ServiceModel.ChannelFactory> ou canal, ele cria não usa o endereço do ponto de extremidade ou `Via` endereço (passado para o `CreateChannel` método) porque elas não podem conter correto endereço.  
  
 O <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> classe contém duas propriedades públicas:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, que é usado para descrever o serviço que você deseja chamar.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> que especifica o ponto de extremidade para enviar mensagens de descoberta para descoberta.  
  
 O <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> propriedade permite que você especifique o contrato de serviço que você está procurando, qualquer necessário URIs de escopo e o número máximo de tempo para tentar abrir o canal. O tipo de contrato é especificado chamando o construtor <xref:System.ServiceModel.Discovery.FindCriteria>. URIs de escopo podem ser adicionados para o <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> propriedade. O <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> propriedade permite que você especifique o número máximo de resultados para o qual o cliente tenta se conectar a. Quando for recebida uma resposta de investigação o cliente tenta abrir o canal usando o endereço do ponto de extremidade da resposta de investigação. Se uma exceção ocorrer, que o cliente passa para a próxima resposta de investigação, esperar por respostas mais ser recebida, se necessário. Ele continua a fazer isso até que o canal é aberto com êxito ou o número máximo de resultados for atingido. Para obter mais informações sobre essas configurações, consulte <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 O <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> propriedade permite que você especifique o ponto de extremidade de descoberta para usar. Normalmente, esse é um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, mas pode ser qualquer ponto de extremidade válido.  
  
 Quando você estiver criando a associação a ser usada para se comunicar com o serviço, você deve ser cuidadoso ao usar a mesma associação exata do serviço. A única diferença é que a associação de cliente tem um <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> no topo da pilha. Se o serviço estiver usando uma das associações fornecidas pelo sistema, crie uma nova <xref:System.ServiceModel.Channels.CustomBinding> e passe a associação fornecida pelo sistema para o <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> construtor. Em seguida, você pode adicionar o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> chamando `Insert` sobre o <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> propriedade.  
  
 Depois de adicionar o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> para sua associação e configurá-lo, você pode criar uma instância da classe de cliente do WCF, abri-lo e chamar seus métodos. O exemplo a seguir usa o canal cliente Discovery para descobrir um serviço WCF que implementa o `ICalculator` classe (usado no tutorial de Introdução ao WCF) e chama seu `Add` método.  
  
```  
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the   
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a>Segurança e o canal cliente Discovery  
 Ao usar o canal cliente discovery, dois pontos de extremidade estão sendo especificados. Um é usado para mensagens de descoberta, geralmente <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, e o outro é o ponto de extremidade do aplicativo. Ao implementar um serviço seguro, é necessário ter cuidado para proteger os pontos de extremidade. Para obter mais informações sobre a segurança, consulte [protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
