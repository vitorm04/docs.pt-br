---
title: '&lt;transporte&gt; de &lt;wsHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57496371032fd8f07f69bf71cc5c266d977bf57d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a>&lt;transporte&gt; de &lt;wsHttpBinding&gt;
Define as configurações de autenticação para o transporte HTTP.  
  
 \<System. ServiceModel >  
\<associações >  
\<wsHttpBinding >  
\<associação >  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a>Tipo  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`clientCredentialType`|Especifica a credencial usada para autenticar o cliente para o serviço. Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Especifica a credencial usada para autenticar o cliente a um proxy do domínio. Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Uma cadeia de caracteres que especifica o realm de autenticação para a autenticação básica ou digest. O padrão é uma cadeia de caracteres vazia.<br /><br /> Pelo menos, um realm de autenticação especifica o nome do host que executa a autenticação. Ele também pode especificar uma coleção de usuários que tem acesso. Um usuário pode consultar o realm de autenticação para determinar qual da várias possíveis nomes de usuário e senhas pode ser usado.|  
|`policyEnforcement`|Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> devem ser impostas.<br /><br /> 1.  Nunca – a política é aplicada nunca (proteção estendida é desabilitada).<br />2.  WhenSupported – a política será aplicada somente se o cliente oferece suporte à proteção estendida.<br />3.  Sempre – a política sempre é aplicada. Os clientes que não oferecem suporte a proteção estendida falhará ao autenticar.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|A segurança é desabilitada.|  
|`Basic`|Usa a autenticação básica.|  
|`Digest`|Usa autenticação digest.|  
|`Ntlm`|Usa a autenticação NTLM como um fallback com um domínio do Windows.|  
|`Windows`|Usa autenticação integrada do Windows.|  
|`Certificate`|Usa certificados x. 509 para autenticar o cliente.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|A segurança é desabilitada.|  
|`Basic`|Usa a autenticação básica.|  
|`Digest`|Usa autenticação digest.|  
|`Ntlm`|Usa NTLM como um fallback com um domínio do Windows.|  
|`Windows`|Usa autenticação integrada do Windows.|  
|`Certificate`|Usa certificados x. 509 para autenticar o cliente.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Representa os recursos de segurança de [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
