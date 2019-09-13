---
title: Filtro de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 30405800cd219f56fcc08b8e8d22f4fe0b907e32
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928696"
---
# <a name="custom-message-filter"></a>Filtro de mensagem personalizado
Este exemplo demonstra como substituir os filtros de mensagem que Windows Communication Foundation (WCF) usa para enviar mensagens para pontos de extremidade.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 Quando a primeira mensagem em um canal chega ao servidor, o servidor deve determinar qual (se houver) os pontos de extremidade associados a esse URI devem receber a mensagem. Esse processo é controlado pelos <xref:System.ServiceModel.Dispatcher.MessageFilter> objetos anexados <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>ao.  
  
 Cada ponto de extremidade de um serviço tem <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>um único. O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> tem um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> e um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. A União desses dois filtros é o filtro de mensagem usado para esse ponto de extremidade.  
  
 Por padrão, o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> para um ponto de extremidade corresponde a qualquer mensagem que seja endereçada a um endereço que corresponda <xref:System.ServiceModel.EndpointAddress>ao ponto de extremidade de serviço. Por padrão, o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> para um ponto de extremidade inspeciona a ação da mensagem de entrada e faz a correspondência de qualquer mensagem com uma ação que corresponda a uma das ações das operações do contrato de ponto `IsInitiating` de extremidade de serviço (somente = `true`as ações são consideradas). Como resultado, por padrão, o filtro para um ponto de extremidade só corresponde se o cabeçalho da mensagem para é o <xref:System.ServiceModel.EndpointAddress> do ponto de extremidade e a ação da mensagem corresponde a uma das ações da operação do ponto de extremidade.  
  
 Esses filtros podem ser alterados usando um comportamento. No exemplo, <xref:System.ServiceModel.Description.IEndpointBehavior> o serviço cria um que substitui o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> e <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> no <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 Dois filtros de endereço são definidos:  
  
```csharp  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 O `FilteringEndpointBehavior` se torna configurável e permite duas variações diferentes.  
  
```csharp  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 A variação 1 corresponde apenas a endereços que contêm um ' e ' (mas que têm qualquer ação), enquanto a variação 2 corresponde apenas a endereços que não têm um ' e ':  
  
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
  
 Em seguida, o `endpointBehavior` serviço cria configurações para cada variação:  
  
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
  
 Por fim, o ponto de extremidade do serviço faz `behaviorConfigurations`referência a um dos:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 A implementação do aplicativo cliente é simples; Ele cria dois canais para o URI do serviço (passando esse valor como o segundo parâmetro (`via`) para <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> e envia uma única mensagem em cada canal, mas usa endereços de ponto de extremidade diferentes para cada um. Como resultado, as mensagens de saída do cliente têm diferentes designações e o servidor responde de acordo, conforme demonstrado pela saída do cliente:  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Alternar a variação no arquivo de configuração do servidor faz com que o filtro seja trocado e o cliente Veja o comportamento oposto (a mensagem `urn:e` a ser bem-sucedida, enquanto a `urn:a` mensagem falha).  
  
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
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Para executar o exemplo em uma configuração entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) e altere a linha a seguir em Client.cs.  
  
    ```csharp  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Substitua localhost pelo nome do servidor.  
  
    ```csharp  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
