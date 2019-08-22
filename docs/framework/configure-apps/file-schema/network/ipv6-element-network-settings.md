---
title: Elemento <ipv6> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: d89c2e2c6943aca38f8a71092ba3121447a77574
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664092"
---
# <a name="ipv6-element-network-settings"></a>\<Elemento ipv6> (configurações de rede)
Habilita respostas de IPv6 (protocolo IP versão 6) de membros obsoletos <xref:System.Net.Dns> da classe.  
  
 \<configuration>  
\<system.net>  
\<> de configurações  
\<ipv6>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`enabled`|Especifica se os membros da <xref:System.Net.Dns> classe retornam endereços IPv6 (protocolo IP versão 6). O valor padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
 Essa configuração habilita <xref:System.Net.Dns> o suporte a IPv6 para os membros obsoletos da classe <xref:System.Net.Dns.BeginResolve%2A>: <xref:System.Net.Dns.EndGetHostByName%2A> <xref:System.Net.Dns.GetHostByName%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>,,,, <xref:System.Net.Dns.Resolve%2A>e. Para outros membros do <xref:System.Net?displayProperty=nameWithType> namespace, os endereços IPv6 podem ser retornados se o IPv6 estiver habilitado no sistema operacional.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como habilitar o suporte a IPv6 <xref:System.Net.Dns> para a classe.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
