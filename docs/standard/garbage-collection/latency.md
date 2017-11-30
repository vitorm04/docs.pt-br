---
title: "Modos de latência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 439fdd8fe78a0c0f0fda4ac7e759a4a780bb9b58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="latency-modes"></a>Modos de latência
Para recuperar objetos, o coletor de lixo deve interromper todos os threads em execução em um aplicativo. Em algumas situações, como quando um aplicativo recupera dados ou exibe conteúdo, uma coleta de lixo completa pode ocorrer em um momento crítico e impedir o desempenho. Você pode ajustar o risco de invasão do coletor de lixo, definindo o <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> propriedade para um do <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> valores.  
  
 A latência refere-se à hora em que o coletor de lixo invade seu aplicativo. Durante períodos de baixa latência, o coletor de lixo é mais conservador e menos intrusivo na recuperação de objetos. O <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> enumeração fornece duas configurações de baixa latência:  
  
-   <xref:System.Runtime.GCLatencyMode.LowLatency>Suprime a coleções de geração 2 e executa somente as coleções de geração 0 e 1. Ela pode ser usada somente por curtos períodos. Em períodos mais longos, se o sistema estiver sob pressão de memória, o coletor de lixo disparará uma coleção, que pode pausar o aplicativo rapidamente e interromper uma operação de tempo crítico. Essa configuração está disponível somente para coleta de lixo de estação de trabalho.  
  
-   <xref:System.Runtime.GCLatencyMode.SustainedLowLatency>Suprime a coleções de geração 2 em primeiro plano e executa somente a primeira geração 0, 1 e coleções de 2ª geração de plano de fundo. Ela pode ser usada por longos períodos e está disponível para coleta de lixo de estação de trabalho e servidor. Essa configuração não poderá ser usada se a [coleta de lixo simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) estiver desabilitada.  
  
 Durante períodos de baixa latência, coletas da geração 2 são suprimidas, a menos que ocorra o seguinte:  
  
-   O sistema recebe uma notificação de falta de memória do sistema operacional.  
  
-   O código do aplicativo induzir a uma coleção, chamando o <xref:System.GC.Collect%2A?displayProperty=nameWithType> método e especificar 2 para o `generation` parâmetro.  
  
 A tabela a seguir lista os cenários de aplicativo para usar o <xref:System.Runtime.GCLatencyMode> valores.  
  
|Modo de latência|Cenários de aplicativo|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Para aplicativos que não têm operações de interface do usuário ou do servidor.<br /><br /> Este é o modo padrão quando a [coleta de lixo simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) está desabilitada.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Para a maioria dos aplicativos que têm uma interface do usuário.<br /><br /> Este é o modo padrão quando a [coleta de lixo simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) está habilitada.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Para aplicativos que têm operações de curto prazo, sensíveis ao tempo, durante o qual as interrupções do coletor de lixo podem ser prejudiciais. Por exemplo, os aplicativos com funções de aquisição de dados ou renderização de animação.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Para aplicativos que têm operações sensíveis ao tempo, por uma duração contida, mas potencialmente maior, durante a qual as interrupções do coletor de lixo poderiam ser prejudiciais. Por exemplo, aplicativos que precisam de tempos de resposta rápidos, como alterações de dados de mercado durante o horário comercial.<br /><br /> Esse modo resulta em um tamanho maior do heap gerenciado do que outros modos. Como ele não compacta o heap gerenciado, é possível maior fragmentação. Verifique se há memória suficiente disponível.|  
  
## <a name="guidelines-for-using-low-latency"></a>Diretrizes para uso de baixa latência  
 Quando você usa <xref:System.Runtime.GCLatencyMode.LowLatency> modo, considere as seguintes diretrizes:  
  
-   Mantenha o período de baixa latência o mais curto possível.  
  
-   Evite a alocação de grande quantidade de memória durante períodos de baixa latência. Notificações de memória insuficiente podem ocorrer porque a coleta de lixo recupera menos objetos.  
  
-   No modo de baixa latência, minimize o número de alocações feitas, principalmente alocações em heap de objetos grandes e objetos fixados.  
  
-   Esteja atento a ameaças que possam ser alocadas. Porque o <xref:System.Runtime.GCSettings.LatencyMode%2A> configuração da propriedade é todo o processo, você pode gerar um <xref:System.OutOfMemoryException> em qualquer thread que pode ser alocar.  
  
-   Encapsular o código de baixa latência em regiões de execução restrita (para obter mais informações, consulte [regiões de execução restrita](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
-   Você pode forçar a coleções de geração 2 durante um período de baixa latência ao chamar o <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> método.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.GC?displayProperty=nameWithType>  
 [Coletas Induzidas](../../../docs/standard/garbage-collection/induced.md)  
 [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
