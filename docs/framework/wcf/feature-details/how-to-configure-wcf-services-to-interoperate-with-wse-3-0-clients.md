---
title: "Como configurar serviços do WCF para interoperar com clientes WSE 3.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5589ad8e4193416738da98676551bbf82c128a79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Como configurar serviços do WCF para interoperar com clientes WSE 3.0
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]os serviços são compatíveis com o nível de transmissão com 3.0 de aprimoramentos de serviços Web para clientes do Microsoft .NET (WSE) quando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços estão configurados para usar a versão de agosto de 2004 da especificação WS-Addressing.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Para habilitar um serviço WCF interoperar com clientes WSE 3.0  
  
1.  Definir uma associação personalizada para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.  
  
     Para especificar que a versão de agosto de 2004 da especificação WS-Addressing é usada para codificação de mensagens, uma associação personalizada deve ser criada.  
  
    1.  Adicionar uma criança [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) para o [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração do serviço.  
  
    2.  Especifique um nome para a associação, adicionando um [ \<associação >](../../../../docs/framework/misc/binding.md) para o [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) e configuração de `name` atributo.  
  
    3.  Especifique um modo de autenticação e a versão das especificações do WS-Security que são usadas para proteger as mensagens que são compatíveis com WSE 3.0, adicionando um filho [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) para o [ \<associação >](../../../../docs/framework/misc/binding.md).  
  
         Para definir o modo de autenticação, defina o `authenicationMode` atributo o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Um modo de autenticação é aproximadamente equivalente a uma asserção de segurança completa WSE 3.0. A tabela a seguir mapeia os modos de autenticação na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para declarações de segurança completa de WSE 3.0.  
  
        |Modo de autenticação do WCF|Asserção de segurança completa de WSE 3.0|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \*Uma das principais diferenças entre o `mutualCertificate10Security` e `mutualCertificate11Security` asserções de segurança completa é a versão da especificação WS-Security WSE usa para proteger as mensagens SOAP. Para `mutualCertificate10Security`, WS-Security 1.0 for usada, enquanto 1.1 do WS-Security é usada para `mutualCertificate11Security`. Para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], a versão da especificação WS-Security é especificada no `messageSecurityVersion` atributo o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Para definir a versão da especificação WS-Security que é usada para proteger mensagens SOAP, defina o `messageSecurityVersion` atributo o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Para interoperar com WSE 3.0, defina o valor da `messageSecurityVersion` atributo <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  Especificar que a versão de agosto de 2004 da especificação WS-Addressing é usada pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adicionando um [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) e defina o `messageVersion` para seu valor como <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
        > [!NOTE]
        >  Quando você estiver usando SOAP 1.2, defina o `messageVersion` atributo <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2.  Especifique que o serviço usa a associação personalizada.  
  
    1.  Definir o `binding` atributo do [ \<ponto de extremidade >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento `customBinding`.  
  
    2.  Definir o `bindingConfiguration` atributo do [ \<ponto de extremidade >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento para o valor especificado no `name` atributo do [ \<associação >](../../../../docs/framework/misc/binding.md) para personalizado associação.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir especifica que o `Service.HelloWorldService` usa uma associação personalizada para interoperar com clientes WSE 3.0. A associação personalizada Especifica a versão de agosto de 2004 do WS-Addressing e o conjunto de 1.1 do WS-Security de especificações são usados para codificar as mensagens trocadas. As mensagens são protegidas usando o <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> modo de autenticação.  
  
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
 [Como: personalizar uma associação fornecida pelo sistema](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
