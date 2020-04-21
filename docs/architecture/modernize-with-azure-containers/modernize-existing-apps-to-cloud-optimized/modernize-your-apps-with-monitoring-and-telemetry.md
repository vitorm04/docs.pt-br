---
title: Modernizar seus aplicativos com o monitoramento e telemetria
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Modernize seus aplicativos com monitoramento e telemetria
ms.date: 04/30/2018
ms.openlocfilehash: a5101f150d6548406db8638904fb4ab6375edf9c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739177"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizar seus aplicativos com o monitoramento e telemetria

Quando você executa um aplicativo em produção, é fundamental que você tenha insights sobre como seu aplicativo está se saindo. Está se apresentando em alto nível? Os usuários estão cometendo erros ou o aplicativo é estável e confiável? Você precisa de um monitoramento de desempenho rico, alertas poderosos e dashboards para ajudar a garantir que seu aplicativo esteja disponível e funcionando como esperado. Você também precisa ser capaz de ver rapidamente se há um problema, determinar quantos clientes são afetados e realizar uma análise de causa básica para encontrar e corrigir o problema.

## <a name="monitor-your-application-with-application-insights"></a>Monitore seu aplicativo com insights de aplicativos

O Application Insights é um serviço extensível de Gerenciamento de Desempenho de Aplicativos (APM) para desenvolvedores web que trabalham em várias plataformas. Use-o para monitorar seu aplicativo Web online. O Application Insights detecta automaticamente anomalias de desempenho. Ele inclui ferramentas de análise poderosas para ajudá-lo a diagnosticar problemas e ajudá-lo a entender o que os usuários realmente fazem com seu aplicativo. O Application Insights foi projetado para ajudar você a aprimorar continuamente o desempenho e a usabilidade do seu aplicativo. Ele funciona para aplicativos em uma ampla variedade de plataformas, incluindo .NET, Node.js e J2EE, seja hospedado no local ou na nuvem. O Application Insights integra-se aos seus processos de DevOps e tem pontos de conexão para uma variedade de ferramentas de desenvolvimento.

A Figura 4-10 mostra um exemplo de como o Application Insights monitora seu aplicativo e como ele aparece esses insights em um painel de controle.

![Captura de tela do painel de monitoramento do Application Insights.](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Figura 4-10.** Painel de monitoramento do Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitore sua infra-estrutura do Docker com o Log Analytics e sua solução de monitoramento de contêineres

[O Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) faz parte da solução global de monitoramento do [Microsoft Azure.](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview) É também um serviço no [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). O Log Analytics monitora ambientes em nuvem e locais (OMS para locais) para ajudar a manter a disponibilidade e o desempenho. Ele coleta dados gerados pelos recursos em seus ambientes de nuvem e locais e de outras ferramentas de monitoramento para fornecer análise de várias fontes.

Em relação aos registros de infra-estrutura do Azure, o Log Analytics, como um serviço Do Zure, ingere dados de log e métrica de outros serviços do Azure (via [Azure Monitor),](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)VMs do Azure, contêineres Docker e no local ou outras infra-estruturas em nuvem. O Log Analytics oferece pesquisa de log flexível e análises fora da caixa em cima desses dados. Ele fornece ferramentas ricas que você pode usar para analisar dados entre fontes, permite consultas complexas em todos os registros e pode alertar proativamente com base em condições especificadas. Você pode até mesmo coletar dados personalizados no repositório central do Log Analytics, onde você pode consultar e visualizá-los. Você também pode aproveitar as soluções incorporadas do Log Analytics para obter imediatamente insights sobre a segurança e funcionalidade de sua infra-estrutura.

Você pode acessar o Log Analytics através do portal OMS ou do portal Azure, que é executado em qualquer navegador, e fornecer-lhe acesso às configurações de configuração e várias ferramentas para analisar e agir sobre os dados coletados.

A [solução de monitoramento de contêineres](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) no Log Analytics ajuda você a visualizar e gerenciar seus hosts Docker e Windows Container em um único local. A solução mostra quais contêineres estão funcionando, qual a imagem do contêiner que eles estão executando e onde os contêineres estão sendo executados. Você pode visualizar informações detalhadas de auditoria, incluindo comandos que estão sendo usados com contêineres. Você também pode solucionar problemas de contêineres visualizando e pesquisando logs centralizados, sem precisar visualizar remotamente hosts Docker ou Windows. Você pode encontrar contêineres que podem ser barulhentos e consumir recursos excessivos em um host. Além disso, você pode visualizar informações centralizadas de CPU, memória, armazenamento e uso de rede e desempenho, para contêineres. Nos computadores que executam o Windows, você pode centralizar e comparar os logs do Windows Server, do Hyper-V e dos contêineres do Docker. A solução oferece suporte aos orquestradores de contêiner a seguir:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

A Figura 4-11 mostra as relações entre vários hosts de contêineres e agentes e OMS.

![Captura de tela da solução Log Analytics Container Monitoring.](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Figura 4-11.** Solução de monitoramento de contêineres do Log Analytics

Você pode usar a solução Log Analytics Container Monitoring para:

- Veja informações sobre todos os hosts de contêineres em um único local.

- Saiba quais contêineres estão funcionando, que imagem estão executando e para onde estão correndo.

- Consulte um rastro de auditoria para ações em contêineres.

- Solucionar problemas visualizando e pesquisando logs centralizados sem login remoto nos hosts do Docker.

- Encontre contêineres que possam ser "vizinhos barulhentos", e esteja consumindo recursos excessivos em um host.

- Exibir informações centralizadas de CPU, memória, armazenamento e uso de rede e informações de desempenho para contêineres.

### <a name="additional-resources"></a>Recursos adicionais

- **Visão geral do monitoramento no Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **O que é o Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **O que é o Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Solução de monitoramento de contêiner no Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Visão geral do Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **O que é Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[anterior](life-cycle-ci-cd-pipelines-devops-tools.md)
