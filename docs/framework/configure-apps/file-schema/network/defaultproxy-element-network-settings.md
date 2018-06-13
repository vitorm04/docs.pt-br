---
title: '&lt;defaultProxy&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a91775ff9f46eba772a959cfac3115c9720ac5ab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742712"
---
# <a name="ltdefaultproxygt-element-network-settings"></a>&lt;defaultProxy&gt; elemento (configurações de rede)
Configura o servidor de proxy do protocolo HTTP (Hypertext Transfer).  
  
 \<configuration>  
\<system.net>  
\<defaultProxy >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|`enabled`|Especifica se um proxy da web é usado. O valor padrão é `true`.|  
|`useDefaultCredentials`|Especifica se as credenciais padrão para este host são usadas para acessar o proxy da web. O valor padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Fornece um conjunto de expressões regulares que descrevem os endereços que não usam o proxy.|  
|[Módulo](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|Adiciona um novo módulo de proxy para o aplicativo.|  
|[Proxy](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|Define um servidor proxy.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="remarks"></a>Comentários  
 Se o elemento defaultProxy estiver vazio, as configurações de proxy do Internet Explorer serão usadas. Esse comportamento é diferente da versão 1.1 do .NET Framework.  
  
 Uma exceção será lançada se o [módulo](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) elemento Especifica um tipo não público, o tipo não é derivada do <xref:System.Net.IWebProxy> classe, ocorreu uma exceção do construtor padrão do objeto ou uma exceção ocorreu enquanto Recuperando o proxy padrão do sistema especificado. O <xref:System.Exception.InnerException%2A> propriedade sobre a exceção deve ter mais informações sobre a causa do erro.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa os padrões do proxy do Internet Explorer, especifica o endereço de proxy e ignora o proxy para acesso local e contoso.com.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
