---
title: Modernize o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Modernize o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c4d3eaa50f6c7645c954ca65bf42c6c1eab3a68d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45742867"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="a15a8-103">Modernize o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem</span><span class="sxs-lookup"><span data-stu-id="a15a8-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="a15a8-104">As empresas de hoje precisam inovar em um ritmo acelerado para sermos competitivos no marketplace.</span><span class="sxs-lookup"><span data-stu-id="a15a8-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="a15a8-105">Fornecimento de alta qualidade, aplicativos modernos requer ferramentas de DevOps e os processos que são essenciais para implementar esse ciclo constante da inovação.</span><span class="sxs-lookup"><span data-stu-id="a15a8-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="a15a8-106">Com as ferramentas certas do DevOps, os desenvolvedores podem simplificar a implantação contínua e obter aplicativos inovadores nas mãos de usuários mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="a15a8-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="a15a8-107">Embora as práticas de implantação e integração contínuas sejam bem estabelecidas, a introdução de contêineres apresenta novas considerações, especialmente quando você estiver trabalhando com aplicativos de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="a15a8-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="a15a8-108">Serviços de DevOps do Azure dá suporte à integração contínua e implantação de aplicativos de vários contêineres em uma variedade de ambientes por meio de tarefas de implantação de serviços de DevOps do Azure oficiais:</span><span class="sxs-lookup"><span data-stu-id="a15a8-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

-   <span data-ttu-id="a15a8-109">[Implantar a VM de Host do Docker autônoma](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux ou Windows Server 2016 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="a15a8-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/azure/devops/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="a15a8-110">Implantar no Service Fabric</span><span class="sxs-lookup"><span data-stu-id="a15a8-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="a15a8-111">Implantar no serviço de contêiner do Azure – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a15a8-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="a15a8-112">Mas você também pode implantar em [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS usando serviços de DevOps do Azure baseada em script as tarefas.</span><span class="sxs-lookup"><span data-stu-id="a15a8-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="a15a8-113">Para continuar promovendo a agilidade de implantação, essas ferramentas oferecem experiências de implantação de desenvolvimento para teste para produção excelente para cargas de trabalho de contêiner, com uma opção de desenvolvimento e soluções de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="a15a8-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="a15a8-114">Figura 4-12 mostra um pipeline de implantação contínua que implanta em um cluster Kubernetes no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="a15a8-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Pipeline de implantação contínua de serviços de DevOps do Azure, implantar um cluster Kubernetes](./media/image12.png)

> <span data-ttu-id="a15a8-116">**Figura 4 a 12.**</span><span class="sxs-lookup"><span data-stu-id="a15a8-116">**Figure 4-12.**</span></span> <span data-ttu-id="a15a8-117">Pipeline de implantação contínua de serviços de DevOps do Azure, implantar um cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a15a8-117">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a15a8-118">[Anterior](modernize-your-apps-with-monitoring-and-telemetry.md)
[Próximo](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="a15a8-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
