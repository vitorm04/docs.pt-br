---
title: Modernizar seus aplicativos com o monitoramento e telemetria
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Modernizar seus aplicativos com o monitoramento e telemetria"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1535951eb648deab17cf8c2fe64db6ddf7df4cb5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizar seus aplicativos com o monitoramento e telemetria

Quando você executa um aplicativo em produção, é essencial que você tenha informações sobre o desempenho do seu aplicativo. Ele está executando em um nível alto? São usuários recebendo erros ou é o aplicativo estável e confiável? É necessário o monitoramento de desempenho avançado, poderoso alertas e painéis para ajudar a garantir que seu aplicativo está disponível e executando como esperado. Você também precisa ser capaz de ver rapidamente se há um problema, determine quantos clientes são afetados e executam uma análise de causas básicas para encontrar e corrigir o problema.

## <a name="monitor-your-application-with-application-insights"></a>Monitorar seu aplicativo com o Application Insights

Application Insights é um serviço de gerenciamento de desempenho de aplicativos (APM) extensível para desenvolvedores da web que trabalham em várias plataformas. Usá-lo para monitorar o aplicativo web em tempo real. Application Insights detecta automaticamente os problemas de desempenho. Ele inclui ferramentas de análise avançada para ajudá-lo a diagnosticar problemas e para ajudá-lo a entender o que os usuários, na verdade, fazem com seu aplicativo. Application Insights foi projetado para ajudá-lo a melhorar continuamente o desempenho e usabilidade. Ele funciona para aplicativos em uma ampla variedade de plataformas, incluindo .NET, Node.js e J2EE, se hospedado no local ou na nuvem. Application Insights integra-se com seus processos de DevOps e tem pontos de conexão a uma variedade de ferramentas de desenvolvimento.

Figura 4-10 mostra um exemplo de como o Application Insights monitorar seu aplicativo e como ele reproduz os insights em um painel.

![Painel de monitoramento do Application Insights](./media/image10.png)

> **Figura 4-10.** Painel de monitoramento do Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorar sua infra-estrutura de Docker com análise de Log e sua solução de monitoramento de contêiner

[Análise de logs do Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) faz parte do [geral de solução de monitoramento do Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Também é um serviço [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Análise de log monitora nuvem locais e ambientes (OMS local) para ajudar a manter a disponibilidade e o desempenho. Ele coleta dados gerados pelos recursos em seus ambientes de nuvem e locais e de outras ferramentas de monitoramentos para fornecer análise em várias origens.

Em relação aos logs de infraestrutura do Azure, a análise de Log, como um serviço do Azure, consome dados de log e métrica de outros serviços do Azure (por meio de [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), máquinas virtuais do Azure, contêineres do Docker e outros infraestruturas de nuvem ou local. Análise de log oferece pesquisa flexível de log e análise de fora da caixa sobre esses dados. Ele fornece ferramentas avançadas que você pode usar para analisar os dados entre fontes, permite consultas complexas entre todos os logs e proativamente alertá-com base nas condições especificadas. Você ainda pode coletar dados personalizados no repositório de análise de Log central, onde você pode consultar e visualizá-la. Você também pode tirar proveito das soluções de análise de Log internos para imediatamente obter ideias sobre a segurança e a funcionalidade de sua infraestrutura.

Você pode acessar a análise de Log por meio do portal do OMS ou o portal do Azure, que são executados em qualquer navegador, e fornecer acesso a definições de configuração e várias ferramentas para analisar e agir sobre dados coletados.

O [solução de monitoramento de contêiner](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) na análise de Log ajuda você exibir e gerenciar seus hosts de Docker e o contêiner do Windows em um único local. A solução mostra quais contêineres estão em execução, qual imagem de contêiner que está sendo executado e onde contêineres estão em execução. Você pode exibir informações detalhadas de auditoria, incluindo comandos que estão sendo usados com contêineres. Você também pode solucionar contêineres exibindo e pesquisando logs centralizados, sem a necessidade de exibir remotamente os hosts de Docker ou do Windows. Você pode encontrar os contêineres que podem ser ruídos e consumo de recursos em excesso em um host. Além disso, você pode exibir centralizado de CPU, memória, armazenamento e uso de rede e informações de desempenho, para contêineres. Em computadores que executam o Windows, você pode centralizar e comparar os logs do Windows Server, Hyper-V e contêineres do Docker. A solução oferece suporte as seguir orchestrators de contêiner:

-   Por nuvem de docker

-   DC/OS

-   Kubernetes

-   Malha do serviço

-   Red Hat OpenShift

Figura 4-11 mostra as relações entre vários hosts de contêiner e os agentes e o OMS.

![Solução de monitoramento de contêiner de análise de log](./media/image11.png)

> **Figura 4-11.** Solução de monitoramento de contêiner de análise de log

Você pode usar a solução de monitoramento de contêiner de análise de Log para:

-   Consulte informações sobre todos os hosts de contêiner em um único local.

-   Saber quais contêineres estão em execução, que imagem que está sendo executado e onde eles estão executando.

-   Consulte uma trilha de auditoria para ações em contêineres.

-   Solucionar problemas exibindo e pesquisando logs centralizados sem logon remoto para os hosts de Docker.

-   Localize contêineres que podem ser "vizinhos ruídos" e consumindo recursos em excesso em um host.

-   Exiba centralizado de CPU, memória, armazenamento e uso de rede e informações de desempenho, para contêineres.

### <a name="additional-resources"></a>Recursos adicionais

-   **Visão geral do monitoramento no Microsoft Azure**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   **O que é o Application Insights?**

[https://docs.microsoft.com/azure/application-insights/app-insights-overview](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   **O que é a análise de Log?**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-overview](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   **Solução de monitoramento de contêiner na análise de Log**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-containers](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   **Visão geral do Monitor do Azure**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   **O que é o Operations Management Suite (OMS)?**

[https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   **Monitoramento de contêineres do Windows Server na malha do serviço com o OMS**

[https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
[Anterior](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Próximo](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
