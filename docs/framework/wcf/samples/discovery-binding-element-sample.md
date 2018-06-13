---
title: Amostra do elemento de associação de descoberta
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: 853f5cebfd745b3413d605dcfbf0e395e103b4f1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805662"
---
# <a name="discovery-binding-element-sample"></a>Amostra do elemento de associação de descoberta
Este exemplo demonstra como usar o elemento de associação de cliente de descoberta para descobrir um serviço. Esse recurso permite aos desenvolvedores adicionar um canal de cliente de descoberta para sua pilha de canais de cliente existente, tornando o modelo de programação muito intuitiva. Quando o canal associado é aberto, o endereço do serviço é resolvido usando a descoberta. Este exemplo consiste nas seguintes projetos:  
  
-   **CalculatorService**: um serviço WCF detectável.  
  
-   **CalculatorClient**: aplicativo de cliente de um WCF que usa o canal cliente discovery para pesquisar e chamar o CalculatorService.  
  
-   **DynamicCalculatorClient**: aplicativo de cliente de um WCF que usa um ponto de extremidade dinâmico para pesquisar e chamar o CalculatorService.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 Este projeto contém um serviço de cálculo simples que implementa o `ICalculatorService` contrato.  
  
 O seguinte arquivo App. config é usado para adicionar um `<serviceDiscovery>` comportamento os comportamentos de serviço, bem como o ponto de extremidade de descoberta.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 Isso torna o serviço e seus pontos de extremidade podem ser descobertos. O CalculatorService é um serviço auto-hospedado que adiciona um ponto de extremidade usando a associação de NetTcpBinding. Ele também adiciona uma `EndpointDiscoveryBehavior` ao ponto de extremidade e especifica um escopo, conforme mostrado no código a seguir.  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 Este projeto contém uma implementação de cliente que envia mensagens para o CalculatorService. Esse programa usa a `CreateCustomBindingWithDiscoveryElement()` método para criar uma associação personalizada que usa o canal cliente Discovery.  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 Após o <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> é instanciada, o desenvolvedor Especifica os critérios para usar ao pesquisar para um serviço. Nesse caso, o critério de localização de descoberta é o `ICalculatorService` tipo. Além disso, o desenvolvedor Especifica um <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> que retorna um <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> que especifica onde procurar os serviços. O <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> retorna um novo <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instância. Para obter mais informações, consulte [usando uma associação personalizada com o canal cliente Discovery](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 Nesse caso, o cliente usa o protocolo UDP multicast mecanismo definido pelo protocolo de descoberta para procurar serviços na sub-rede local. O restante do método cria uma associação personalizada e insere o elemento de associação de descoberta na parte superior da pilha.  
  
> [!NOTE]
>  O <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> devem ser colocados na parte superior da pilha de associação. Qualquer <xref:System.ServiceModel.Channels.BindingElement> na parte superior do <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> deve certificar-se de que a fábrica de canais ou o canal cria não usa o `EndpointAddress` ou `Via` propriedades, porque o endereço real é encontrado apenas no canal cliente Discovery.  
  
 Em seguida, o `CalculatorClient` pode ser instanciado, passando essa associação personalizada, bem como um endereço de ponto de extremidade.  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 Ao usar o canal cliente Discovery, o endereço de constante de ponto de extremidade especificado anteriormente é passado. Agora em tempo de execução, o canal cliente Discovery localiza o serviço especificado pelos critérios de localização e se conectará a ele. Para o serviço e o cliente para estabelecer uma conexão, eles também devem ter a mesma pilha de associação subjacente.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Compile a solução.  
  
3.  Execute o aplicativo de serviço e cada cliente de aplicativos.  
  
4.  Observe que o cliente foi capaz de encontrar o serviço sem saber o endereço.  
  
## <a name="see-also"></a>Consulte também
