---
title: '&lt;performanceCounters&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 64afd62c6eeca7bce14e331fdc65fccfa3d02bce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltperformancecountersgt-element"></a>&lt;performanceCounters&gt; elemento
Especifica o tamanho da memória global compartilhada por contadores de desempenho.  
  
 \<configuration>  
\<System. Diagnostics >  
\<performanceCounters >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|filemappingsize|Atributo obrigatório.<br /><br /> Especifica o tamanho, em bytes, da memória global compartilhado por contadores de desempenho. O padrão é 524288.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`Configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica o elemento raiz para a seção de configuração do ASP.NET.|  
  
## <a name="remarks"></a>Comentários  
 Contadores de desempenho de usam um arquivo de memória mapeada ou memória compartilhada, para publicar dados de desempenho.  O tamanho da memória compartilhada determina quantas instâncias podem ser usadas uma vez.  Há dois tipos de memória compartilhada: compartilhada global de memória e memória compartilhada separada.  A memória compartilhada global é usada por todas as categorias de contador de desempenho instaladas com o .NET Framework versão 1.0 ou 1.1.  Categorias de contador de desempenho instaladas com o .NET Framework versão 2.0 usam memória compartilhada separada, com cada categoria de contador de desempenho com sua própria memória.  
  
 O tamanho de memória compartilhada global pode ser definido somente com um arquivo de configuração.  O tamanho padrão é 524.288 bytes, o tamanho máximo é 33,554,432 bytes e o tamanho mínimo é 32.768 bytes.  Desde que a memória compartilhada global é compartilhada por todos os processos e categorias, o criador do primeiro especifica o tamanho.  Se você definir o tamanho em seu arquivo de configuração do aplicativo, esse tamanho só será usado se o aplicativo é o primeiro aplicativo que faz com que os contadores de desempenho executar.  Portanto, o local correto para especificar o `filemappingsize` valor é o arquivo Machine. config.  Não é possível liberar memória na memória compartilhada global por individuais contadores de desempenho, portanto, eventualmente, a memória compartilhada global seja exaurida se um grande número de instâncias de contador de desempenho com nomes diferentes é criado.  
  
 O tamanho de memória compartilhada separada, o valor de DWORD FileMappingSize no registro chave HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<nome da categoria >*\Performance é referenciado primeiro, seguido pelo valor especificado para a memória compartilhada global no arquivo de configuração. Se o valor de FileMappingSize não existir, o tamanho de memória compartilhada separada é definido como um quarto (1/4) a configuração global no arquivo de configuração.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
