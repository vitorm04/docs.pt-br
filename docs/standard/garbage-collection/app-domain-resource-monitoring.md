---
title: "Monitoramento de recursos de domínio de aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62a514f94857044af5020d36a1cfd6ce06741ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="application-domain-resource-monitoring"></a>Monitoramento de recursos de domínio de aplicativo
Recursos de domínio de aplicativo de monitoramento (ARM) permite que os hosts monitorar o uso de CPU e memória por domínio de aplicativo. Isso é útil para hosts como o ASP.NET que usam vários domínios de aplicativo em um processo de execução longa. O host pode descarregar o domínio de aplicativo de um aplicativo que está prejudicando o desempenho de todo o processo, mas apenas se ele pode identificar o aplicativo problemático. ARM fornece informações que podem ser usadas para ajudar a tomar essas decisões.  
  
 Por exemplo, um serviço de hospedagem pode ter vários aplicativos em execução em um servidor do ASP.NET. Se um aplicativo no processo de começar a consumir muita memória ou muito tempo do processador, o serviço de hospedagem pode usar ARM para identificar o domínio de aplicativo que está causando o problema.  
  
 ARM é suficientemente leve para usar em aplicativos em tempo real. Você pode acessar as informações usando o rastreamento de eventos para Windows (ETW) ou diretamente por meio de APIs gerenciado ou nativo.  
  
## <a name="enabling-resource-monitoring"></a>Habilitar o monitoramento de recursos  
 ARM pode ser habilitada em quatro maneiras: fornecendo um arquivo de configuração quando o common language runtime (CLR) é iniciado, usando um não gerenciado API de hospedagem, usando código gerenciado, ou escutar eventos ETW de ARM.  
  
 Assim que ARM estiver habilitado, ele começa coletando dados em todos os domínios de aplicativo no processo. Se um domínio de aplicativo foi criado antes de ARM está habilitada, dados cumulativos inicia quando ARM está habilitada, não quando o domínio de aplicativo foi criado. Depois de ter habilitado, ARM não pode ser desabilitado.  
  
-   Você pode habilitar ARM na inicialização do CLR, adicionando o [ \<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) elemento para o arquivo de configuração e a configuração de `enabled` atributo `true`. Um valor de `false` (o padrão) significa apenas que ARM não está habilitado na inicialização; você pode ativá-la mais tarde usando um dos mecanismos de ativação.  
  
-   O host pode habilitar ARM solicitando o [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface de hospedagem. Depois que esta interface é obtida com êxito, ARM está habilitada.  
  
-   Código gerenciado pode habilitar ARM definindo estático (`Shared` no Visual Basic) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriedade `true`. Assim que a propriedade é definida, ARM está habilitado.  
  
-   Você pode habilitar ARM após a inicialização, escutar eventos ETW. ARM está habilitado e começa a criação de eventos para todos os domínios de aplicativo quando você habilita o provedor público `Microsoft-Windows-DotNETRuntime` usando o `AppDomainResourceManagementKeyword` palavra-chave. Para correlacionar dados com domínios de aplicativo e threads, você também deve habilitar o `Microsoft-Windows-DotNETRuntimeRundown` provedor com o `ThreadingKeyword` palavra-chave.  
  
## <a name="using-arm"></a>Usando ARM  
 ARM fornece o tempo total do processador que é usado por um domínio de aplicativo e três tipos de informações sobre o uso de memória.  
  
-   **Total de tempo do processador para um domínio de aplicativo, em segundos**: isso é calculado somando os tempos de thread relatados pelo sistema operacional de todos os threads gasto na execução de tempo no domínio do aplicativo durante seu ciclo de vida. Bloqueado ou threads em suspensão não usa o tempo do processador. Quando um thread chama-se em código nativo, a hora em que o thread gasta em código nativo está incluída na contagem para o domínio de aplicativo em que a chamada foi feita.  
  
    -   API gerenciada: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> propriedade.  
  
    -   API de hospedagem: [: Getcurrentcputime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) método.  
  
    -   Eventos ETW: `ThreadCreated`, `ThreadAppDomainEnter`, e `ThreadTerminated` eventos. Para obter informações sobre palavras-chave e provedores, consulte "Eventos de monitoramento de recursos AppDomain" em [eventos de ETW CLR](../../../docs/framework/performance/clr-etw-events.md).  
  
-   **Total de alocações gerenciadas feitas por um domínio de aplicativo durante seu ciclo de vida, em bytes**: Total de alocações nem sempre reflete o uso de memória por um domínio de aplicativo, pois os objetos alocados podem ser curta duração. No entanto, se um aplicativo aloca e libera grandes quantidades de objetos, o custo das alocações pode ser significativo.  
  
    -   API gerenciada: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> propriedade.  
  
    -   API de hospedagem: [: Getcurrentallocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) método.  
  
    -   Eventos ETW: `AppDomainMemAllocated` evento `Allocated` campo.  
  
-   **Gerenciado de memória, em bytes, que é referenciado por um domínio de aplicativo e que sobreviveram o completo mais recente, o bloqueio de coleta**: esse número é preciso somente após um completo, bloqueio de coleta. (Isso é diferente de coleções simultâneas, que ocorrem em segundo plano e não bloqueia o aplicativo). Por exemplo, o <xref:System.GC.Collect?displayProperty=nameWithType> sobrecarga do método faz com que um completo, bloqueio de coleta.  
  
    -   API gerenciada: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> propriedade.  
  
    -   API de hospedagem: [: Getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) método `pAppDomainBytesSurvived` parâmetro.  
  
    -   Eventos ETW: `AppDomainMemSurvived` evento `Survived` campo.  
  
-   **Total de memória gerenciada, em bytes, que é referenciado pelo processo e que sobreviveram o completo mais recente, o bloqueio de coleta**: A memória examina para domínios de aplicativos individuais pode ser comparada para esse número.  
  
    -   API gerenciada: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> propriedade.  
  
    -   API de hospedagem: [: Getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) método `pTotalBytesSurvived` parâmetro.  
  
    -   Eventos ETW: `AppDomainMemSurvived` evento `ProcessSurvived` campo.  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>Para determinar quando um completo, bloqueio de coleta ocorre  
 Para determinar quando as contagens de memória examina são precisas, você precisa saber quando uma coleção completa, de bloqueio apenas ocorreu. O método para fazer isso depende da API permite examinar estatísticas ARM.  
  
#### <a name="managed-api"></a>API gerenciada  
 Se você usar as propriedades do <xref:System.AppDomain> classe, você pode usar o <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> método para se registrar para notificação de coleções completas. O limite que você usa não é importante, porque estão aguardando a conclusão de uma coleção em vez da abordagem de uma coleção. Em seguida, você pode chamar o <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> método, que bloqueia até que uma coleção completa seja concluída. Você pode criar um thread que chama o método em um loop e não faz nenhuma análise necessária sempre que o método retorna.  
  
 Como alternativa, você pode chamar o <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> método periodicamente para verificar se a contagem de coleções de geração 2 aumentou. Dependendo da frequência de sondagem, essa técnica pode não oferecer como precisas uma indicação da ocorrência de uma coleção completa.  
  
#### <a name="hosting-api"></a>API de hospedagem  
 Se você usar a API não gerenciada de hospedagem, o host deve passar o CLR uma implementação do [IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) interface. O CLR chama o [Ihostgcmanager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) método quando ele retoma a execução de threads que foram suspensos enquanto ocorre de uma coleção. O CLR passa a geração da coleção concluída como um parâmetro do método, para que o host possa determinar se a coleção foi completa ou parcial. A implementação do [Ihostgcmanager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) método pode consultar para memória examina, certifique-se de que as contagens são recuperadas assim que elas são atualizadas.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [Interface ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [Eventos de CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
