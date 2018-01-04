---
title: Usando o canal cliente Discovery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11d693e35017d7290e1cf1209dc3d6423afc38b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-discovery-client-channel"></a>Usando o canal cliente Discovery
Ao escrever um aplicativo cliente WCF que você precisa saber o endereço do ponto de extremidade do serviço que você está chamando. Em muitas situações o endereço do ponto de extremidade de serviço não for conhecido antecipadamente ou o endereço do serviço de alterações ao longo do tempo. O canal cliente Discovery permite que você escrever um aplicativo de cliente do WCF, descreva o serviço que você deseja chamar e o canal cliente envia uma solicitação de investigação automaticamente. Quando um serviço responde, o canal cliente discovery recupera o endereço de ponto de extremidade para o serviço da resposta de investigação e as usa para chamar o serviço.  
  
## <a name="using-the-discovery-client-channel"></a>Usando o canal cliente Discovery  
 Para usar o canal cliente Discovery, adicione uma instância do <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> para a pilha de canais do cliente. Como alternativa, você pode usar o <xref:System.ServiceModel.Discovery.DynamicEndpoint> e um <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> é adicionado automaticamente à sua associação se não estiverem presentes.  
  
> [!CAUTION]
>  É recomendável que o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> é o elemento mais alto em sua pilha de canais do cliente. Qualquer elemento de associação que é adicionado na parte superior do <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> deve assegurar que o <xref:System.ServiceModel.ChannelFactory> ou canal cria não usa o endereço de ponto de extremidade ou `Via` endereço (passado para o `CreateChannel` método) porque elas não podem conter o correto endereço.  
  
 O <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> classe contém duas propriedades públicas:  
  
1.  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, que é usado para descrever o serviço que você deseja chamar.  
  
2.  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>que especifica o ponto de extremidade para enviar mensagens de descoberta para descoberta.  
  
 O <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> propriedade permite que você especifique o contrato de serviço que você está procurando, qualquer necessário URIs de escopo e o número máximo de tempo para tentar abrir o canal. O tipo de contrato é especificado chamando o construtor <xref:System.ServiceModel.Discovery.FindCriteria>. URIs de escopo podem ser adicionados para o <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> propriedade. O <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> propriedade permite que você especifique o número máximo de resultados para o qual o cliente tenta se conectar ao. Quando é recebida uma resposta de investigação o cliente tenta abrir o canal usando o endereço de ponto de extremidade da resposta de investigação. Se uma exceção ocorrer, que o cliente passa para a próxima resposta de investigação, aguardando respostas mais ser recebidas se necessário. Ela continua a fazer isso até que o canal é aberto com êxito ou o número máximo de resultados for atingido. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Essas configurações, consulte <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 O <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> propriedade permite que você especifique o ponto de extremidade de descoberta para usar. Geralmente, isso é um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, mas pode ser qualquer ponto de extremidade válido.  
  
 Ao criar a associação a ser usada para se comunicar com o serviço, você deve ter cuidado ao usar a mesma associação exata do serviço. A única diferença é que a ligação do cliente tem um <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> na parte superior da pilha. Se o serviço estiver usando uma das associações fornecidas pelo sistema, crie um novo <xref:System.ServiceModel.Channels.CustomBinding> e passar a associação fornecida pelo sistema para o <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> construtor. Em seguida, você pode adicionar o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> chamando `Insert` no <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> propriedade.  
  
 Depois que você adicionou o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> à sua associação e configurado, você pode criar uma instância da classe do cliente WCF, abri-lo e chamar seus métodos. O exemplo a seguir usa o canal cliente Discovery para descobrir um serviço WCF que implementa o `ICalculator` classe (usado no tutorial guia de Introdução WCF) e chama seu `Add` método.  
  
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
 Ao usar o canal cliente discovery, dois pontos de extremidade estão sendo especificados. Um é usado para mensagens de descoberta, geralmente <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, e o outro é o ponto de extremidade do aplicativo. Ao implementar um serviço seguro, deve ter cuidado para proteger os pontos de extremidade. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]segurança, consulte [protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
