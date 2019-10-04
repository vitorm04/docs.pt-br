---
title: Associação HTTP de federação do WS 2007
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: ad56665b5b6648fb93a9f31f18167a964b4cba92
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834649"
---
# <a name="ws-2007-federation-http-binding"></a>Associação HTTP de federação do WS 2007

Este exemplo demonstra o uso de <xref:System.ServiceModel.WS2007FederationHttpBinding>, uma associação padrão que você pode usar para criar cenários federados que dão suporte à versão 1,3 da especificação WS-Trust.

> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.

O exemplo consiste em um programa cliente baseado em console (*Client. exe*), um programa de serviço de token de segurança baseado em console (*SecurityTokenService. exe*) e um programa de serviço baseado em console (*Service. exe*). O serviço implementa um contrato que define um padrão de comunicação de solicitação/resposta. O contrato é definido pela interface `ICalculator`, que expõe operações matemáticas (`Add`, `Subtract`, `Multiply` e `Divide`). O cliente obtém um token de segurança do STS (serviço de token de segurança) e faz solicitações síncronas para o serviço para uma determinada operação matemática. Em seguida, o serviço responde com o resultado. A atividade do cliente fica visível na janela do console.

O exemplo torna o contrato `ICalculator` disponível usando o elemento `ws2007FederationHttpBinding`. A configuração dessa associação no cliente é mostrada no código a seguir:

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

No [> \<Security](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), o valor de `security` especifica qual modo de segurança deve ser usado. Neste exemplo, é usada a segurança `message`, que é o motivo pelo qual a [> \<message](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) é especificada dentro do [> \<security](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). O elemento [\<issuer >](../../configure-apps/file-schema/wcf/issuer.md) dentro de [@no__t >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especifica o endereço e a associação para o STS que emite um token de segurança para o cliente para que o cliente possa se autenticar no serviço `ICalculator`.
  
A configuração dessa associação no serviço é mostrada no código a seguir:

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

No [> \<Security](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), o valor de `security` especifica qual modo de segurança deve ser usado. Neste exemplo, é usada a segurança `message`, que é o motivo pelo qual a [> \<message](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) é especificada dentro do [> \<security](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). O elemento [\<issuerMetadata >](../../configure-apps/file-schema/wcf/issuermetadata.md) do `ws2007FederationHttpBinding` dentro do [\<message >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especifica o endereço e a identidade de um ponto de extremidade que pode ser usado para recuperar metadados para o STS.

O comportamento do serviço é mostrado no código a seguir:

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
  
O > de [> de @no__t 1issuedTokenAuthentication](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)permite que o serviço especifique restrições nos tokens que permite que os clientes apresentem durante a autenticação. Essa configuração especifica que os tokens assinados por um certificado cujo nome da entidade é CN = STS são aceitos pelo serviço.

O STS disponibiliza um único ponto de extremidade usando o <xref:System.ServiceModel.WS2007HttpBinding> padrão. O serviço responde às solicitações de clientes para tokens. Se o cliente for autenticado usando uma conta do Windows, o serviço emitirá um token que contém o nome de usuário do cliente como uma declaração. Como parte da criação do token, o STS assina o token usando a chave privada associada ao certificado CN = STS. Além disso, ele cria uma chave simétrica e a criptografa usando a chave pública associada ao certificado CN = localhost. Ao retornar o token para o cliente, o STS também retorna a chave simétrica. O cliente apresenta o token emitido para o serviço `ICalculator` e comprova que ele conhece a chave simétrica assinando a mensagem com essa chave.

Quando você executa o exemplo, a solicitação para o token de segurança é mostrada na janela do console do STS. As solicitações e respostas da operação são exibidas nas janelas do console do cliente e do serviço. Pressione ENTER em qualquer uma das janelas do console para desligar o aplicativo.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

O arquivo *Setup. bat* incluído com este exemplo permite que você configure o servidor e o STS com os certificados relevantes para executar um aplicativo auto-hospedado. O arquivo em lotes cria dois certificados no repositório de certificados LocalMachine/TrustedPeople. O primeiro certificado tem um nome de assunto de CN = STS e é usado pelo STS para assinar os tokens de segurança que ele emite para o cliente. O segundo certificado tem um nome de assunto de CN = localhost e é usado pelo STS para criptografar uma chave de forma que o serviço possa ser descriptografado.

## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Abra um Prompt de Comando do Desenvolvedor para o Visual Studio com privilégios de administrador e execute o arquivo setup. bat para criar os certificados necessários.

 Esse arquivo em lotes usa *certmgr. exe* e MakeCert. exe, que são distribuídos com o SDK do Windows. No entanto, você deve executar *Setup. bat* de dentro de um prompt de comando do Visual Studio para habilitar o script para encontrar essas ferramentas.

1. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).

2. Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md). Se você estiver usando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], deverá executar *Service. exe*, *Client. exe*e *SecurityTokenService. exe* com privilégios elevados (clique com o botão direito do mouse nos arquivos e clique em **Executar como administrador**).

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está no seguinte diretório:
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
