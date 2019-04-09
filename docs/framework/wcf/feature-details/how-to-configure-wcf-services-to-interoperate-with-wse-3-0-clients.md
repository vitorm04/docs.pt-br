---
title: 'Como: configurar serviços do WCF para interoperar com clientes WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 24c44f415eff8518bcd73696c5cd9302371ad0c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177288"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Como: configurar serviços do WCF para interoperar com clientes WSE 3.0
Serviços Windows Communication Foundation (WCF) são compatíveis com o nível de transmissão com Web Services aprimoramentos 3.0 para clientes do Microsoft .NET (WSE) quando os serviços do WCF são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Para habilitar um serviço WCF interoperar com clientes WSE 3.0  
  
1.  Defina uma ligação personalizada para o serviço WCF.  
  
     Para especificar que a versão de agosto de 2004 da especificação WS-Addressing é usada para codificação de mensagens, uma ligação personalizada deve ser criada.  
  
    1.  Adicionar uma criança [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) para o [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração do serviço.  
  
    2.  Especifique um nome para a associação, adicionando um [ \<associação >](../../../../docs/framework/misc/binding.md) para o [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) e definindo o `name` atributo.  
  
    3.  Especifique um modo de autenticação e a versão das especificações WS-Security que são usados para proteger as mensagens que são compatíveis com o WSE 3.0, com a adição de um filho [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) para o [ \<de associação >](../../../../docs/framework/misc/binding.md).  
  
         Para definir o modo de autenticação, defina as `authenicationMode` atributo o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Um modo de autenticação é aproximadamente equivalente a uma asserção de segurança pronta para uso em WSE 3.0. A tabela a seguir mapeia os modos de autenticação no WCF para asserções de segurança pronta para uso em WSE 3.0.  
  
        |Modo de autenticação do WCF|Declaração de segurança pronta para uso do WSE 3.0|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* Uma das principais diferenças entre o `mutualCertificate10Security` e `mutualCertificate11Security` asserções de segurança turnkey é a versão da especificação WS-Security WSE usa para proteger as mensagens SOAP. Para `mutualCertificate10Security`, WS-Security 1.0 for usada, enquanto que o WS-Security 1.1 é usado para `mutualCertificate11Security`. Para o WCF, a versão da especificação WS-Security é especificada no `messageSecurityVersion` atributo o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Para definir a versão da especificação WS-Security que é usada para proteger mensagens SOAP, defina as `messageSecurityVersion` atributo o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Para interoperar com o WSE 3.0, defina o valor da `messageSecurityVersion` atributo <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  Especificar que a versão de agosto de 2004 da especificação WS-Addressing é usada pelo WCF, adicionando um [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) e defina as `messageVersion` para seu valor para <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
        > [!NOTE]
        >  Quando você estiver usando o SOAP 1.2, defina as `messageVersion` atributo <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2.  Especifique que o serviço usa a associação personalizada.  
  
    1.  Defina a `binding` atributo do [ \<ponto de extremidade >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento a ser `customBinding`.  
  
    2.  Definir a `bindingConfiguration` atributo do [ \<ponto de extremidade >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento como o valor especificado no `name` atributo do [ \<associação >](../../../../docs/framework/misc/binding.md) para personalizado associação.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir especifica que o `Service.HelloWorldService` usa uma ligação personalizada para interoperar com clientes WSE 3.0. A associação personalizada Especifica a versão de agosto de 2004 de WS-Addressing e o conjunto de WS-Security 1.1 das especificações são usados para codificar as mensagens trocadas. As mensagens são protegidas usando o <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> modo de autenticação.  
  
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

- [Como: personalizar uma associação fornecida pelo sistema](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
