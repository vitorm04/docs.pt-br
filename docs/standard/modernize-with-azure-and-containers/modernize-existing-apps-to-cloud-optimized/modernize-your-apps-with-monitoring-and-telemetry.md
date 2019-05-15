---
title: Modernizar seus aplicativos com o monitoramento e telemetria
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Modernizar seus aplicativos com o monitoramento e telemetria
ms.date: 04/30/2018
ms.openlocfilehash: 94196365e6ed93839b28ed3b375e75a9119ae12d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643689"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizar seus aplicativos com o monitoramento e telemetria

Quando você executa um aplicativo em produção, é essencial que você tenha insights sobre o desempenho do seu aplicativo. Ele está executando em um alto nível? Os usuários recebam erros ou é o aplicativo estável e confiável? Você precisa de monitoramento de desempenho avançado, avançados de alerta e painéis para ajudar a garantir que seu aplicativo está disponível e funcionando conforme o esperado. Você também precisa ser capaz de ver rapidamente se há um problema, determine quantos clientes são afetados e realizam uma análise de causa raiz para encontrar e corrigir o problema.

## <a name="monitor-your-application-with-application-insights"></a>Monitorar seu aplicativo com o Application Insights

Application Insights é um serviço de gerenciamento de desempenho de aplicativos (APM) extensível para desenvolvedores da web que trabalham em várias plataformas. Usá-lo para monitorar seu aplicativo web em tempo real. Application Insights detecta automaticamente anomalias de desempenho. Ele inclui ferramentas de análise avançadas para ajudar a diagnosticar problemas e para ajudá-lo a entender o que os usuários realmente fazem com seu aplicativo. Application Insights foi projetado para ajudá-lo a aprimorar continuamente o desempenho e usabilidade. Ele funciona para aplicativos em uma ampla variedade de plataformas, incluindo .NET, Node. js e J2EE, sejam hospedados localmente ou na nuvem. Application Insights integra-se com seus processos de DevOps e tem pontos de conexão para uma variedade de ferramentas de desenvolvimento.

Figura 4-10 mostra um exemplo de como o Application Insights monitora seu aplicativo e como ele revela esses insights em um painel.

![Painel de monitoramento do Application Insights](./media/image10.png)

> **Figura 4 a 10.** Painel de monitoramento do Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorar a infraestrutura do Docker com o Log Analytics e sua solução de monitoramento de contêiner

[O Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) faz parte do [gerais de solução de monitoramento do Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Ele também é um serviço em [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Log Analytics monitora a nuvem e ambientes locais (para o local OMS) para ajudar a manter a disponibilidade e desempenho. Ele coleta dados gerados pelos recursos em seus ambientes de nuvem e locais e de outras ferramentas de monitoramento para fornecer análise de várias fontes.

Em relação aos logs de infraestrutura do Azure Log Analytics, como um serviço do Azure, consome os dados de log e métrica de outros serviços do Azure (via [do Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), VMs do Azure, contêineres do Docker e outras infraestruturas de nuvem ou locais. O log Analytics oferece pesquisa de logs flexíveis e análises de fora da caixa sobre esses dados. Ele fornece ferramentas avançadas que você pode usar para analisar dados de fontes, ele permite consultas complexas em todos os logs e pode alertar proativamente com base nas condições especificadas. Você pode até mesmo coletar dados personalizados no repositório do Log Analytics central, onde você pode consultar e visualizá-los. Você também pode tirar proveito das soluções internas do Log Analytics para imediatamente obter ideias sobre a segurança e a funcionalidade da sua infraestrutura.

Você pode acessar o Log Analytics por meio do portal do OMS ou portal do Azure, que são executados em qualquer navegador, e fornece acesso às definições de configuração e várias ferramentas para analisar e agir sobre os dados coletados.

O [solução de monitoramento de contêiner](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) no Log Analytics ajuda você pode exibir e gerenciar os hosts do Docker e o contêiner do Windows em um único local. A solução mostra quais contêineres estão em execução, qual imagem de contêiner estiverem em execução e, em que os contêineres estão em execução. Você pode exibir informações detalhadas de auditoria, incluindo comandos que estão sendo usados com contêineres. Você também pode solucionar problemas de contêineres exibindo e pesquisando logs centralizados, sem precisar exibir remotamente os hosts do Docker ou do Windows. Você pode encontrar contêineres que podem estar com ruídos e consumindo recursos em excesso em um host. Além disso, você pode exibir centralizadas de CPU, memória, armazenamento e o uso da rede e informações de desempenho, para contêineres. Em computadores com Windows, você pode centralizar e comparar os logs do Windows Server, Hyper-V e contêineres do Docker. A solução dá suporte aos orquestradores de contêiner a seguir:

- Docker Swarm

- DC/OS

- Kubernetes

- Service Fabric

- Red Hat OpenShift

Figura 4-11 mostra as relações entre vários hosts de contêiner e agentes e o OMS.

![Solução de monitoramento de contêiner com a análise de log](./media/image11.png)

> **Figura 4-11.** Solução de monitoramento de contêiner com a análise de log

Você pode usar a solução de monitoramento de contêiner do Log Analytics para:

- Ver informações sobre todos os hosts de contêiner em um único local.

- Saber quais contêineres estão em execução, qual imagem estiverem em execução e onde elas estão em execução.

- Consulte uma trilha de auditoria para ações em contêineres.

- Solucionar problemas exibindo e pesquisando logs centralizados sem logon remoto para os hosts do Docker.

- Encontre contêineres que podem ser "vizinhos barulhentos" e consumindo recursos em excesso em um host.

- Exiba centralizadas de CPU, memória, armazenamento e o uso da rede e informações de desempenho, para contêineres.

### <a name="additional-resources"></a>Recursos adicionais

- **Visão geral do monitoramento no Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **O que é o Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **O que é o Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Solução de monitoramento de contêiner no Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Visão geral do Monitor do Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **O que é Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

- **Monitoramento de contêineres do Windows Server no Service Fabric com o OMS**

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
>[Anterior](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[Próximo](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
