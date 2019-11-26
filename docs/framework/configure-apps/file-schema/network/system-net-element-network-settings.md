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
ms.openlocfilehash: 810e942394c75c192e4423afe4c674ef3a2b9900
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697505"
---
# <a name="systemnet-element-network-settings"></a>\<Elemento system.Net> (configurações de rede)
Contém configurações que especificam como o .NET Framework se conecta à rede.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. net >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
 None.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|Especifica os módulos usados para autenticar solicitações da Internet.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Especifica o número máximo de conexões com um host de Internet.|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configura o servidor proxy HTTP (Hypertext Transfer Protocol).|  
|[mailSettings](mailsettings-element-network-settings.md)|Configura as opções de envio de email do protocolo SMTP.|  
|[requestCaching](requestcaching-element-network-settings.md)|Controla o mecanismo de cache para solicitações de rede.|  
|[settings](settings-element-network-settings.md)|Configura as opções básicas de rede para classes no <xref:System.Net> e namespaces filho relacionados.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Especifica os módulos a serem usados para solicitar informações de hosts da Internet.|  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[configuração](../configuration-element.md)|Contém configurações para todos os namespaces.|  
  
## <a name="remarks"></a>Comentários  
 O elemento [\<System. net >](system-net-element-network-settings.md) contém configurações para classes no <xref:System.Net> e namespaces filho relacionados. As configurações definem módulos de autenticação, gerenciamento de conexão, configurações de email, o servidor proxy e os módulos de solicitação da Internet para receber informações de hosts da Internet.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo a seguir mostra uma configuração típica usada pelas classes <xref:System.Net>.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações de rede](index.md)
