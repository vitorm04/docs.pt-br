---
title: '&lt;bypasslist&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d2076ee5e95ab722fe828ee625392671a6281c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbypasslistgt-element-network-settings"></a>&lt;bypasslist&gt; elemento (configurações de rede)
Fornece um conjunto de expressões regulares que descrevem os endereços que não usam um proxy.  
  
 \<configuration>  
\<system.net>  
\<defaultProxy >  
\<bypasslist >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|Adiciona um endereço IP ou nome DNS para a lista de proxies.|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|Limpa a lista de bypass.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|Remove a lista de proxies um endereço IP ou nome DNS.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Configura o servidor de proxy do protocolo HTTP (Hypertext Transfer).|  
  
## <a name="remarks"></a>Comentários  
 A lista de bypass contém expressões regulares que descrevem os URIs que <xref:System.Net.WebRequest> instâncias acessar diretamente em vez de por meio do servidor proxy.  
  
 Você deve ter cuidado ao especificar uma expressão regular para este elemento. A expressão regular "[a-z] +\\.contoso\\.com" corresponde a qualquer host no domínio contoso.com, mas também corresponde a qualquer host no domínio contoso.com.cpandl.com. Para corresponder a um host no domínio contoso.com, use uma âncora ("$"): "[a-z] +\\.contoso\\.com$".  
  
 Para obter mais informações sobre expressões regulares, consulte. [Expressões regulares do .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir adiciona dois endereços à lista de bypass. O primeiro ignora o proxy para todos os servidores no domínio contoso.com; o segundo ignora o proxy para todos os servidores cujos endereços IP começam com 192.168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
