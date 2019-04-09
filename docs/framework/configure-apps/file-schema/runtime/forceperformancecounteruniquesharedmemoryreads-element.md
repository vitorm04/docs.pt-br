---
title: <forcePerformanceCounterUniqueSharedMemoryReads> Elemento
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d4a205f643c844b2fe77d3aa5211b4bc1f322fd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186960"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads > elemento
Especifica se o PerfCounter.dll usa a configuração de registro CategoryOptions em um aplicativo do .NET Framework versão 1.1 para determinar se é preciso carregar dados do contador de desempenho da memória global ou da memória compartilhada especifica da categoria.  
  
 \<configuration>  
\<runtime>  
\<forcePerformanceCounterUniqueSharedMemoryReads>  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Indica se o PerfCounter usa a configuração do registro CategoryOptions para determinar se deve carregar dados do contador de desempenho da memória global ou categoria específica memória compartilhada.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|PerfCounter não usa o CategoryOptions essa configuração de registro é o padrão.|  
|`true`|Usa a configuração do registro CategoryOptions PerfCounter.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Nas versões do .NET Framework antes do [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], a versão do PerfCounter que foi carregado correspondia ao tempo de execução que foi carregado no processo. Se um computador tiver o .NET Framework versão 1.1 e o [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] instalado, um aplicativo do .NET Framework 1.1 carregaria a versão do .NET Framework 1.1 de PerfCounter. Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a versão instalada mais recente de PerfCounter é carregada. Isso significa que um aplicativo do .NET Framework 1.1 carregará os [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] versão do PerfCounter se o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] está instalado no computador.  
  
 Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], ao consumir contadores de desempenho, PerfCounter verifica a entrada do registro CategoryOptions para cada provedor determinar se ele deve ler da categoria específica memória compartilhada ou memória compartilhada global. O PerfCounter do .NET Framework 1.1 não lê essa entrada de registro, porque ele não está ciente da categoria específica memória compartilhada; ele sempre lê na memória compartilhada global.  
  
 Para compatibilidade com versões anteriores, o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter não verifica a entrada do registro CategoryOptions quando em execução em um aplicativo do .NET Framework 1.1. Ela simplesmente usa a memória compartilhada global, assim como o PerfCounter do .NET Framework 1.1. No entanto, você pode instruir o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter para verificar a configuração do registro, habilitando o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento.  
  
> [!NOTE]
>  Habilitando o `<forcePerformanceCounterUniqueSharedMemoryReads>` elemento não garante que a categoria específica memória compartilhada será usada. Configuração habilitada para `true` apenas faz com que o PerfCounter fazer referência a configuração do registro CategoryOptions. A configuração padrão para CategoryOptions é usar a categoria memória compartilhada; No entanto, você pode alterar CategoryOptions para indicar que a memória compartilhada global deve ser usada.  
  
 A chave do registro que contém a configuração CategoryOptions é HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance. Por padrão, CategoryOptions é definido como 3, que instrui o PerfCounter usar memória compartilhada de categoria específico. Se CategoryOptions for definido como 0, o PerfCounter usa memória global compartilhada. Dados da instância serão reutilizados somente se o nome da instância que está sendo criado é idêntico à instância que está sendo reutilizada. Todas as versões será capazes de gravar na categoria. Se CategoryOptions for definido como 1, memória compartilhada global é usada, mas os dados de instância podem ser reutilizados se o nome da categoria é o mesmo tamanho que a categoria que está sendo reutilizado.  
  
 As configurações de 0 e 1 podem levar a vazamentos de memória e preenchimento de memória do contador de desempenho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar se PerfCounter devem fazer referência a entrada do registro CategoryOptions para determinar se ele deve usar a memória compartilhada de categoria específico.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
