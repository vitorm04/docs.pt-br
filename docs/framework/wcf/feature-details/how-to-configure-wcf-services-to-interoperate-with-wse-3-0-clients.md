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
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="0b706-102">Como configurar serviços do WCF para interoperar com clientes WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="0b706-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="0b706-103">Os serviços de Windows Communication Foundation (WCF) são compatíveis com nível de conexão com os serviços Web de aprimoramentos 3,0 para Microsoft .NET (WSE) quando os serviços WCF são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="0b706-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="0b706-104">Para habilitar um serviço WCF para interoperar com clientes WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="0b706-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="0b706-105">Defina uma associação personalizada para o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="0b706-105">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="0b706-106">Para especificar que a versão de agosto de 2004 da especificação WS-Addressing seja usada para codificação de mensagens, uma associação personalizada deve ser criada.</span><span class="sxs-lookup"><span data-stu-id="0b706-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="0b706-107">Adicione um [> filho\<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) à [\<associações](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="0b706-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="0b706-108">Especifique um nome para a associação, adicionando um [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) ao [> CustomBinding\<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) e definindo o atributo `name`.</span><span class="sxs-lookup"><span data-stu-id="0b706-108">Specify a name for the binding, by adding a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="0b706-109">Especifique um modo de autenticação e a versão das especificações do WS-Security que são usadas para proteger mensagens que são compatíveis com o WSE 3,0, adicionando um [> de segurança de\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) filho ao [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md).</span><span class="sxs-lookup"><span data-stu-id="0b706-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md).</span></span>

        <span data-ttu-id="0b706-110">Para definir o modo de autenticação, defina o atributo `authenticationMode` do [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0b706-110">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="0b706-111">Um modo de autenticação é praticamente equivalente a uma declaração de segurança completa no WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="0b706-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="0b706-112">A tabela a seguir mapeia modos de autenticação no WCF para declarações de segurança de uso imediato no WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="0b706-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="0b706-113">Modo de autenticação do WCF</span><span class="sxs-lookup"><span data-stu-id="0b706-113">WCF Authentication Mode</span></span>|<span data-ttu-id="0b706-114">Declaração de segurança do WSE 3,0 pronto para uso</span><span class="sxs-lookup"><span data-stu-id="0b706-114">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="0b706-115">\* uma das principais diferenças entre as declarações de segurança `mutualCertificate10Security` e `mutualCertificate11Security` pronto para uso é a versão da especificação WS-Security que o WSE usa para proteger as mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="0b706-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="0b706-116">Para `mutualCertificate10Security`, o WS-Security 1,0 é usado, ao passo que WS-Security 1,1 é usado para `mutualCertificate11Security`.</span><span class="sxs-lookup"><span data-stu-id="0b706-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="0b706-117">Para o WCF, a versão da especificação WS-Security é especificada no atributo `messageSecurityVersion` do > de [segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0b706-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="0b706-118">Para definir a versão da especificação WS-Security usada para proteger mensagens SOAP, defina o atributo `messageSecurityVersion` do [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="0b706-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="0b706-119">Para interoperar com o WSE 3,0, defina o valor do atributo `messageSecurityVersion` como <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b706-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="0b706-120">Especifique que a versão de agosto de 2004 da especificação WS-Addressing é usada pelo WCF adicionando um [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) e defina o `messageVersion` como seu valor como <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b706-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="0b706-121">Quando você estiver usando SOAP 1,2, defina o atributo `messageVersion` como <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b706-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="0b706-122">Especifique que o serviço usa a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0b706-122">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="0b706-123">Defina o atributo `binding` do elemento [> do ponto de extremidade do\<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) como `customBinding`.</span><span class="sxs-lookup"><span data-stu-id="0b706-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="0b706-124">Defina o atributo `bindingConfiguration` do elemento [ponto de extremidade do\<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) para o valor especificado no atributo `name` da [\<de associação](../../configure-apps/file-schema/wcf/bindings.md) > para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0b706-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="0b706-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b706-125">Example</span></span>

<span data-ttu-id="0b706-126">O exemplo de código a seguir especifica que o `Service.HelloWorldService` usa uma associação personalizada para interoperar com clientes WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="0b706-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="0b706-127">A associação personalizada especifica que a versão de agosto de 2004 do WS-Addressing e o conjunto de especificações do WS-Security 1,1 são usados para codificar as mensagens trocadas.</span><span class="sxs-lookup"><span data-stu-id="0b706-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="0b706-128">As mensagens são protegidas usando o modo de autenticação <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>.</span><span class="sxs-lookup"><span data-stu-id="0b706-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0b706-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b706-129">See also</span></span>

- [<span data-ttu-id="0b706-130">Como personalizar uma associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="0b706-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
