---
title: '&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1f041cbfb4195b2c649c3af4fa061bf63e227df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754282"
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a>&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; elemento
Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.  
  
 \<configuration>  
\<runtime>  
\<forcePerformanceCounterUniqueSharedMemoryReads >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Indica se PerfCounter.dll usa a configuração de registro CategoryOptions para determinar se deve carregar dados de contador de desempenho da memória compartilhada específicas de categoria ou memória global.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|PerfCounter.dll não usa o CategoryOptions essa configuração de registro é o padrão.|  
|`true`|PerfCounter.dll usar a configuração de registro de CategoryOptions.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Em versões do .NET Framework antes do [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], correspondia a versão do PerfCounter.dll que foi carregado no tempo de execução que foi carregado no processo. Se um computador tiver o .NET Framework versão 1.1 e o [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] instalado, um aplicativo do .NET Framework 1.1 carrega a versão do .NET Framework 1.1 do PerfCounter.dll. Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a versão instalada mais recente do PerfCounter.dll é carregada. Isso significa que um aplicativo do .NET Framework 1.1 carregará o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] versão do PerfCounter.dll se o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] está instalado no computador.  
  
 Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], durante o consumo de contadores de desempenho, PerfCounter.dll verifica a entrada de registro CategoryOptions para cada provedor determinar se ele deve ler de memória compartilhada específicas de categoria ou a memória compartilhada global. O PerfCounter.dll do .NET Framework 1.1 não lê essa entrada do registro, porque ele não está ciente de categoria específica memória compartilhada; ele sempre lê da memória compartilhada global.  
  
 Para compatibilidade com versões anteriores, o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll não verifica a entrada de registro CategoryOptions quando executada em um aplicativo do .NET Framework 1.1. Ele simplesmente usa a memória compartilhada global, como o PerfCounter.dll do .NET Framework 1.1. No entanto, você pode instruir o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll para verificar a configuração do registro, permitindo que o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento.  
  
> [!NOTE]
>  Habilitando o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento não garante que a memória compartilhada específicas de categoria será usada. Configuração habilitada para `true` só faz com que PerfCounter.dll referenciar a configuração de registro CategoryOptions. A configuração padrão para CategoryOptions é usar a memória compartilhada específicas de categoria; No entanto, você pode alterar CategoryOptions para indicar que a memória compartilhada global deve ser usada.  
  
 A chave do registro que contém a configuração CategoryOptions é HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. Por padrão, CategoryOptions é definido como 3, que instrui o PerfCounter.dll para uso de memória compartilhada específicas de categoria. Se CategoryOptions for definido como 0, PerfCounter.dll usa a memória compartilhada global. Dados da instância serão reutilizados somente se o nome da instância que está sendo criado é idêntico à instância que está sendo reutilizada. Todas as versões será capazes de gravar na categoria. Se CategoryOptions for definido como 1, a memória compartilhada global é usada, mas os dados de instância podem ser reutilizados se o nome da categoria é o mesmo comprimento que a categoria que está sendo reutilizado.  
  
 As configurações de 0 e 1 podem levar a vazamentos de memória e preenchimento de memória do contador de desempenho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar se PerfCounter.dll devem fazer referência a entrada de registro CategoryOptions para determinar se deve usar a memória compartilhada específicas de categoria.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
