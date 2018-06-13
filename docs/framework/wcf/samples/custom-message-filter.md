---
title: Filtro de mensagem personalizado
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: d01fd0d08a7f5d9b12007bc22a26e6f08e006b64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504122"
---
# <a name="custom-message-filter"></a>Filtro de mensagem personalizado
Este exemplo demonstra como substituir os filtros de mensagem que usa o Windows Communication Foundation (WCF) para enviar mensagens a pontos de extremidade.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Quando a primeira mensagem em um canal chega ao servidor, o servidor deve determinar quais (se houver) dos pontos de extremidade associados a esse URI deve receber a mensagem. Esse processo é controlado pelo <xref:System.ServiceModel.Dispatcher.MessageFilter> objetos anexados para o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Cada ponto de extremidade de serviço tem um único <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. O <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> tem um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> e um <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. A união entre esses dois filtros é o filtro de mensagem usado para esse ponto de extremidade.  
  
 Por padrão, o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> para um ponto de extremidade corresponde a qualquer mensagem que é resolvida para um endereço que coincide com o ponto de extremidade de serviço <xref:System.ServiceModel.EndpointAddress>. Por padrão, o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> para um ponto de extremidade inspeciona a ação da mensagem de entrada e faz a correspondência de qualquer mensagem com uma ação que corresponde a uma das ações de operações do contrato do ponto de extremidade de serviço (somente `IsInitiating` = `true`ações são consideradas). Como resultado, por padrão, o filtro para um ponto de extremidade corresponde apenas se os dois da mensagem ao cabeçalho é o <xref:System.ServiceModel.EndpointAddress> de ponto de extremidade e a ação da mensagem corresponde a uma das ações da operação de ponto de extremidade.  
  
 Esses filtros podem ser alterados usando um comportamento. No exemplo, o serviço cria um <xref:System.ServiceModel.Description.IEndpointBehavior> que substitui o <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> e <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> no <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
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
  
 Somente os endereços que contêm um 'e' (mas que possuem qualquer ação) corresponde a variação 1 enquanto somente os endereços que não tenham um 'e' corresponde a variação 2:  
  
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
  
 Em seguida, o serviço cria `endpointBehavior` configurações para cada variação:  
  
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
  
 Por fim, ponto de extremidade do serviço faz referência a um o `behaviorConfigurations`:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 A implementação do aplicativo cliente é simples; ele cria dois canais para URI do serviço (passando esse valor como o segundo (`via`) parâmetro para <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> e envia uma única mensagem em cada canal, mas usa endereços de ponto de extremidade diferente para cada um. Como resultado, as mensagens de saída do cliente têm diferentes para designações, e o servidor responde adequadamente, conforme demonstrado pela saída do cliente:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Alternar a variação no arquivo de configuração do servidor faz com que o filtro a ser trocada e o cliente vê o comportamento oposto (a mensagem `urn:e` for bem-sucedida, enquanto a mensagem `urn:a` falhar).  
  
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) e altere a linha a seguir em Client.cs.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Substitua localhost pelo nome do servidor.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a>Consulte também
