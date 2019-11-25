---
title: Como fazer intercâmbio de mensagens dentro de uma sessão confiável
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 58a392fc6295e82f41e08c80a3343b4059afad7e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141683"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Como fazer intercâmbio de mensagens dentro de uma sessão confiável

Este tópico descreve as etapas necessárias para habilitar uma sessão confiável usando uma das associações fornecidas pelo sistema que dão suporte a essa sessão, mas não por padrão. Você habilita uma sessão confiável imperativamente usando código ou declarativamente em seu arquivo de configuração. Este procedimento usa os arquivos de configuração de cliente e serviço para habilitar a sessão confiável e estipular que as mensagens chegam na mesma ordem em que foram enviadas.

A parte principal desse procedimento é que o elemento de configuração do ponto de extremidade contém um atributo `bindingConfiguration` que faz referência a uma configuração de associação chamada `Binding1`. O elemento de configuração [ **\<binding >** ](../../configure-apps/file-schema/wcf/bindings.md) faz referência a esse nome para habilitar sessões confiáveis, definindo o atributo `enabled` do elemento [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) como `true`. Você especifica as garantias de entrega ordenadas para a sessão confiável definindo o atributo `ordered` como `true`.

Para a cópia de origem deste exemplo, consulte a [sessão confiável do WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurar o serviço com uma WSHttpBinding para usar uma sessão confiável

1. Defina um contrato de serviço para o tipo de serviço.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implemente o contrato de serviço em uma classe de serviço. Observe que as informações de endereço ou de associação não são especificadas dentro da implementação do serviço. Não é necessário escrever código para recuperar o endereço ou as informações de associação do arquivo de configuração.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Crie um arquivo *Web. config* para configurar um ponto de extremidade para o `CalculatorService` que usa o <xref:System.ServiceModel.WSHttpBinding> com sessão confiável habilitada e entrega ordenada de mensagens necessárias.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Crie um arquivo *Service. svc* que contenha a linha:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Coloque o arquivo *Service. svc* no diretório virtual do serviços de informações da Internet (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurar o cliente com um WSHttpBinding para usar uma sessão confiável

1. Use a [ferramenta de utilitário de metadados ServiceModel (*svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar código de metadados de serviço:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. O cliente gerado contém a interface `ICalculator` que define o contrato de serviço que a implementação do cliente deve satisfazer.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. O aplicativo cliente gerado também contém a implementação do `ClientCalculator`. Observe que as informações de endereço e de associação não são especificadas em nenhum lugar dentro da implementação do serviço. Não é necessário escrever código para recuperar o endereço ou as informações de associação do arquivo de configuração.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil. exe* também gera a configuração para o cliente que usa a classe <xref:System.ServiceModel.WSHttpBinding>. Nomeie o arquivo de configuração *app. config* ao usar o Visual Studio.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Crie uma instância do `ClientCalculator` em um aplicativo e chame as operações de serviço.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Compile e execute o cliente.

## <a name="example"></a>Exemplo

Por padrão, várias das associações fornecidas pelo sistema dão suporte a sessões confiáveis. Elas incluem:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Para obter um exemplo de como criar uma associação personalizada que dê suporte a sessões confiáveis, consulte [como: criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Consulte também

- [Sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
