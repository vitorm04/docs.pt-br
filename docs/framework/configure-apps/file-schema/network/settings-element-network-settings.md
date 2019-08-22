---
title: Elemento <settings> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: 12797e2f06d03aacd81700eae57d5776c1a6f354
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663988"
---
# <a name="settings-element-network-settings"></a>\<Elemento > Settings (configurações de rede)
Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.  
  
 \<configuration>  
\<system.net>  
\<> de configurações  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[httpListener](httplistener-element-network-settings.md)|Personaliza os <xref:System.Net.HttpListener> parâmetros usados pela classe.|  
|[httpWebRequest](httpwebrequest-element-network-settings.md)|Personaliza os parâmetros de solicitação da Web.|  
|[ipv6](ipv6-element-network-settings.md)|Habilita o suporte a IPv6 (protocolo IP versão 6).|  
|[\<performanceCounter > elemento (configurações de rede)](performancecounter-element-network-settings.md)|Habilita contadores de desempenho de rede.|  
|[servicePointManager](servicepointmanager-element-network-settings.md)|Configura conexões com recursos de rede.|  
|[socket](socket-element-network-settings.md)|Especifica se as operações de soquete usam portas de conclusão.|  
|[\<Elemento de > webProxyScript (configurações de rede)](webproxyscript-element-network-settings.md)|Configura as características do script usado para descobrir proxies da Web.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
