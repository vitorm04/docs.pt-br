---
title: Associação HTTP de federação do WS 2007
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 550a88552658864e3eedb70463e676ad6f9a2511
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007507"
---
# <a name="ws-2007-federation-http-binding"></a>Associação HTTP de federação do WS 2007
Este exemplo demonstra o uso de <xref:System.ServiceModel.WS2007FederationHttpBinding>, um padrão de associação que você pode usar para criar cenários federados esse suporte de versão 1.3 da especificação WS-Trust.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O exemplo consiste em um programa de cliente baseada em console (Client.exe), um programa de serviço de token de segurança baseada em console (Securitytokenservice.exe) e um programa de serviço baseada em console (Service.exe). O serviço implementa um contrato que define um padrão de comunicação de solicitação/resposta. O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (`Add`, `Subtract`, `Multiply`, e `Divide`). O cliente obtém um token de segurança do Security Token Service (STS) e faz solicitações síncronas para o serviço para uma operação matemática determinado. O serviço responde com o resultado. Atividade do cliente está visível na janela do console.  
  
 O exemplo faz o `ICalculator` contrato disponíveis usando o `ws2007FederationHttpBinding` elemento. A configuração desta associação no cliente é mostrada no código a seguir.  
  
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
  
 Sobre o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), o `security` valor Especifica o modo de segurança deve ser usado. Neste exemplo, `message` segurança for usada, o que é por isso que o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especificado dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). O [ \<emissor >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) elemento dentro de [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Especifica o endereço e a associação para o STS que emite um token de segurança para o cliente para que o cliente possa autenticar o `ICalculator` service.  
  
 A configuração desta associação de serviço é mostrada no código a seguir.  
  
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
  
 Sobre o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), o `security` valor Especifica o modo de segurança deve ser usado. Neste exemplo, `message` segurança for usada, o que é por isso que o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) especificado dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). O [ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elemento da `ws2007FederationHttpBinding` dentro do [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Especifica o endereço e a identidade para um ponto de extremidade que pode ser usado para recuperar metadados para o STS.  
  
 O comportamento para o serviço é mostrado no código a seguir.  
  
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
  
 O [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> permite que o serviço especificar restrições nos tokens que ele permite que os clientes presentes durante a autenticação. Essa configuração especifica que os tokens assinados por um certificado cujo nome de assunto é CN = STS são aceitos pelo serviço.  
  
 STS disponibiliza um ponto de extremidade usando o padrão <xref:System.ServiceModel.WS2007HttpBinding>. O serviço responde às solicitações de clientes para tokens. Se o cliente é autenticado usando uma conta do Windows, o serviço emite um token que contém o nome de usuário do cliente como uma declaração. Como parte da criação de token, o STS assina o token usando a chave privada associada com o CN = certificado STS. Além disso, ele cria uma chave simétrica e criptografa usando a chave pública associada com o CN = localhost certificate. Retornar o token para o cliente, o STS também retorna a chave simétrica. O cliente apresenta o token emitido para o `ICalculator` de serviço e comprova que ele saiba a chave simétrica inscrevendo-se a mensagem com essa chave.  
  
 Quando você executar o exemplo, a solicitação de token de segurança é mostrada na janela do console do STS. A operação solicitações e respostas são exibidas nas janelas do console de cliente e o serviço. Pressione ENTER em qualquer uma das janelas do console para fechar o aplicativo.  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 O arquivo Setup bat incluído com este exemplo permite que você configure o servidor e o STS com os certificados relevantes para executar um aplicativo hospedado internamente. O arquivo em lotes cria dois certificados no repositório de certificados LocalMachine/TrustedPeople. O primeiro certificado tem um nome de assunto de CN = STS e é usado pelo STS para assinar os tokens de segurança que emite ao cliente. O segundo certificado tem um nome de assunto de CN = localhost e é usada para criptografar uma chave de forma que o serviço pode descriptografar pelo STS.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Abra um Prompt de comando do desenvolvedor para Visual Studio com privilégios de administrador e execute o arquivo Setup. bat para criar os certificados necessários.  
  
 Esse arquivo em lotes usa Certmgr.exe e Makecert.exe, que são distribuídos com o SDK do Windows. No entanto, você deve executar o Setup. bat de dentro de um prompt de comando do Visual Studio para habilitar o script localizar essas ferramentas.  
  
1. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Se você estiver usando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], você deve executar Service.exe, Client.exe, e SecurityTokenService.exe com privilégios elevados (os arquivos com o botão direito e, em seguida, clique em **executar como administrador**).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
