---
title: Associação HTTP de federação do WS 2007
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 0fe4c0e62dbff3ae7f99f3a6dde34940abf90ae9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ws-2007-federation-http-binding"></a>Associação HTTP de federação do WS 2007
Este exemplo demonstra o uso de <xref:System.ServiceModel.WS2007FederationHttpBinding>, um padrão de associação que você pode usar para criar cenários federados que suporte de versão 1.3 da especificação WS-Trust.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O exemplo consiste em um programa baseado no console de cliente (Client.exe), um programa de serviço de token de segurança baseada em console (Securitytokenservice.exe) e um programa de serviço baseado em console (Service.exe). O serviço implementa um contrato que define um padrão de comunicação de solicitação/resposta. O contrato é definido pelo `ICalculator` interface, que expõe operações matemáticas (`Add`, `Subtract`, `Multiply`, e `Divide`). O cliente obtém um token de segurança do Security Token Service (STS) e faz solicitações síncronas para o serviço para uma operação matemática determinado. O serviço responde com o resultado. Atividade do cliente estiver visível na janela do console.  
  
 O exemplo faz o `ICalculator` contrato disponíveis usando o `ws2007FederationHttpBinding` elemento. A configuração da ligação no cliente é mostrada no código a seguir.  
  
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
  
 Sobre o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), o `security` valor Especifica o modo de segurança deve ser usado. Neste exemplo, `message` segurança for usada, que é por isso que o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) é especificada dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). O [ \<emissor >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) elemento dentro do [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Especifica o endereço e a associação para o STS emite um token de segurança para o cliente para que o cliente possa autenticar o `ICalculator` service.  
  
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
  
 Sobre o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), o `security` valor Especifica o modo de segurança deve ser usado. Neste exemplo, `message` segurança for usada, que é por isso que o [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) é especificada dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). O [ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elemento de `ws2007FederationHttpBinding` dentro de [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Especifica o endereço e a identidade de um ponto de extremidade que pode ser usado para recuperar metadados para o STS.  
  
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
  
 O [ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> permite que o serviço especificar restrições sobre os tokens que ele permite que os clientes apresentar durante a autenticação. Essa configuração especifica que os tokens assinados por um certificado cujo nome de assunto é CN = STS são aceitos pelo serviço.  
  
 STS disponibiliza um ponto de extremidade usando o padrão <xref:System.ServiceModel.WS2007HttpBinding>. O serviço responde às solicitações dos clientes de tokens. Se o cliente é autenticado usando uma conta do Windows, o serviço emite um token que contém o nome de usuário do cliente como uma declaração. Como parte da criação de token, STS assina o token usando a chave privada associada com o CN = certificado STS. Além disso, ele cria uma chave simétrica e criptografá-la usando a chave pública associada com o CN = localhost certificate. Retornar o token para o cliente, o STS também retorna a chave simétrica. O cliente apresenta o token emitido para o `ICalculator` de serviço e comprova que sabe a chave simétrica inscrevendo-se a mensagem com essa chave.  
  
 Quando você executar o exemplo, a solicitação para o token de segurança é mostrada na janela do console do STS. A operação solicitações e respostas são exibidas nas janelas do console de cliente e de serviço. Pressione ENTER em qualquer uma das janelas do console para desligar o aplicativo.  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 O arquivo bat incluído com este exemplo permite que você configure o servidor e o STS com os certificados relevantes para executar um aplicativo auto-hospedado. O arquivo em lotes cria dois certificados no repositório de certificados LocalMachine/TrustedPeople. O primeiro certificado tem um nome de assunto de CN = STS e é usado pelo STS para assinar os tokens de segurança que emite para o cliente. O segundo certificado tem um nome de assunto de CN = localhost e é usado pelo STS para criptografar uma chave de forma que o serviço pode descriptografar.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abra um prompt de comando do Visual Studio com privilégios de administrador e execute o arquivo bat para criar os certificados necessários.  
  
 Esse arquivo em lotes usa Certmgr.exe e Makecert.exe, que são distribuídas com o SDK do Windows. No entanto, você deve executar bat de dentro de um prompt de comando do Visual Studio para habilitar o script encontrar essas ferramentas.  
  
1.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Se você estiver usando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], você deve executar Service.exe, Client.exe, e SecurityTokenService.exe com privilégios de elevados (clique os arquivos e, em seguida, clique em **executar como administrador**).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a>Consulte também
