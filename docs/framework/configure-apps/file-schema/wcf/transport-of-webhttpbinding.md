---
title: <transport> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732795"
---
# <a name="transport-of-webhttpbinding"></a>> de transporte de \<de \<WebHttpBinding >
Define as configurações de segurança no nível de transporte para um ponto de extremidade de serviço configurado para receber solicitações HTTP.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WebHttpBinding**](webhttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<security >** ](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**transporte >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a>Digite  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`clientCredentialType`|Especifica a credencial usada para autenticar o cliente para o serviço. Este atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Especifica a credencial usada para autenticar o cliente para um proxy de domínio. Este atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Uma cadeia de caracteres que especifica o realm de autenticação para Digest ou autenticação básica. O padrão é uma cadeia de caracteres vazia.<br /><br /> Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação. Ele também pode especificar uma coleção de usuários que tem acesso. Um usuário pode consultar o realm de autenticação para determinar que um dos vários nomes de usuário e senhas possíveis podem ser usados.|  
|`policyEnforcement`|Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser aplicado.<br /><br /> 1. nunca – a política nunca é imposta (a proteção estendida está desabilitada).<br />2. WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.<br />3. sempre – a política é sempre imposta. Os clientes que não dão suporte à proteção estendida não serão autenticados.|  
  
## <a name="clientcredentialtype-attribute"></a>Atributo clientCredentialtype  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|A segurança é desabilitada.|  
|`Basic`|Usa a autenticação básica.|  
|`Certificate`|Usa certificados X. 509 para autenticar o cliente.|  
|`Digest`|Usa a autenticação Digest.|  
|`Ntlm`|Usa a autenticação NTLM como um fallback com um domínio do Windows.|  
|`Windows`|Usa a autenticação integrada do Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>Atributo proxyCredentialType  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`None`|A segurança é desabilitada.|  
|`Basic`|Usa a autenticação básica.|  
|`Digest`|Usa a autenticação Digest.|  
|`Ntlm`|Usa NTLM como um fallback com um domínio do Windows.|  
|`Windows`|Usa a autenticação integrada do Windows.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Security >](security-of-webhttpbinding.md)|Representa os recursos de segurança do elemento [\<wsHttpBinding >](wshttpbinding.md) .|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
- [Modelo de programação HTTP Web do WCF](../../../wcf/feature-details/wcf-web-http-programming-model.md)
