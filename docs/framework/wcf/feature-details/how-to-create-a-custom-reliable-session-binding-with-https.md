---
title: 'Como: Criar uma associação de sessão confiável personalizada com HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: f39325829cf4b548482a6a570a5aa1fd65e61a1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516675"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>Como: Criar uma associação de sessão confiável personalizada com HTTPS

Este tópico demonstra o uso da segurança de transporte de Secure Sockets Layer (SSL) com sessões confiáveis. Para usar uma sessão confiável por HTTPS, você deve criar uma associação personalizada que usa uma sessão confiável e o transporte HTTPS. Você habilitar a sessão confiável imperativamente por meio de código ou declarativamente no arquivo de configuração. Este procedimento usa os arquivos de configuração do cliente e o serviço para habilitar a sessão confiável e o [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) elemento.

A parte principal desse procedimento é que o  **\<ponto de extremidade >** elemento de configuração contêm uma `bindingConfiguration` atributo que faz referência a uma configuração de associação personalizada chamada `reliableSessionOverHttps`. O [  **\<associação >** ](../../../../docs/framework/misc/binding.md) elemento de configuração faz referência a esse nome para especificar que uma sessão confiável e o transporte HTTPS são usados, incluindo  **\< reliableSession >** e  **\<httpsTransport >** elementos.

Para a cópia de origem deste exemplo, consulte [personalizar associação de sessão confiável via HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Configurar o serviço com CustomBinding para usar uma sessão confiável com HTTPS

1. Defina um contrato de serviço para o tipo de serviço.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. Implemente o contrato de serviço em uma classe de serviço. Observe que as informações de associação ou o endereço não estão especificadas dentro da implementação do serviço. Não é necessário escrever código para recuperar as informações de associação ou o endereço do arquivo de configuração.

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. Criar uma *Web. config* arquivo para configurar um ponto de extremidade para o `CalculatorService` com uma associação personalizada denominada `reliableSessionOverHttps` que usa uma sessão confiável e o transporte HTTPS.

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. Criar uma *svc* arquivo que contém a linha:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Coloque o *svc* arquivo no seu diretório virtual de serviços de informações da Internet (IIS).

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>Configurar o cliente com CustomBinding para usar uma sessão confiável com HTTPS

1. Use o [ferramenta de utilitário de metadados ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) da linha de comando para gerar o código de metadados de serviço.

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. O aplicativo de cliente gerado também contém a implementação do `ClientCalculator`. Observe que as informações de endereço e a associação não são especificadas dentro da implementação do serviço. Não é necessário escrever código para recuperar as informações de endereço e a associação do arquivo de configuração.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. Configurar uma associação personalizada denominada `reliableSessionOverHttps` para usar o transporte HTTPS e sessões confiáveis.

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. Criar uma instância das `ClientCalculator` em um aplicativo e, em seguida, chamar as operações de serviço.

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. Compile e execute o cliente.  

## <a name="net-framework-security"></a>Segurança do .NET Framework

Porque o certificado usado neste exemplo é criado com um certificado de teste *Makecert.exe*, um alerta de segurança é exibida quando você tenta acessar um endereço HTTPS, tais como `https://localhost/servicemodelsamples/service.svc`, do seu navegador.

## <a name="see-also"></a>Consulte também

- [Sessões confiáveis](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
