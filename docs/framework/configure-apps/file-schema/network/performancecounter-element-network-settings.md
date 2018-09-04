---
title: '&lt;performanceCounter&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 564cef8ae53bf4a455a2e8032a296aa36e309917
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517506"
---
# <a name="ltperformancecountergt-element-network-settings"></a>&lt;performanceCounter&gt; (configurações de rede)
Habilita ou desabilita os contadores de desempenho de rede.  
  
 \<configuration>  
\<system.net>  
\<Configurações >  
\<performanceCounters >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Especifica se os contadores de desempenho de rede estão habilitados. O valor padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
 Contadores de desempenho de rede precisam ser habilitados no arquivo de configuração a ser usado. Todos os contadores de desempenho de rede são habilitados ou desabilitados com uma única configuração no arquivo de configuração. Contadores de desempenho de rede individuais não podem ser habilitados nem desabilitados. Para obter mais informações sobre os contadores de desempenho de rede específicos, consulte [contadores de desempenho de rede](https://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).  
  
 O valor padrão é o desempenho de rede que os contadores estão desabilitados.  
  
 O <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do **habilitado** atributo dos arquivos de configuração aplicáveis.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar o <xref:System.Net> e namespaces para habilitar os contadores de desempenho de rede relacionados.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [Contadores de desempenho de rede](https://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
