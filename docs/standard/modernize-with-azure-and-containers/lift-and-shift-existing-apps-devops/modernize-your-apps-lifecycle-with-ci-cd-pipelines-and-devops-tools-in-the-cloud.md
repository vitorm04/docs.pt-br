---
title: Modernizar ciclo de vida do aplicativo com pipelines de CI/CD e ferramentas do DevOps na nuvem
description: Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Modernizar ciclo de vida do aplicativo com pipelines de CI/CD e ferramentas do DevOps na nuvem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56dbd4a867e0f47d0f7e681d924584629d763f87
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="a0a0f-103">Modernizar ciclo de vida do aplicativo com pipelines de CI/CD e ferramentas do DevOps na nuvem</span><span class="sxs-lookup"><span data-stu-id="a0a0f-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="a0a0f-104">As empresas de hoje precisam inovar em um ritmo acelerado para sermos competitivos no mercado.</span><span class="sxs-lookup"><span data-stu-id="a0a0f-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="a0a0f-105">Entrega de alta qualidade, os aplicativos modernos requer DevOps ferramentas e os processos que são essenciais para implementar esse ciclo constante de inovação.</span><span class="sxs-lookup"><span data-stu-id="a0a0f-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="a0a0f-106">Com as ferramentas corretas do DevOps, os desenvolvedores podem simplificar a implantação contínua e obter aplicativos inovadores nas mãos de usuários mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="a0a0f-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="a0a0f-107">Embora as práticas recomendadas de implantação e a integração contínuas são bem estabelecidas, a introdução de contêineres apresenta novas considerações, especialmente quando você estiver trabalhando com aplicativos de multi contêiner.</span><span class="sxs-lookup"><span data-stu-id="a0a0f-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="a0a0f-108">Visual Studio Team Services dá suporte à integração contínua e implantação de aplicativos de contêiner vários para vários ambientes pelas tarefas de implantação do Team Services oficiais:</span><span class="sxs-lookup"><span data-stu-id="a0a0f-108">Visual Studio Team Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Team Services deployment tasks:</span></span>

-   <span data-ttu-id="a0a0f-109">[Implantar a VM do Host de Docker autônoma](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux ou Windows Server 2016 ou posterior)</span><span class="sxs-lookup"><span data-stu-id="a0a0f-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="a0a0f-110">Implantar a malha do serviço</span><span class="sxs-lookup"><span data-stu-id="a0a0f-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="a0a0f-111">Implantação de serviço de contêiner do Azure – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a0a0f-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="a0a0f-112">Mas você também pode implantar em [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS usando as tarefas do Team Services baseado em script.</span><span class="sxs-lookup"><span data-stu-id="a0a0f-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Team Services script-based tasks.</span></span>

<span data-ttu-id="a0a0f-113">Para continuar facilitando a agilidade da implantação, essas ferramentas oferecem experiências de implantação excelente de desenvolvimento para teste de produção de cargas de trabalho de contêiner, com uma opção de desenvolvimento e soluções de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="a0a0f-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="a0a0f-114">Figura 4-12 mostra um pipeline de implantação contínua que implanta um cluster Kubernetes no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="a0a0f-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Pipeline de implantação contínua do Visual Studio Team Services, implantando um cluster Kubernetes](./media/image12.png)

> <span data-ttu-id="a0a0f-116">**Figura 4-12.**</span><span class="sxs-lookup"><span data-stu-id="a0a0f-116">**Figure 4-12.**</span></span> <span data-ttu-id="a0a0f-117">Pipeline de implantação contínua do Visual Studio Team Services, implantando um cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="a0a0f-117">Visual Studio Team Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a0a0f-118">[Anterior](modernize-your-apps-with-monitoring-and-telemetry.md)
[Próximo](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="a0a0f-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
