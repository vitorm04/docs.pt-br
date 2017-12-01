---
title: Modernizar ciclo de vida do aplicativo com pipelines de CI/CD e ferramentas do DevOps na nuvem
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Modernizar ciclo de vida do aplicativo com pipelines de CI/CD e ferramentas do DevOps na nuvem"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 2799f203cec2b01d2c9ff1a60ece801dc5939104
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizar ciclo de vida do aplicativo com pipelines de CI/CD e ferramentas do DevOps na nuvem

As empresas de hoje precisam inovar em um ritmo acelerado para sermos competitivos no mercado. Entrega de alta qualidade, os aplicativos modernos requer DevOps ferramentas e os processos que são essenciais para implementar esse ciclo constante de inovação. Com as ferramentas corretas do DevOps, os desenvolvedores podem simplificar a implantação contínua e obter aplicativos inovadores nas mãos de usuários mais rapidamente.

Embora as práticas recomendadas de implantação e a integração contínuas são bem estabelecidas, a introdução de contêineres apresenta novas considerações, especialmente quando você estiver trabalhando com aplicativos de multi contêiner.

Visual Studio Team Services dá suporte à integração contínua e implantação de aplicativos de contêiner vários para vários ambientes pelas tarefas de implantação do Team Services oficiais:

-   [Implantar a VM do Host de Docker autônoma](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux ou Windows Server 2016 ou posterior)

-   [Implantar a malha do serviço](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [Implantação de serviço de contêiner do Azure – Kubernetes](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

Mas você também pode implantar em [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS usando as tarefas do Team Services baseado em script.

Para continuar facilitando a agilidade da implantação, essas ferramentas oferecem experiências de implantação excelente de desenvolvimento para teste de produção de cargas de trabalho de contêiner, com uma opção de desenvolvimento e soluções de CI/CD.

Figura 4-12 mostra um pipeline de implantação contínua que implanta um cluster Kubernetes no serviço de contêiner do Azure.

![Pipeline de implantação contínua do Visual Studio Team Services, implantando um cluster Kubernetes](./media/image12.png)

> **Figura 4-12.** Pipeline de implantação contínua do Visual Studio Team Services, implantando um cluster Kubernetes

>[!div class="step-by-step"]
[Anterior](modernize-your-apps-with-monitoring-and-telemetry.md)
[Próximo](migrate-to-hybrid-cloud-scenarios.md)
