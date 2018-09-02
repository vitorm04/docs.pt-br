---
title: Eventos ETW no CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 983c38567667da911132217dcfda37c009dc833c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423479"
---
# <a name="clr-etw-events"></a>Eventos ETW no CLR
Os tópicos desta seção descrevem os eventos ETW (rastreamento de eventos para Windows). Cada evento tem uma palavra-chave e um nível associados, que são descritos no tópico [Palavras-chave e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md). O CLR tem dois provedores para os eventos:  
  
-   O provedor de tempo de execução, que aciona eventos, dependendo de quais palavras-chave (categorias de eventos) são habilitadas. O GUID do provedor de tempo de execução CLR é e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
-   O provedor de encerramento, que tem usos de finalidade especial. O GUID do provedor de encerramento CLR é a669021c-c450-4609-a035-5af59af4df18.  
  
 Para obter mais informações sobre os provedores, consulte [Provedores CLR ETW](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Eventos de informações de tempo de execução](../../../docs/framework/performance/runtime-information-etw-events.md)  
 Captura informações sobre o tempo de execução, incluindo a SKU, o número de versão, a maneira pela qual o tempo de execução foi ativado, os parâmetros de linha de comando com os quais ele foi iniciado, o GUID (se aplicável) e outras informações relevantes.  
  
 [Evento Exception Thrown_V1](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Captura informações sobre as exceções geradas.  
  
 [Eventos de contenção](../../../docs/framework/performance/contention-etw-events.md)  
 Captura informações sobre a contenção de bloqueios do monitor ou bloqueios nativos usados pelo tempo de execução.  
  
 [Eventos de pool de threads](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Captura informações sobre pools de threads de trabalho e pools de threads de E/S.  
  
 [Eventos de carregador](../../../docs/framework/performance/loader-etw-events.md)  
 Captura informações sobre o carregamento e descarregamento de domínios do aplicativo, assemblies e módulos.  
  
 [Eventos de método](../../../docs/framework/performance/method-etw-events.md)  
 Captura informações sobre métodos CLR para a resolução de símbolo.  
  
 [Eventos de coleta de lixo](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Captura informações referentes à coleta de lixo, para ajudar no diagnóstico e na depuração.  
  
 [Eventos de rastreamento JIT](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Captura informações sobre chamadas inlining e tail JIT (Just-In-Time).  
  
 [Eventos de interoperabilidade](../../../docs/framework/performance/interop-etw-events.md)  
 Captura informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).  
  
 [Eventos de ARM](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Captura informações de diagnóstico detalhadas sobre o estado de um domínio do aplicativo.  
  
 [Eventos de segurança](../../../docs/framework/performance/security-etw-events.md)  
 Captura informações sobre o nome forte e a verificação do Authenticode.  
  
 [Evento de pilha](../../../docs/framework/performance/stack-etw-event.md)  
 Captura informações que são usadas com outros eventos para gerar rastreamentos de pilha depois que um evento é acionado.  
  
## <a name="see-also"></a>Consulte também  
 [Melhorar a depuração e ajuste de desempenho com o ETW](https://go.microsoft.com/fwlink/?LinkId=179696)  
 [Blog de desempenho do Windows](https://go.microsoft.com/fwlink/?LinkId=179509)  
 [Controlando o log no .NET Framework](../../../docs/framework/performance/controlling-logging.md)  
 [Provedores CLR ETW](../../../docs/framework/performance/clr-etw-providers.md)  
 [Palavras-chave e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [Eventos ETW no Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
