---
title: '&lt;transporte&gt; de &lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 17468bc2354dc2865f10384e918ffb821a28f059
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767448"
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a>&lt;transporte&gt; de &lt;webHttpBinding&gt;
Define as configurações de segurança de nível de transporte para um ponto de extremidade de serviço configurada para receber solicitações HTTP.  
  
 \<system.ServiceModel>  
\<associações >  
\<webHttpBinding>  
\<associação >  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
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
|`Certificate`|Usa certificados x. 509 para autenticar o cliente.|  
|`Digest`|Usa autenticação digest.|  
|`Ntlm`|Usa a autenticação NTLM como um fallback com um domínio do Windows.|  
|`Windows`|Usa autenticação integrada do Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|A segurança é desabilitada.|  
|`Basic`|Usa a autenticação básica.|  
|`Digest`|Usa autenticação digest.|  
|`Ntlm`|Usa NTLM como um fallback com um domínio do Windows.|  
|`Windows`|Usa autenticação integrada do Windows.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|Representa os recursos de segurança de [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)  
 [Modelo de programação HTTP Web do WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
