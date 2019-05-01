---
title: Filtro de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 34e6d851bd0aa3515c5c43521be6213451b7ed12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003061"
---
# <a name="custom-message-filter"></a>Filtro de mensagem personalizado
Este exemplo demonstra como substituir os filtros de mensagem que usa o Windows Communication Foundation (WCF) para enviar mensagens para pontos de extremidade.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Quando a primeira mensagem em um canal chega ao servidor, o servidor deve determinar quais (se houver) dos pontos de extremidade associados a esse URI deve receber a mensagem. Esse processo é controlado pelo <xref:System.ServiceModel.Dispatcher.MessageFilter> objetos anexados para o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Cada ponto de extremidade de serviço tem um único <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> tem um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> e um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. A união entre esses dois filtros é o filtro de mensagem usado para esse ponto de extremidade.  
  
 Por padrão, o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> para um ponto de extremidade corresponde a qualquer mensagem que é endereçada a um endereço que corresponde a um ponto de extremidade de serviço <xref:System.ServiceModel.EndpointAddress>. Por padrão, o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> para um ponto de extremidade inspeciona a ação da mensagem de entrada e corresponde a qualquer mensagem com uma ação que corresponde a uma das ações de operações do contrato do ponto de extremidade de serviço (só `IsInitiating` = `true`ações são consideradas). Como resultado, por padrão, o filtro para um ponto de extremidade corresponde apenas se ambos da mensagem para o cabeçalho é o <xref:System.ServiceModel.EndpointAddress> do ponto de extremidade e a ação da mensagem corresponde a uma das ações da operação de ponto de extremidade.  
  
 Esses filtros podem ser alterados usando um comportamento. No exemplo, o serviço cria um <xref:System.ServiceModel.Description.IEndpointBehavior> que substitui o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> e <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> sobre o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 Dois filtros de endereço são definidos:  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 O `FilteringEndpointBehavior` é feita configurável e permite duas variações diferentes.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 Variação 1 corresponde apenas os endereços que contêm um 'e' (mas que têm qualquer ação), enquanto somente os endereços que não têm um 'e' corresponde a variação 2:  
  
```  
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
  
 Em seguida, o serviço cria `endpointBehavior` configurações para cada variação de:  
  
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
  
 Por fim, o ponto de extremidade do serviço referencia um ou mais o `behaviorConfigurations`:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 A implementação do aplicativo cliente é simples; ele cria dois canais para o URI do serviço (passando esse valor como o segundo (`via`) o parâmetro para <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> e envia uma única mensagem em cada canal, mas usa os endereços de ponto de extremidade diferente para cada um. Como resultado, as mensagens de saída do cliente têm diferentes para designações, e o servidor responde da mesma forma, conforme demonstrado pela saída do cliente:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Alternar a variação no arquivo de configuração do servidor faz com que o filtro a serem trocados e o cliente vê comportamento oposto (a mensagem a ser `urn:e` tiver êxito, enquanto que a mensagem a ser `urn:a` falhar).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de várias máquinas, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) e altere a linha a seguir em Client.cs.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Substitua localhost pelo nome do servidor.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
