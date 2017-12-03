---
title: "Serviços de duplex"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5c7cb9d963e56c6a6e06421afdb14427440643c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="duplex-services"></a>Serviços de duplex
Um contrato de serviço duplex é um padrão de troca de mensagem no qual os pontos de extremidade podem enviar mensagens para o outro independentemente. Um serviço duplex, portanto, pode enviar mensagens para o ponto de extremidade do cliente, fornecendo o comportamento do tipo de evento. Comunicação duplex ocorre quando um cliente se conecta a um serviço e fornece o serviço com um canal em que o serviço pode enviar mensagens de volta ao cliente. Observe que o comportamento do tipo de evento de serviços duplex só funciona em uma sessão.  
  
 Para criar um contrato duplex você criar um par de interfaces. A primeira é a interface de contrato de serviço que descreve as operações que um cliente pode invocar. Esse contrato de serviço deve especificar um *contrato de retorno de chamada* no <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> propriedade. O contrato de retorno de chamada é a interface que define as operações que o serviço pode chamar o ponto de extremidade do cliente. Um contrato duplex não requer uma sessão, embora as associações de duplex fornecido pelo sistema fazer utilizá-las.  
  
 Este é um exemplo de um contrato duplex.  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 O `CalculatorService` classe implementa primário `ICalculatorDuplex` interface. O serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o resultado para cada sessão. Uma propriedade privada denominada `Callback` acessa o canal de retorno de chamada para o cliente. O serviço usa o retorno de chamada para enviar mensagens ao cliente por meio da interface de retorno de chamada, conforme mostrado no código de exemplo a seguir.  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 O cliente deve fornecer uma classe que implementa a interface de retorno de chamada do contrato duplex, para receber mensagens do serviço. O exemplo a seguir mostra código um `CallbackHandler` classe que implementa o `ICalculatorDuplexCallback` interface.  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente que é gerado para um contrato duplex requer um <xref:System.ServiceModel.InstanceContext> classe será fornecido após a construção. Isso <xref:System.ServiceModel.InstanceContext> classe é usada como o site para um objeto que implementa a interface de retorno de chamada e manipula mensagens que são enviadas de volta do serviço. Um <xref:System.ServiceModel.InstanceContext> classe é construída com uma instância do `CallbackHandler` classe. Esse objeto manipula mensagens enviadas do serviço para o cliente na interface de retorno de chamada.  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 A configuração para o serviço deve configurar para fornecer uma associação que dá suporte à comunicação de sessão e comunicação duplex. O `wsDualHttpBinding` elemento dá suporte à comunicação de sessão e permite a comunicação duplex, fornecendo duas conexões HTTP, uma para cada direção.  
  
 No cliente, você deve configurar um endereço que o servidor pode usar para se conectar ao cliente, conforme mostrado no exemplo de configuração.  
  
  
  
> [!NOTE]
>  Clientes não-duplex que falham ao autenticar usando uma conversa segura normalmente geram um <xref:System.ServiceModel.Security.MessageSecurityException>. No entanto, se um cliente duplex que usa uma conversa segura não for autenticado, o cliente recebe um <xref:System.TimeoutException> em vez disso.  
  
 Se você criar um serviço do cliente usando o `WSHttpBinding` elemento e você não incluir o ponto de extremidade de retorno de chamada do cliente, você receberá o erro a seguir.  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 O código de exemplo a seguir mostra como especificar o cliente do endereço de ponto de extremidade no código.  
  
```  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
  
 O código de exemplo a seguir mostra como especificar o cliente do endereço de ponto de extremidade na configuração.  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  O modelo duplex não detecta automaticamente quando um serviço ou cliente fecha o canal. Então se um cliente termina inesperadamente, por padrão o serviço não será notificado, ou se um cliente termina inesperadamente, o serviço não será notificado. Os clientes e serviços podem implementar seu próprio protocolo para notificar uns aos outros, se desejarem assim.  
  
## <a name="see-also"></a>Consulte também  
 [Duplex](../../../../docs/framework/wcf/samples/duplex.md)  
 [Specifying Client Run-Time Behavior](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md) (Especificando o comportamento em tempo de execução do cliente)  
 [Como: criar uma fábrica de canais e usá-lo para criar e gerenciar canais](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
