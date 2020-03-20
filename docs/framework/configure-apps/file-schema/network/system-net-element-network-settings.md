---
title: Elemento <system.Net> (configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154550"
---
# <a name="systemnet-element-network-settings"></a>\<Elemento system.Net> (configurações de rede)
Contém configurações que especificam como o .NET Framework se conecta à rede.  
  
[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|Especifica módulos usados para autenticar solicitações da Internet.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Especifica o número máximo de conexões a um host da Internet.|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Configura o servidor proxy Hypertext Transfer Protocol (HTTP).|  
|[Mailsettings](mailsettings-element-network-settings.md)|Configura opções de envio de e-mails do Simple Mail Transport Protocol (SMTP).|  
|[solicitaçãoCaching](requestcaching-element-network-settings.md)|Controla o mecanismo de cache para solicitações de rede.|  
|[configurações](settings-element-network-settings.md)|Configura opções básicas de <xref:System.Net> rede para classes nos espaços de nome de crianças relacionados.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Especifica módulos a serem usados para solicitar informações de hosts da Internet.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[configuração](../configuration-element.md)|Contém configurações para todos os namespaces.|  
  
## <a name="remarks"></a>Comentários  
 O [ \<elemento>system.net](system-net-element-network-settings.md) contém configurações para classes nos <xref:System.Net> espaços de nome de crianças e filhos relacionados. As configurações configuram módulos de autenticação, gerenciamento de conexão, configurações de e-mail, servidor proxy e módulos de solicitação da Internet para receber informações de hosts da Internet.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra <xref:System.Net> uma configuração típica usada pelas classes.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações de rede](index.md)
