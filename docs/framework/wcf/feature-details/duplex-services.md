---
title: Serviços de duplex
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: f9e563cb87ee376e33442cdf718f70202d300f40
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895176"
---
# <a name="duplex-services"></a>Serviços de duplex

Um contrato de serviço duplex é um padrão de troca de mensagens no qual ambos os pontos de extremidade podem enviar mensagens para o outro de forma independente. Um serviço duplex, portanto, pode enviar mensagens de volta ao ponto de extremidade do cliente, fornecendo comportamento semelhante a evento. A comunicação duplex ocorre quando um cliente se conecta a um serviço e fornece o serviço com um canal no qual o serviço pode enviar mensagens de volta ao cliente. Observe que o comportamento do tipo evento dos serviços duplex só funciona em uma sessão.

Para criar um contrato duplex, crie um par de interfaces. A primeira é a interface de contrato de serviço que descreve as operações que um cliente pode invocar. Esse contrato de serviço deve especificar um contrato de retorno <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> de *chamada* na propriedade. O contrato de retorno de chamada é a interface que define as operações que o serviço pode chamar no ponto de extremidade do cliente. Um contrato duplex não requer uma sessão, embora as associações duplex fornecidas pelo sistema façam uso delas.

Veja a seguir um exemplo de um contrato duplex.

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

A `CalculatorService` classe implementa a interface `ICalculatorDuplex` primária. O serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o resultado de cada sessão. Uma propriedade privada chamada `Callback` acessa o canal de retorno de chamada para o cliente. O serviço usa o retorno de chamada para enviar mensagens de volta para o cliente por meio da interface de retorno de chamada, conforme mostrado no código de exemplo a seguir.

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

O cliente deve fornecer uma classe que implemente a interface de retorno de chamada do contrato duplex, para receber mensagens do serviço. O código de exemplo a seguir `CallbackHandler` mostra uma classe que `ICalculatorDuplexCallback` implementa a interface.

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

O cliente WCF que é gerado para um contrato duplex requer que <xref:System.ServiceModel.InstanceContext> uma classe seja fornecida na construção. Essa <xref:System.ServiceModel.InstanceContext> classe é usada como o site de um objeto que implementa a interface de retorno de chamada e manipula as mensagens que são enviadas de volta do serviço. Uma <xref:System.ServiceModel.InstanceContext> classe é construída com uma instância `CallbackHandler` da classe. Esse objeto manipula as mensagens enviadas do serviço para o cliente na interface de retorno de chamada.

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

A configuração do serviço deve ser configurada para fornecer uma associação que dê suporte à comunicação de sessão e à comunicação duplex. O `wsDualHttpBinding` elemento dá suporte à comunicação de sessão e permite a comunicação duplex fornecendo conexões http duplas, uma para cada direção.

No cliente, você deve configurar um endereço que o servidor pode usar para se conectar ao cliente, conforme mostrado na seguinte configuração de exemplo.

> [!NOTE]
> Clientes não duplex que não se autenticam usando uma conversa segura normalmente lançam <xref:System.ServiceModel.Security.MessageSecurityException>um. No entanto, se um cliente duplex que usa uma conversa segura não for autenticado, o <xref:System.TimeoutException> cliente receberá um em vez disso.

Se você criar um cliente/serviço usando o `WSHttpBinding` elemento e não incluir o ponto de extremidade de retorno de chamada do cliente, você receberá o seguinte erro.

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

O código de exemplo a seguir mostra como especificar o endereço do ponto de extremidade do cliente programaticamente.

```csharp
WSDualHttpBinding binding = new WSDualHttpBinding();
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");
```

```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")
```

O código de exemplo a seguir mostra como especificar o endereço do ponto de extremidade do cliente na configuração.

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
> O modelo duplex não detecta automaticamente quando um serviço ou cliente fecha seu canal. Portanto, se um cliente for encerrado inesperadamente, por padrão, o serviço não será notificado, ou se um serviço for encerrado inesperadamente, o cliente não será notificado. Se você usar um serviço que está desconectado, <xref:System.ServiceModel.CommunicationException> a exceção será gerada. Os clientes e serviços podem implementar seu próprio protocolo para notificar uns aos outros se escolherem. Para obter mais informações sobre o tratamento de erros, consulte [controle de erros do WCF](../wcf-error-handling.md)

## <a name="see-also"></a>Consulte também

- [Duplex](../samples/duplex.md)
- [Especificando o comportamento em tempo de execução do cliente](../specifying-client-run-time-behavior.md)
- [Como: Criar uma fábrica de canais e usá-la para criar e gerenciar canais](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
