---
title: Eventos ETW de coleta de lixo
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149728"
---
# <a name="garbage-collection-etw-events"></a>Eventos ETW de coleta de lixo
<a name="top"></a> Esses eventos coletam informações referentes à coleta de lixo. Eles ajudam no diagnóstico e na depuração, inclusive determinando quantas vezes a coleta de lixo foi executada, a quantidade de memória liberada durante a coleta de lixo e assim por diante.  
  
 Esta categoria consiste nos seguintes eventos:  
  
-   [Evento GCStart_V1](#gcstart_v1_event)  
  
-   [Evento GCEnd_V1](#gcend_v1_event)  
  
-   [Evento GCHeapStats_V1](#gcheapstats_v1_event)  
  
-   [Evento GCCreateSegment_V1](#gccreatesegment_v1_event)  
  
-   [Evento GCFreeSegment_V1](#gcfreesegment_v1_event)  
  
-   [Evento GCRestartEEBegin_V1](#gcrestarteebegin_v1_event)  
  
-   [Evento GCRestartEEEnd_V1](#gcrestarteeend_v1_event)  
  
-   [Evento GCSuspendEE_V1](#gcsuspendee_v1_event)  
  
-   [Evento GCSuspendEEEnd_V1](#gcsuspendeeend_v1_event)  
  
-   [Evento GCAllocationTick_V2](#gcallocationtick_v2_event)  
  
-   [Evento GCFinalizersBegin_V1](#gcfinalizersbegin_v1_event)  
  
-   [Evento GCFinalizersEnd_V1](#gcfinalizersend_v1_event)  
  
-   [Evento GCCreateConcurrentThread_V1](#gccreateconcurrentthread_v1_event)  
  
-   [Evento GCTerminateConcurrentThread_V1](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>Evento GCStart_V1  
 A tabela a seguir mostra a palavra-chave e o nível. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1|Uma coleta de lixo foi iniciada.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Contagem|win:UInt32|O *n*ª coleta de lixo.|  
|Profundidade|win:UInt32|A geração que está sendo coletada.|  
|Motivo|win:UInt32|Motivo do gatilho da coleta de lixo:<br /><br /> 0x0 – Alocação de heap de objetos pequenos.<br /><br /> 0x1 – Induzido.<br /><br /> 0x2 – Memória insuficiente.<br /><br /> 0x3 – Vazio.<br /><br /> 0x4 – Alocação de heap de objetos grandes.<br /><br /> 0x5 – Espaço insuficiente (para heap de objetos pequenos).<br /><br /> 0x6 – Espaço insuficiente (para heap de objetos grandes).<br /><br /> 0x7 – Induzido, mas não forçado como bloqueio.|  
|Tipo|win:UInt32|0x0 – A coleta de lixo de bloqueio ocorreu fora da coleta de lixo em segundo plano.<br /><br /> 0x1 – Coleta de lixo em segundo plano.<br /><br /> 0x2 – A coleta de lixo de bloqueio ocorreu durante a coleta de lixo em segundo plano.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>Evento GCEnd_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|A coleta de lixo foi encerrada.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Contagem|win:UInt32|O *n*ª coleta de lixo.|  
|Profundidade|win:UInt32|A geração que foi coletada.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>Evento GCHeapStats_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Descrição|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|Mostra as estatísticas de heap no final de cada coleta de lixo.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|GenerationSize0|win:UInt64|O tamanho, em bytes, da memória de geração 0.|  
|TotalPromotedSize0|win:UInt64|O número de bytes que são promovidos da geração 0 para a geração 1.|  
|GenerationSize1|win:UInt64|O tamanho, em bytes, da memória de geração 1.|  
|TotalPromotedSize1|win:UInt64|O número de bytes que são promovidos da geração 1 para a geração 2.|  
|GenerationSize2|win:UInt64|O tamanho, em bytes, da memória de geração 2.|  
|TotalPromotedSize2|win:UInt64|O número de bytes que sobreviveram na geração 2 após a última coleta.|  
|GenerationSize3|win:UInt64|O tamanho, em bytes, do heap de objetos grandes.|  
|TotalPromotedSize3|win:UInt64|O número de bytes que sobreviveram no heap de objetos grandes após a última coleta.|  
|FinalizationPromotedSize|win:UInt64|O tamanho total, em bytes, dos objetos que estão prontos para finalização.|  
|FinalizationPromotedCount|win:UInt64|O número de objetos que estão prontos para finalização.|  
|PinnedObjectCount|win:UInt32|O número de objetos (imóveis) fixados.|  
|SinkBlockCount|win:UInt32|O número de blocos de sincronização em uso.|  
|GCHandleCount|win:UInt32|O número de manipuladores de coleta de lixo em uso.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>Evento GCCreateSegment_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|Um novo segmento de coleta de lixo foi criado. Além disso, quando o rastreamento é habilitado em um processo que já está em execução, esse evento é acionado para cada segmento existente.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Endereço|win:UInt64|O endereço do segmento.|  
|Tamanho|win:UInt64|O tamanho do segmento.|  
|Tipo|win:UInt32|0x0 – Heap de objetos pequenos.<br /><br /> 0x1 – Heap de objetos grandes.<br /><br /> 0x2 – Heap somente leitura.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 Observe que o tamanho de segmentos alocados pelo coletor de lixo é específico à implementação e está sujeito a alterações a qualquer momento, incluindo em atualizações periódicas. Seu aplicativo nunca deve fazer suposições sobre o tamanho de um segmento em particular nem depender dele, tampouco deve tentar configurar a quantidade de memória disponível para alocações de segmento.  
  
 [Voltar ao início](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>Evento GCFreeSegment_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|Um segmento de coleta de lixo foi liberado.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Endereço|win:UInt64|O endereço do segmento.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>Evento GCRestartEEBegin_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|A continuidade da suspensão do Common Language Runtime foi iniciada.|  
  
 Nenhum dado do evento.  
  
 [Voltar ao início](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>Evento GCRestartEEEnd_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|A continuidade da suspensão do Common Language Runtime foi encerrada.|  
  
 Nenhum dado do evento.  
  
 [Voltar ao início](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>Evento GCSuspendEE_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|Início da suspensão do mecanismo de execução da coleta de lixo.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Motivo|win:UInt16|0x0 – Outros.<br /><br /> 0x1 – Coleta de lixo.<br /><br /> 0x2 – Desligamento do domínio do aplicativo.<br /><br /> 0x3 – Densidade do código.<br /><br /> 0x4 – Desligamento.<br /><br /> 0x5 – Depurador.<br /><br /> 0x6 – Preparação para a coleta de lixo.|  
|Contagem|win:UInt32|A contagem de GC no momento. Normalmente, você verá um evento de Início de GC posterior depois disso e sua Contagem será essa Contagem + 1, conforme aumentamos o Índice de GC durante uma coleta de lixo.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>Evento GCSuspendEEEnd_V1  
 A seguinte tabela mostra a palavra-chave e o nível:  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A seguinte tabela mostra as informações do evento:  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|Fim da suspensão do mecanismo de execução da coleta de lixo.|  
  
 Nenhum dado do evento.  
  
 [Voltar ao início](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>Evento GCAllocationTick_V2  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|A cada vez, aproximadamente 100 KB são alocados.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|AllocationAmount|win:UInt32|O tamanho de alocação, em bytes. Esse valor é preciso para alocações menores do que o tamanho de um ULONG (4.294.967.295 bytes). Se a alocação for maior, esse campo conterá um valor truncado. Use `AllocationAmount64` para alocações muito grandes.|  
|AllocationKind|win:UInt32|0x0 – Alocação de objeto pequeno (a alocação está no heap de objetos pequenos).<br /><br /> 0x1 – Alocação de objeto grande (a alocação está no heap de objetos grandes).|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
|AllocationAmount64|win:UInt64|O tamanho de alocação, em bytes. Esse valor é preciso para alocações muito grandes.|  
|TypeId|win:Pointer|O endereço da MethodTable. Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o endereço da MethodTable que corresponde ao último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).|  
|NomeDoTipo|win:UnicodeString|O nome do tipo que foi alocado. Quando há vários tipos de objetos que foram alocados durante esse evento, esse é o tipo do último objeto alocado (o objeto que fez com que o limite de 100 KB fosse excedido).|  
|HeapIndex|win:UInt32|O heap em que o objeto foi alocado. Esse valor é 0 (zero) durante a execução da coleta de lixo da estação de trabalho.|  
  
 [Voltar ao início](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>Evento GCFinalizersBegin_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|O início da execução dos finalizadores.|  
  
 Nenhum dado do evento.  
  
 [Voltar ao início](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>Evento GCFinalizersEnd_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|O fim da execução dos finalizadores.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Contagem|win:UInt32|O número de finalizadores que foram executados.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>Evento GCCreateConcurrentThread_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
|`ThreadingKeyword` (0x10000)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|O thread da coleta de lixo simultânea foi criado.|  
  
 Nenhum dado do evento.  
  
 [Voltar ao início](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>Evento GCTerminateConcurrentThread_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativo (4)|  
|`ThreadingKeyword` (0x10000)|Informativo (4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|O thread da coleta de lixo simultânea foi terminado.|  
  
 Nenhum dado do evento.  
  
## <a name="see-also"></a>Consulte também

- [Eventos ETW no CLR](../../../docs/framework/performance/clr-etw-events.md)
