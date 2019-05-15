---
title: Modos de latência
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a81a0015ae046682e1afa40c1c8d272357839ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622769"
---
# <a name="latency-modes"></a>Modos de latência
Para recuperar objetos, o coletor de lixo deve interromper todos os threads em execução em um aplicativo. Em algumas situações, como quando um aplicativo recupera dados ou exibe conteúdo, uma coleta de lixo completa pode ocorrer em um momento crítico e impedir o desempenho. Você pode ajustar a intrusão do coletor de lixo, definindo a propriedade <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> como um dos valores <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>.  
  
 A latência refere-se à hora em que o coletor de lixo invade seu aplicativo. Durante períodos de baixa latência, o coletor de lixo é mais conservador e menos intrusivo na recuperação de objetos. A enumeração <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> fornece duas configurações de baixa latência:  
  
- <xref:System.Runtime.GCLatencyMode.LowLatency> suprime coletas da geração 2 e executa somente coletas da geração 0 e 1. Ela pode ser usada somente por curtos períodos. Em períodos mais longos, se o sistema estiver sob pressão de memória, o coletor de lixo disparará uma coleção, que pode pausar o aplicativo rapidamente e interromper uma operação de tempo crítico. Essa configuração está disponível somente para coleta de lixo de estação de trabalho.  
  
- <xref:System.Runtime.GCLatencyMode.SustainedLowLatency> suprime coletas da geração 2 em primeiro plano e executa somente a geração 0, 1 e coletas da geração 2 em segundo plano. Ela pode ser usada por longos períodos e está disponível para coleta de lixo de estação de trabalho e servidor. Essa configuração não poderá ser usada se a [coleta de lixo simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) estiver desabilitada.  
  
 Durante períodos de baixa latência, coletas da geração 2 são suprimidas, a menos que ocorra o seguinte:  
  
- O sistema recebe uma notificação de falta de memória do sistema operacional.  
  
- O código do aplicativo induz uma coleção chamando o método <xref:System.GC.Collect%2A?displayProperty=nameWithType> e especificando 2 para o parâmetro `generation`.  
  
 A tabela a seguir lista os cenários de aplicativo para uso dos valores <xref:System.Runtime.GCLatencyMode>.  
  
|Modo de latência|Cenários de aplicativo|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|Para aplicativos que não têm operações de interface do usuário ou do servidor.<br /><br /> Este é o modo padrão quando a [coleta de lixo simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) está desabilitada.|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|Para a maioria dos aplicativos que têm uma interface do usuário.<br /><br /> Este é o modo padrão quando a [coleta de lixo simultânea](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) está habilitada.|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|Para aplicativos que têm operações de curto prazo, sensíveis ao tempo, durante o qual as interrupções do coletor de lixo podem ser prejudiciais. Por exemplo, os aplicativos com funções de aquisição de dados ou renderização de animação.|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|Para aplicativos que têm operações sensíveis ao tempo, por uma duração contida, mas potencialmente maior, durante a qual as interrupções do coletor de lixo poderiam ser prejudiciais. Por exemplo, aplicativos que precisam de tempos de resposta rápidos, como alterações de dados de mercado durante o horário comercial.<br /><br /> Esse modo resulta em um tamanho maior do heap gerenciado do que outros modos. Como ele não compacta o heap gerenciado, é possível maior fragmentação. Verifique se há memória suficiente disponível.|  
  
## <a name="guidelines-for-using-low-latency"></a>Diretrizes para uso de baixa latência  
 Ao usar o modo <xref:System.Runtime.GCLatencyMode.LowLatency>, considere as seguintes diretrizes:  
  
- Mantenha o período de baixa latência o mais curto possível.  
  
- Evite a alocação de grande quantidade de memória durante períodos de baixa latência. Notificações de memória insuficiente podem ocorrer porque a coleta de lixo recupera menos objetos.  
  
- No modo de baixa latência, minimize o número de alocações feitas, principalmente alocações em heap de objetos grandes e objetos fixados.  
  
- Esteja atento a ameaças que possam ser alocadas. Como a configuração da propriedade <xref:System.Runtime.GCSettings.LatencyMode%2A> é de todo o processo, você pode gerar uma <xref:System.OutOfMemoryException> em qualquer thread que possa ser alocado.  
  
- Encapsule o código de baixa latência em regiões de execução restrita (para saber mais, confira [Regiões de execução restrita](../../../docs/framework/performance/constrained-execution-regions.md)).  
  
- Você pode forçar coletas da geração 2 durante um período de baixa latência ao chamar o método <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.GC?displayProperty=nameWithType>
- [Coletas Induzidas](../../../docs/standard/garbage-collection/induced.md)
- [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
