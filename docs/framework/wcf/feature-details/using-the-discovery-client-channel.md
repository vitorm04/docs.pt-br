---
title: Usando o canal cliente Discovery
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 2d9dd68d233541f4d8cb3185adc1023cd5a19de1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184258"
---
# <a name="using-the-discovery-client-channel"></a>Usando o canal cliente Discovery
Ao escrever um aplicativo cliente WCF, você precisa saber o endereço final do serviço que você está chamando. Em muitas situações, o endereço final de um serviço não é conhecido com antecedência ou o endereço do serviço muda ao longo do tempo. O Discovery Client Channel permite que você escreva um aplicativo cliente WCF, descreva o serviço que deseja ligar e o canal do cliente envie automaticamente uma solicitação de teste. Quando um serviço responde, o canal cliente de descoberta recupera o endereço de ponto final para o serviço a partir da resposta do teste e o usa para chamar o serviço.  
  
## <a name="using-the-discovery-client-channel"></a>Usando o canal cliente Discovery  
 Para usar o Discovery Client Channel, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> adicione uma instância da pilha de canais do cliente. Alternativamente, você <xref:System.ServiceModel.Discovery.DynamicEndpoint> pode <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> usar o e a é automaticamente adicionado à sua vinculação, se ainda não estiver presente.  
  
> [!CAUTION]
> Recomenda-se que <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> o elemento seja o mais alto na pilha de canais do cliente. Qualquer elemento de vinculação adicionado <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> em cima <xref:System.ServiceModel.ChannelFactory> do deve certificar-se de que `Via` o ou canal `CreateChannel` que ele cria não usa o endereço ou endereço do ponto final (passado para o método) porque eles podem não conter o endereço correto.  
  
 A <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> classe contém duas propriedades públicas:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, que é usado para descrever o serviço que você deseja chamar.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>que especifica o ponto final da descoberta para enviar mensagens de descoberta.  
  
 A <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> propriedade permite que você especifique o contrato de serviço que você está procurando, quaisquer URIs de escopo necessários e o número máximo de tempo para tentar abrir o canal. O tipo de contrato é especificado ligando para o construtor <xref:System.ServiceModel.Discovery.FindCriteria>. URIs de escopo podem <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> ser adicionados à propriedade. A <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> propriedade permite especificar o número máximo de resultados aos quais o cliente tenta se conectar. Quando uma resposta do teste é recebida, o cliente tenta abrir o canal usando o endereço de ponto final a partir da resposta do teste. Se ocorrer uma exceção, o cliente passa para a próxima resposta do teste, esperando que mais respostas sejam recebidas, se necessário. Ele continua a fazer isso até que o canal seja aberto com sucesso ou o número máximo de resultados seja alcançado. Para obter mais informações sobre essas configurações, consulte <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 A <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> propriedade permite que você especifique o ponto final de descoberta a ser usado. Normalmente este <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>é um , mas pode ser qualquer ponto final válido.  
  
 Quando você está criando a vinculação para usar para se comunicar com o serviço, você deve ter o cuidado de usar exatamente a mesma vinculação que o serviço. A única diferença é que <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> a vinculação do cliente tem um na parte superior da pilha. Se o serviço estiver usando uma das vinculações <xref:System.ServiceModel.Channels.CustomBinding> fornecidas pelo sistema, crie uma <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> nova e passe na vinculação fornecida pelo sistema ao construtor. Então você pode <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> adicionar `Insert` o <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> chamando na propriedade.  
  
 Depois de adicionar <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> o vinculação e configurá-lo, você pode criar uma instância da classe cliente WCF, abri-la e chamar seus métodos. O exemplo a seguir usa o Discovery Client Channel `ICalculator` para descobrir um serviço WCF que implementa a classe (usada no tutorial Do WCF Getting Started) e chama seu `Add` método.  
  
```csharp
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
  
## <a name="security-and-the-discovery-client-channel"></a>Segurança e o Discovery Client Channel  
 Ao usar o canal cliente de descoberta, dois pontos finais estão sendo especificados. Um é usado para mensagens de descoberta, geralmente <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, e o outro é o ponto final do aplicativo. Ao implementar um serviço seguro, deve-se tomar cuidado para garantir ambos os pontos finais. Para obter mais informações sobre segurança, consulte [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
