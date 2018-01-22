---
title: "Como fazer intercâmbio de mensagens dentro de uma sessão confiável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba3948ef52e6ce527b0bdba77652949e43d05eb2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Como fazer intercâmbio de mensagens dentro de uma sessão confiável

Este tópico descreve as etapas necessárias para habilitar uma sessão confiável usando uma das associações fornecidas pelo sistema que oferecem suporte a uma sessão, mas não por padrão. Habilitar uma sessão confiável imperativa usando código ou declarativamente em seu arquivo de configuração. Este procedimento usa os arquivos de configuração do cliente e de serviço para habilitar a sessão confiável e estipular que as mensagens chegam na mesma ordem em que foram enviadas.

A parte fundamental desse procedimento é que o elemento de configuração de ponto de extremidade contêm um `bindingConfiguration` atributo que faz referência a uma configuração de associação denominada `Binding1`. O [  **\<associação >** ](../../../../docs/framework/misc/binding.md) elemento de configuração faz referência a esse nome para permitir sessões confiáveis, definindo o `enabled` atributo o [  **\<reliableSession >** ](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elemento `true`. Especifique as garantias de entrega ordenada para a sessão confiável, definindo o `ordered` atributo `true`.

Para a cópia de origem deste exemplo, consulte [sessão confiável de WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configure o serviço com um WSHttpBinding para usar uma sessão confiável

1. Defina um contrato de serviço para o tipo de serviço.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implemente o contrato de serviço em uma classe de serviço. Observe que as informações de associação ou o endereço não estão especificadas dentro da implementação do serviço. Não é necessário escrever código para recuperar as informações de associação ou o endereço do arquivo de configuração.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Criar um *Web. config* arquivo para configurar um ponto de extremidade para o `CalculatorService` que usa o <xref:System.ServiceModel.WSHttpBinding> com sessão confiável habilitado e a entrega de mensagens necessária ordenada.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Criar um *svc* arquivo que contém a linha:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  Coloque o *svc* arquivo no seu diretório virtual dos serviços de informações da Internet (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Configurar o cliente com um WSHttpBinding para usar uma sessão confiável

1. Use o [Ferramenta Utilitária de metadados ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar o código de metadados de serviço:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. O cliente gerado contém o `ICalculator` interface que define o contrato de serviço que deve atender a implementação do cliente.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. O aplicativo cliente gerado também contém a implementação de `ClientCalculator`. Observe que as informações de endereço e associação não são especificadas em qualquer lugar dentro da implementação do serviço. Não é necessário escrever código para recuperar as informações de associação ou o endereço do arquivo de configuração.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* também gera a configuração do cliente que usa o <xref:System.ServiceModel.WSHttpBinding> classe. Nomeie o arquivo de configuração *App. config* ao usar [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Criar uma instância do `ClientCalculator` em um aplicativo e chamar as operações de serviço.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Compile e execute o cliente.

## <a name="example"></a>Exemplo

Várias das associações fornecidas pelo sistema suportam a sessões confiáveis por padrão. Elas incluem:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Para obter um exemplo de como criar uma associação personalizada que dá suporte a sessões confiáveis, consulte [como: criar uma associação de sessão confiável personalizada com HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Consulte também

[Sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
