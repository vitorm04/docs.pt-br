---
title: Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Modernize o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas DevOps na nuvem
ms.date: 04/30/2018
ms.openlocfilehash: ac2d9a1e9ab432cf69cb3da670fc91c681f802c2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987849"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem

As empresas de hoje precisam inovar em um ritmo rápido para serem competitivas no mercado. Fornecer aplicações modernas e de alta qualidade requer ferramentas e processos DevOps que são fundamentais para implementar esse ciclo constante de inovação. Com as ferramentas DevOps certas, os desenvolvedores podem simplificar a implantação contínua e colocar aplicativos inovadores nas mãos dos usuários mais rapidamente.

Embora as práticas de integração e implantação contínuas estejam bem estabelecidas, a introdução de contêineres introduz novas considerações, especialmente quando você está trabalhando com aplicações de vários contêineres.

O Azure DevOps Services suporta integração contínua e implantação de aplicativos de vários contêineres para uma variedade de ambientes através das tarefas oficiais de implantação do Azure DevOps Services:

- [Implantar em um aplicativo web do Azure para contêineres](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Implantar no Serviço Azure Kubernetes](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Mas você também pode implantar no [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) ou DC/OS usando tarefas baseadas em script do Azure DevOps Services.

Para continuar facilitando a agilidade de implantação, essas ferramentas fornecem excelentes experiências de implantação de desenvolvimento para teste-para-produção para cargas de trabalho de contêineres, com uma escolha de desenvolvimento e soluções de CI/CD.

A Figura 4-12 mostra um pipeline de implantação contínua que é implantado em um cluster Kubernetes no Azure Container Service.

![Captura de tela dos Serviços Azure DevOps implantados em um cluster Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Figura 4-12.** Azure DevOps Services gasoduto de implantação contínua, implantando em um cluster Kubernetes

>[!div class="step-by-step"]
>[Próximo](modernize-your-apps-with-monitoring-and-telemetry.md)
>[anterior](migrate-to-hybrid-cloud-scenarios.md)
