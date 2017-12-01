---
title: "Resiliência e a alta disponibilidade em microservices"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Resiliência e a alta disponibilidade em microservices"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 149e28ac7bd7383e4e960ed8a226943e2b9bdaa1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Resiliência e a alta disponibilidade em microservices

Lidar com falhas inesperadas é um dos problemas mais difíceis de resolver, especialmente em um sistema distribuído. Grande parte do código que os desenvolvedores gravar envolve tratamento de exceções e isso também é onde a maioria do tempo é gasto no teste. O problema é mais envolvido que escrever código para lidar com falhas. O que acontece quando o computador onde o microsserviço está em execução falhar? Não só é necessário detectar a falha de microsserviço (um problema de disco rígido em seu próprio), mas algo para reiniciar o microsserviço também é necessário.

Um microsserviço precisa para ser resiliente a falhas e para conseguir reiniciar geralmente em outro computador para disponibilidade. Essa flexibilidade também resume ao estado em que foi salvo em nome de microsserviço, onde o microsserviço pode recuperar esse estado de, e se o microsserviço pode reiniciar com êxito. Em outras palavras, deve ser resiliência na capacidade de computação (o processo pode reiniciar a qualquer momento), bem como resiliência no estado ou dados (sem perda de dados e os dados permanecem consistentes).

Os problemas de resiliência são abordados durante a outros cenários, como quando falhas ocorrerem durante uma atualização de aplicativo. Precisa de microsserviço, trabalhando com o sistema de implantação, para determinar se ele pode continuar a mover para a versão mais recente ou em vez disso, reverter para uma versão anterior para manter um estado consistente. Perguntas como máquinas suficientes estejam disponíveis para manter movimento para frente e como recuperar versões anteriores de microsserviço precisam ser considerados. Isso requer o microsserviço para emitir informações de integridade para que o aplicativo geral e o orchestrator podem tomar essas decisões.

Além disso, a resiliência está relacionada aos sistemas como baseado em nuvem deve se comportam. Conforme mencionado, um sistema baseado em nuvem deve compreender falhas e deve tentar se recuperar automaticamente de-los. Por exemplo, no caso de falhas de rede ou um contêiner, aplicativos cliente ou serviços do cliente devem ter uma estratégia de repetição de envio de mensagens ou tentar novamente solicitações, como em muitos casos falhas na nuvem são parciais. O [implementando aplicativos resilientes](#implementing_resilient_apps) seção neste guia aborda como lidar com falhas parciais. Descreve técnicas como as repetições com retirada exponencial ou o padrão de disjuntor no núcleo do .NET usando bibliotecas como [Polly](https://github.com/App-vNext/Polly), que oferece uma grande variedade de políticas para lidar com esse assunto.

## <a name="health-management-and-diagnostics-in-microservices"></a>Gerenciamento de integridade e diagnóstico em microservices

Pode parecer óbvio e muitas vezes é ignorado, mas um microsserviço deve informar sua integridade e diagnóstico. Caso contrário, há pouca visão de uma perspectiva de operações. Correlacionar eventos de diagnóstico em um conjunto de serviços independentes e lidar com desvios de relógio do computador para compreender a ordem de eventos é um desafio. Da mesma maneira que você interage com um microsserviço estabelecido protocolos e formatos de dados, há a necessidade de padronização como integridade e eventos de diagnóstico que, por fim, terminam em um repositório de eventos para consultar e exibir log. Uma abordagem microservices, ela é a chave que diferentes equipes concordam em um formato de log único. Precisa ser uma abordagem consistente para exibir eventos de diagnóstico no aplicativo.

### <a name="health-checks"></a>Verificações de integridade

Integridade é diferente do diagnóstico. Integridade está prestes o microsserviço reporting seu estado atual para executar as ações apropriadas. Um bom exemplo está trabalhando com mecanismos de implantação e atualização para manter a disponibilidade. Embora um serviço no momento pode estar com problemas devido a uma falha de processo ou reinicialização do computador, o serviço ainda pode estar operacional. É a última coisa que você precisa fazer isso pior executando uma atualização. A melhor abordagem é fazer uma investigação primeiro ou aguarde até que o microsserviço recuperar. Eventos de integridade de um microsserviço nos ajudam a tomar decisões informadas e, na verdade, ajuda a criar serviços auto-reparo.

A implementação integridade verifica na seção de serviços do ASP.NET Core deste guia, que explicam como usar uma nova biblioteca ASP.NET HealthChecks em seu microservices, portanto, eles podem relatar seu estado para um serviço de monitoramento para executar as ações apropriadas.

### <a name="using-diagnostics-and-logs-event-streams"></a>Usando fluxos de eventos de diagnóstico e de logs

Logs fornecem informações sobre como um aplicativo ou serviço estiver em execução, incluindo exceções, avisos e mensagens informativas simples. Normalmente, cada log está em um formato de texto com uma linha por evento, embora exceções também muitas vezes mostram o rastreamento de pilha em várias linhas.

Monolíticos aplicativos baseados em servidor, você pode simplesmente gravar logs de um arquivo no disco (um arquivo de log) e, em seguida, analisá-lo com qualquer ferramenta. Desde que a execução do aplicativo é limitada a um servidor fixa ou VM, geralmente não é muito complexa para analisar o fluxo de eventos. No entanto, em um aplicativo distribuído em vários serviços são executados em vários nós em um cluster do orchestrator, capacidade de correlacionar eventos distribuídos é um desafio.

Um aplicativo baseado em microsserviço, não tente armazenar o fluxo de saída de eventos ou arquivos de log por si só e nem mesmo tentar gerenciar o roteamento de eventos para um local central. Ele deve ser transparente, o que significa que cada processo deve gravar apenas seu fluxo de eventos em uma saída padrão que será coletada pela infraestrutura do ambiente de execução onde ele está sendo executado sob. Um exemplo desses roteadores do fluxo de evento é [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), que coleta os fluxos de eventos de várias fontes e publica para sistemas de saída. Eles podem incluir simple padrão de saída para um ambiente de desenvolvimento ou sistemas de nuvem como [Application Insights](https://azure.microsoft.com/services/application-insights/), [OMS](https://github.com/Azure/diagnostics-eventflow#oms-operations-management-suite) (para aplicativos locais) e [odiagnósticodoAzure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics). Também há plataformas de análise de log de terceiros boa e ferramentas que podem procurar, alerta, relatórios, e os logs de monitor, mesmo em tempo real, como [Splunk](http://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrators gerenciamento de informações de integridade e diagnóstico

Quando você cria um aplicativo baseado em microsserviço, você precisa lidar com a complexidade. Logicamente, um único microsserviço é simple lidar com, mas dúzias ou centenas de tipos e milhares de instâncias de microservices é um problema complexo. Não envolve apenas criando sua arquitetura de microsserviço — você também precisa de alta disponibilidade, capacidade de endereçamento, resiliência, integridade e diagnóstico se você pretende ter um sistema estável e consistente.

![](./media/image22.png)

**Figura 4-22**. Uma plataforma de Microsserviço é fundamental para o gerenciamento de integridade do aplicativo

Os problemas complexos mostrados na Figura 4-22 são muito difíceis de resolver sozinho. As equipes de desenvolvimento devem se concentrar na solução de problemas de negócios e criar aplicativos personalizados com abordagens baseadas em microsserviço. Eles não devem se concentrar na solução de problemas de infraestrutura complexa; Se isso ocorreu, o custo de qualquer aplicativo baseado em microsserviço seria enorme. Portanto, há plataformas e orientada a microsserviço, conhecidas como orchestrators ou clusters de microsserviço, que tenta resolver os problemas de disco rígidos de criação e execução de um serviço e usando os recursos de infraestrutura com eficiência. Isso reduz a complexidade da criação de aplicativos que usam uma abordagem microservices.

Orchestrators diferentes, podem parecer semelhantes, mas o diagnóstico e verificações de integridade oferecidas por cada um deles diferem nos recursos e o estado de vencimento, às vezes, dependendo da plataforma de sistema operacional, conforme explicado na próxima seção.

## <a name="additional-resources"></a>Recursos adicionais

-   **O aplicativo de doze fator. XI. Logs: Tratar logs como fluxos de eventos**
    [*https://12factor.net/logs*](https://12factor.net/logs)

-   **Diagnóstico do Microsoft EventFlow biblioteca.** Repositório do GitHub.

    [*https://GitHub.com/Azure/Diagnostics-eventflow*](https://github.com/Azure/diagnostics-eventflow)

-   **O que é o diagnóstico do Azure**
    [*https://docs.microsoft.com/azure/azure-diagnostics*](https://docs.microsoft.com/azure/azure-diagnostics)

-   **Conectar computadores Windows para o serviço de análise de Log no Azure**
    [*https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents*](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents)

-   **Fazendo o que significam: Usando o bloco de aplicativo do log semântica**
    [*https://msdn.microsoft.com/library/dn440729 (v=pandp.60).aspx*](https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx)

-   **Splunk.** Site oficial.
    [*http://www.splunk.com*](http://www.splunk.com)

-   **Classe EventSource**. API para eventos de rastreamento para Windows (ETW) [ *https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource*](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource)




>[!div class="step-by-step"]
[Anterior] (microservice-based-composite-ui-shape-layout.md) [Avançar] (scalable-available-multi-container-microservice-applications.md)
