---
title: <transport> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: ce8b2acb7d87b094958e20ca0b6cca9fc8266a8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911980"
---
# <a name="transport-of-ws2007httpbinding"></a>\<> de transporte \<do ws2007HttpBinding >
Define as configurações de autenticação para o transporte HTTP.  
  
 \<system.serviceModel>  
\<bindings>  
\<ws2007HttpBinding>  
\<> de associação  
\<> de segurança  
\<> de transporte  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a>Tipo  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`clientCredentialType`|Especifica a credencial usada para autenticar o cliente para o serviço. Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Especifica a credencial usada para autenticar o cliente para um proxy de domínio. Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|O realm de autenticação para Digest ou autenticação básica. O padrão é uma cadeia de caracteres vazia.<br /><br /> Um realm de autenticação especifica pelo menos o nome do host que executa a autenticação. Ele também pode especificar uma coleção de usuários que têm acesso. Um usuário pode consultar o realm de autenticação para determinar qual um dos vários nomes de usuário e senhas possíveis podem ser usados.|  
  
## <a name="clientcredentialtype-attribute"></a>Atributo clientCredentialtype  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|A segurança é desabilitada.|  
|Basic|Usa a autenticação básica.|  
|Digest|Usa a autenticação Digest.|  
|NTLM|Usa a autenticação NTLM como um fallback com um domínio do Windows.|  
|Windows|Usa a autenticação integrada do Windows.|  
|Certificate|Usa certificados X. 509 para autenticar o cliente.|  
  
## <a name="proxycredentialtype-attribute"></a>Atributo proxyCredentialType  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|A segurança é desabilitada.|  
|Basic|Usa a autenticação básica.|  
|Digest|Usa a autenticação Digest.|  
|NTLM|Usa NTLM como um fallback com um domínio do Windows.|  
|Windows|Usa a autenticação integrada do Windows.|  
|Certificate|Usa certificados X. 509 para autenticar o cliente.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|Representa os recursos de segurança do [ \<elemento > ws2007HttpBinding](ws2007httpbinding.md) .|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
