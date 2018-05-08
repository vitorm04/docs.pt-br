---
title: Usando o NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: a753cca008c7eb9b500afa7f3f3b55b5410522a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-nethttpbinding"></a>Usando o NetHttpBinding
O <xref:System.ServiceModel.NetHttpBinding> é uma associação criada para consumir HTTP ou serviços WebSocket e usa a codificação binária por padrão. O <xref:System.ServiceModel.NetHttpBinding> detectará se tiver sido usado com contrato de solicitação-resposta ou contrato de duplex e alterará seu comportamento para corresponder. Ele usará HTTP para contratos de solicitação-resposta e WebSockets para contratos duplex. Esse comportamento pode ser substituído usando o <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` configuração:  
  
1.  Sempre - isso força o WebSockets a ser usado mesmo para contratos de solicitação-resposta.  
  
2.  Nunca - isso impede que o WebSockets seja usado. Tentar usar um contrato duplex com esta configuração resultará em uma exceção.  
  
3.  WhenDuplex - este é o valor padrão e comporta-se como descrito acima.  
  
 O <xref:System.ServiceModel.NetHttpBinding> oferece suporte a sessões confiáveis no modo HTTP e no modo WebSocket. No modo WebSocket as sessões são fornecidas pelo transporte.  
  
> [!WARNING]
>  Quando usar o <xref:System.ServiceModel.NetHttpBinding> e o TransferMode da associação estiver definido como TransferMode.Streamed, os fluxos grandes podem causar um deadlock e a chamada atingirá o tempo limite. Para solucionar esse problema, envie mensagens menores ou use TransferMode.Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Configurando um serviço para usar NetHttpBinding  
 O <xref:System.ServiceModel.NetHttpBinding> pode ser configurado da mesma maneira que qualquer outra associação. O trecho da configuração a seguir demonstra como configurar um serviço WCF com <xref:System.ServiceModel.NetHttpBinding>.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    <!- ... -->   
  </system.serviceModel>  
```  
  
 O trecho de código a seguir mostra como adicionar o <xref:System.ServiceModel.NetHttpBinding> no código.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>Consulte também  
 [Configurando associações para serviços](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [Associações](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Serviços duplex](../../../../docs/framework/wcf/feature-details/duplex-services.md)
