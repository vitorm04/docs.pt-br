---
title: Como configurar serviços do WCF para interoperar com clientes WSE 3.0
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: bd9f2bec94ca45f76590f64366428a00edd5d6ea
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141751"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Como configurar serviços do WCF para interoperar com clientes WSE 3.0

Os serviços de Windows Communication Foundation (WCF) são compatíveis com nível de conexão com os serviços Web de aprimoramentos 3,0 para Microsoft .NET (WSE) quando os serviços WCF são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Para habilitar um serviço WCF para interoperar com clientes WSE 3,0

1. Defina uma associação personalizada para o serviço WCF.

    Para especificar que a versão de agosto de 2004 da especificação WS-Addressing seja usada para codificação de mensagens, uma associação personalizada deve ser criada.

    1. Adicione um [> filho\<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) à [\<associações](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração do serviço.

    2. Especifique um nome para a associação, adicionando um [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) ao [> CustomBinding\<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) e definindo o atributo `name`.

    3. Especifique um modo de autenticação e a versão das especificações do WS-Security que são usadas para proteger mensagens que são compatíveis com o WSE 3,0, adicionando um [> de segurança de\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) filho ao [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md).

        Para definir o modo de autenticação, defina o atributo `authenticationMode` do [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Um modo de autenticação é praticamente equivalente a uma declaração de segurança completa no WSE 3,0. A tabela a seguir mapeia modos de autenticação no WCF para declarações de segurança de uso imediato no WSE 3,0.

        |Modo de autenticação do WCF|Declaração de segurança do WSE 3,0 pronto para uso|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \* uma das principais diferenças entre as declarações de segurança `mutualCertificate10Security` e `mutualCertificate11Security` pronto para uso é a versão da especificação WS-Security que o WSE usa para proteger as mensagens SOAP. Para `mutualCertificate10Security`, o WS-Security 1,0 é usado, ao passo que WS-Security 1,1 é usado para `mutualCertificate11Security`. Para o WCF, a versão da especificação WS-Security é especificada no atributo `messageSecurityVersion` do > de [segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).

        Para definir a versão da especificação WS-Security usada para proteger mensagens SOAP, defina o atributo `messageSecurityVersion` do [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Para interoperar com o WSE 3,0, defina o valor do atributo `messageSecurityVersion` como <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.

    4. Especifique que a versão de agosto de 2004 da especificação WS-Addressing é usada pelo WCF adicionando um [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) e defina o `messageVersion` como seu valor como <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.

        > [!NOTE]
        > Quando você estiver usando SOAP 1,2, defina o atributo `messageVersion` como <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.

2. Especifique que o serviço usa a associação personalizada.

    1. Defina o atributo `binding` do elemento [> do ponto de extremidade do\<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) como `customBinding`.

    2. Defina o atributo `bindingConfiguration` do elemento [ponto de extremidade do\<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) para o valor especificado no atributo `name` da [\<de associação](../../configure-apps/file-schema/wcf/bindings.md) > para a associação personalizada.

## <a name="example"></a>Exemplo

O exemplo de código a seguir especifica que o `Service.HelloWorldService` usa uma associação personalizada para interoperar com clientes WSE 3,0. A associação personalizada especifica que a versão de agosto de 2004 do WS-Addressing e o conjunto de especificações do WS-Security 1,1 são usados para codificar as mensagens trocadas. As mensagens são protegidas usando o modo de autenticação <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>.

```xml
<configuration>
  <system.serviceModel>
    <services>
      <service
        behaviorConfiguration="ServiceBehavior"
        name="Service.HelloWorldService">
        <endpoint binding="customBinding" address=""
          bindingConfiguration="ServiceBinding"
          contract="Service.IHelloWorld"></endpoint>
      </service>
    </services>

    <bindings>
      <customBinding>
        <binding name="ServiceBinding">
          <security authenticationMode="AnonymousForCertificate"
                  messageProtectionOrder="SignBeforeEncrypt"
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"
                  requireDerivedKeys="false">
          </security>
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>
          <httpTransport/>
        </binding>
      </customBinding>
    </bindings>
    <behaviors>
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">
        <serviceCredentials>
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>
        </serviceCredentials>
      </behavior>
    </behaviors>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Consulte também

- [Como personalizar uma associação fornecida pelo sistema](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
