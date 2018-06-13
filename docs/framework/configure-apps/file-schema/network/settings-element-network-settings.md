---
title: '&lt;configurações&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3f717705a6cd4cc29fe333f5012c7fec466d350b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752472"
---
# <a name="ltsettingsgt-element-network-settings"></a>&lt;configurações&gt; elemento (configurações de rede)
Configura as opções de rede básicaspara o namespace <xref:System.Net?displayProperty=nameWithType>.  
  
 \<configuration>  
\<system.net>  
\<Configurações >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[HttpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|Personaliza os parâmetros usados pelo <xref:System.Net.HttpListener> classe.|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|Personaliza os parâmetros de solicitação da Web.|  
|[IPv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|Permite que o protocolo IP versão 6 (IPv6) oferecem suporte.|  
|[\<performanceCounter > elemento (configurações de rede)](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|Permite que os contadores de desempenho de rede.|  
|[servicePointManager](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|Configura conexões aos recursos da rede.|  
|[Soquete](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|Especifica se as operações de soquete usam portas de conclusão.|  
|[\<webProxyScript > elemento (configurações de rede)](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|Define as características do script usado para descobrir os proxies da Web.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Contém configurações que especificam como o .NET Framework se conecta à rede.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
