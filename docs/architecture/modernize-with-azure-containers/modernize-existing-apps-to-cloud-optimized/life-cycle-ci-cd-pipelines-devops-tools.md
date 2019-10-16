---
title: Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Modernizar o ciclo de vida de seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
ms.date: 04/30/2018
ms.openlocfilehash: d1aa2e156e87cafe99fb994233786f67bf7a81a1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396211"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem

As empresas de hoje precisam inovar em um ritmo rápido para serem competitivas no Marketplace. O fornecimento de aplicativos modernos de alta qualidade exige ferramentas e processos de DevOps que são essenciais para implementar esse ciclo constante de inovação. Com as ferramentas DevOps certas, os desenvolvedores podem simplificar a implantação contínua e obter aplicativos inovadores para as mãos de usuários mais rapidamente.

Embora as práticas de integração e implantação contínuas sejam bem estabelecidas, a introdução dos contêineres apresenta novas considerações, especialmente quando você está trabalhando com aplicativos com vários contêineres.

O Azure DevOps Services dá suporte à integração e à implantação contínuas de aplicativos de vários contêineres a uma variedade de ambientes por meio das tarefas oficiais de implantação de Azure DevOps Services:

- [Implantar em um Aplicativo Web para Contêineres do Azure](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Implantar no serviço kubernetes do Azure](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Mas você também pode implantar no [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS usando Azure DevOps Services tarefas baseadas em script.

Para continuar a facilitar a agilidade da implantação, essas ferramentas fornecem excelentes experiências de implantação de desenvolvimento para teste para produção para cargas de trabalho de contêiner, com uma opção de desenvolvimento e soluções de CI/CD.

A Figura 4-12 mostra um pipeline de implantação contínua que é implantado em um cluster kubernetes no serviço de contêiner do Azure.

![Captura de tela de Azure DevOps Services implantando em um cluster kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Figura 4-12.** Azure DevOps Services pipeline de implantação contínua, implantando em um cluster kubernetes

>[!div class="step-by-step"]
>[Anterior](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Próximo](migrate-to-hybrid-cloud-scenarios.md)
