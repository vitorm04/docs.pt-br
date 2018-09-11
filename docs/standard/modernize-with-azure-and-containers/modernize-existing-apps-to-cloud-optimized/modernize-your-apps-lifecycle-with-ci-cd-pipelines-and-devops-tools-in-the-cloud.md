---
title: Modernize o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Modernize o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c4d3eaa50f6c7645c954ca65bf42c6c1eab3a68d
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44366837"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Modernize o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem

As empresas de hoje precisam inovar em um ritmo acelerado para sermos competitivos no marketplace. Fornecimento de alta qualidade, aplicativos modernos requer ferramentas de DevOps e os processos que são essenciais para implementar esse ciclo constante da inovação. Com as ferramentas certas do DevOps, os desenvolvedores podem simplificar a implantação contínua e obter aplicativos inovadores nas mãos de usuários mais rapidamente.

Embora as práticas de implantação e integração contínuas sejam bem estabelecidas, a introdução de contêineres apresenta novas considerações, especialmente quando você estiver trabalhando com aplicativos de vários contêineres.

Serviços de DevOps do Azure dá suporte à integração contínua e implantação de aplicativos de vários contêineres em uma variedade de ambientes por meio de tarefas de implantação de serviços de DevOps do Azure oficiais:

-   [Implantar a VM de Host do Docker autônoma](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux ou Windows Server 2016 ou posterior)

-   [Implantar no Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [Implantar no serviço de contêiner do Azure – Kubernetes](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

Mas você também pode implantar em [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS usando serviços de DevOps do Azure baseada em script as tarefas.

Para continuar promovendo a agilidade de implantação, essas ferramentas oferecem experiências de implantação de desenvolvimento para teste para produção excelente para cargas de trabalho de contêiner, com uma opção de desenvolvimento e soluções de CI/CD.

Figura 4-12 mostra um pipeline de implantação contínua que implanta em um cluster Kubernetes no serviço de contêiner do Azure.

![Pipeline de implantação contínua de serviços de DevOps do Azure, implantar um cluster Kubernetes](./media/image12.png)

> **Figura 4 a 12.** Pipeline de implantação contínua de serviços de DevOps do Azure, implantar um cluster Kubernetes

>[!div class="step-by-step"]
[Anterior](modernize-your-apps-with-monitoring-and-telemetry.md)
[Próximo](migrate-to-hybrid-cloud-scenarios.md)
