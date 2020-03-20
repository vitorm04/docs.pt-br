---
title: Associação HTTP de federação do WS 2007
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183181"
---
# <a name="ws-2007-federation-http-binding"></a>Associação HTTP de federação do WS 2007

Esta amostra demonstra <xref:System.ServiceModel.WS2007FederationHttpBinding>o uso de , uma vinculação padrão que você pode usar para construir cenários federados que suportam a versão 1.3 da especificação WS-Trust.

> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.

A amostra consiste em um programa de cliente baseado em console *(Client.exe),* um programa de serviço de token de segurança baseado em console *(Securitytokenservice.exe)* e um programa de serviço baseado em console *(Service.exe).* O serviço implementa um contrato que define um padrão de comunicação de solicitação/resposta. O contrato é `ICalculator` definido pela interface, que`Add` `Subtract`expõe `Multiply`as `Divide`operações matemáticas ( , , e ). O cliente obtém um token de segurança do Security Token Service (STS) e faz solicitações síncronas ao serviço para uma determinada operação matemática. O serviço então responde com o resultado. A atividade do cliente é visível na janela do console.

A amostra `ICalculator` disponibiliza o `ws2007FederationHttpBinding` contrato usando o elemento. A configuração dessa vinculação no cliente é mostrada no seguinte código:

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Endpoint address and binding for Security Token Service -->
          <issuer address ="http://localhost:8000/sts/windows"
                  binding ="ws2007HttpBinding" />
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

No [ \<>de ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` segurança , o valor especifica qual modo de segurança deve ser usado. Nesta amostra, `message` é usada a segurança, razão pela qual a [ \<mensagem>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) é especificada dentro do [ \<>de segurança ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). O [ \<emissor>](../../configure-apps/file-schema/wcf/issuer.md) elemento dentro da [ \<mensagem>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especifica o endereço e a vinculação para o STS que emite um token de segurança para o cliente para que o cliente possa autenticar o `ICalculator` serviço.
  
A configuração dessa vinculação no serviço é mostrada no seguinte código:

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Metadata address for Security Token Service -->
          <issuerMetadata address ="http://localhost:8000/sts/mex" >
            <identity>
              <certificateReference storeLocation ="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType ="FindBySubjectDistinguishedName"
                                    findValue ="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

No [ \<>de ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` segurança , o valor especifica qual modo de segurança deve ser usado. Nesta amostra, `message` é usada a segurança, razão pela qual a [ \<mensagem>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) é especificada dentro do [ \<>de segurança ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). O [ \<emissorMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) `ws2007FederationHttpBinding` elemento de dentro da [ \<mensagem>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especifica o endereço e a identidade para um ponto final que pode ser usado para recuperar metadados para o STS.

O comportamento do serviço é mostrado no seguinte código:

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name ="ServiceBehaviour" >
      <serviceDebug includeExceptionDetailInFaults ="true"/>
      <serviceMetadata httpGetEnabled ="true"/>
      <serviceCredentials>
        <issuedTokenAuthentication>
          <knownCertificates>
            <add storeLocation ="LocalMachine"
                 storeName="TrustedPeople"
                 x509FindType="FindBySubjectDistinguishedName"
                 findValue="CN=STS" />
          </knownCertificates>
        </issuedTokenAuthentication>
        <serviceCertificate storeLocation ="LocalMachine"
                            storeName ="My"
                            x509FindType ="FindBySubjectDistinguishedName"
                            findValue ="CN=localhost"/>
      </serviceCredentials>
    </behavior>
  </serviceBehaviors>
</behaviors>
```
  
O [ \<>de autenticação Token emitido](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> permite que o serviço especifique restrições nos tokens que permite que os clientes apresentem durante a autenticação. Esta configuração especifica que os tokens assinados por um certificado cujo nome de assunto é CN=STS são aceitos pelo serviço.

O STS disponibiliza um único <xref:System.ServiceModel.WS2007HttpBinding>ponto final usando o padrão . O serviço responde a pedidos de clientes por tokens. Se o cliente for autenticado usando uma conta do Windows, o serviço emitirá um token que contém o nome de usuário do cliente como uma reclamação. Como parte da criação do token, o STS assina o token usando a chave privada associada ao certificado CN=STS. Além disso, ele cria uma chave simétrica e a criptografa usando a chave pública associada ao certificado CN=localhost. Ao devolver o token ao cliente, o STS também retorna a chave simétrica. O cliente apresenta o token `ICalculator` emitido para o serviço e prova que conhece a chave simétrica assinando a mensagem com essa chave.

Quando você executa a amostra, a solicitação do token de segurança é mostrada na janela do console STS. As solicitações e respostas da operação são exibidas nas janelas do cliente e do console de serviço. Pressione ENTER em qualquer uma das janelas do console para desligar o aplicativo.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

O arquivo *Setup.bat* incluído nesta amostra permite configurar o servidor e o STS com os certificados relevantes para executar um aplicativo auto-hospedado. O arquivo em lote cria dois certificados na loja de certificados LocalMachine/TrustedPeople. O primeiro certificado tem um nome de assunto de CN=STS e é usado pela STS para assinar os tokens de segurança que ele emite ao cliente. O segundo certificado tem um nome de assunto de CN=localhost e é usado pelo STS para criptografar uma chave de uma maneira que o serviço possa descriptografar.

## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Abra um prompt de comando de desenvolvedor para o Visual Studio com privilégios de administrador e execute o arquivo Setup.bat para criar os certificados necessários.

 Este arquivo em lote usa *Certmgr.exe* e Makecert.exe, que são distribuídos com o Windows SDK. No entanto, você deve executar *Setup.bat* de dentro de um prompt de comando do Visual Studio para permitir que o script encontre essas ferramentas.

1. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](building-the-samples.md).

2. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](running-the-samples.md)de Comunicação do Windows . Se você estiver usando o Windows Vista, você deve executar *Service.exe*, *Client.exe*e *SecurityTokenService.exe* com privilégios elevados (clique com o botão direito do mouse nos arquivos e clique em **Executar como administrador**).

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está no seguinte diretório:
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
