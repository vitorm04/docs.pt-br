---
title: Filtro de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 896407a218073eba53676baa4bcbd125593c80ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183883"
---
# <a name="custom-message-filter"></a>Filtro de mensagem personalizado
Esta amostra demonstra como substituir os filtros de mensagem que o Windows Communication Foundation (WCF) usa para enviar mensagens para pontos finais.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Quando a primeira mensagem em um canal chega ao servidor, o servidor deve determinar qual (se houver) dos pontos finais associados a esse URI deve receber a mensagem. Este processo é <xref:System.ServiceModel.Dispatcher.MessageFilter> controlado pelos objetos ligados ao <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Cada ponto final de um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>serviço tem um único . O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> tem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>e um . A união desses dois filtros é o filtro de mensagem usado para esse ponto final.  
  
 Por padrão, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> o ponto final corresponde a qualquer mensagem endereçada a <xref:System.ServiceModel.EndpointAddress>um endereço que corresponda ao ponto final do serviço . Por padrão, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> o ponto final inspeciona a ação da mensagem recebida e corresponde a qualquer mensagem com uma ação que `IsInitiating` = `true` corresponda a uma das ações das operações do contrato de ponto final do serviço (apenas ações são consideradas). Como resultado, por padrão, o filtro para um ponto final só corresponde <xref:System.ServiceModel.EndpointAddress> se o cabeçalho da mensagem for o ponto final e a ação da mensagem corresponder a uma das ações da operação de ponto final.  
  
 Esses filtros podem ser alterados usando um comportamento. Na amostra, o serviço <xref:System.ServiceModel.Description.IEndpointBehavior> cria um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> que <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>substitui o e sobre o :  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 Dois filtros de endereço são definidos:  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 O `FilteringEndpointBehavior` é configurável e permite duas variações diferentes.  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 A variação 1 corresponde apenas aos endereços que contenham um 'e' (mas que tenham qualquer Ação), enquanto a Variação 2 corresponde apenas aos endereços que não possuem um 'e':  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 No arquivo de configuração, o serviço registra o novo comportamento:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 Em seguida, `endpointBehavior` o serviço cria configurações para cada variação:  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 Finalmente, o ponto final do serviço `behaviorConfigurations`faz referência a um dos:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 A implementação do aplicativo cliente é simples; ele cria dois canais para o URI do serviço (passando`via`esse valor <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> como o segundo parâmetro ( ) para e envia uma única mensagem em cada canal, mas usa endereços de ponto final diferentes para cada um. Como resultado, as mensagens de saída do cliente têm designações diferentes para, e o servidor responde de acordo, como demonstrado pela saída do cliente:  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 A mudança no arquivo de configuração do servidor faz com que o filtro seja trocado e o cliente veja o comportamento oposto (a mensagem é `urn:e` bem sucedida, enquanto a mensagem falha). `urn:a`  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar a amostra em uma configuração de uma única máquina, siga as instruções em [Executar as amostras da Fundação de Comunicação do Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Para executar a amostra em uma configuração entre máquinas, siga as instruções em [Executar a Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md) e altere a seguinte linha em Client.cs.  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Substitua o host local pelo nome do servidor.  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
