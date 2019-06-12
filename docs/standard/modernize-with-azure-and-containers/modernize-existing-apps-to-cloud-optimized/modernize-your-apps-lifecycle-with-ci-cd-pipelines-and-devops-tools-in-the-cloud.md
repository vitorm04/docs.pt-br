---
title: Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Modernize o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833950"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="92b4a-103">Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem</span><span class="sxs-lookup"><span data-stu-id="92b4a-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="92b4a-104">As empresas de hoje precisam inovar em um ritmo acelerado para sermos competitivos no marketplace.</span><span class="sxs-lookup"><span data-stu-id="92b4a-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="92b4a-105">Fornecimento de alta qualidade, aplicativos modernos requer ferramentas de DevOps e os processos que são essenciais para implementar esse ciclo constante da inovação.</span><span class="sxs-lookup"><span data-stu-id="92b4a-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="92b4a-106">Com as ferramentas certas do DevOps, os desenvolvedores podem simplificar a implantação contínua e obter aplicativos inovadores nas mãos de usuários mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="92b4a-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="92b4a-107">Embora as práticas de implantação e integração contínuas sejam bem estabelecidas, a introdução de contêineres apresenta novas considerações, especialmente quando você estiver trabalhando com aplicativos de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="92b4a-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="92b4a-108">Serviços de DevOps do Azure dá suporte à integração contínua e implantação de aplicativos de vários contêineres em uma variedade de ambientes por meio de tarefas de implantação de serviços de DevOps do Azure oficiais:</span><span class="sxs-lookup"><span data-stu-id="92b4a-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="92b4a-109">Implantar um aplicativo Web do Azure para contêineres</span><span class="sxs-lookup"><span data-stu-id="92b4a-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [<span data-ttu-id="92b4a-110">Implantar no serviço de contêiner do Azure – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="92b4a-110">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="92b4a-111">Mas você também pode implantar em [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS usando serviços de DevOps do Azure baseada em script as tarefas.</span><span class="sxs-lookup"><span data-stu-id="92b4a-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="92b4a-112">Para continuar promovendo a agilidade de implantação, essas ferramentas oferecem experiências de implantação de desenvolvimento para teste para produção excelente para cargas de trabalho de contêiner, com uma opção de desenvolvimento e soluções de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="92b4a-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="92b4a-113">Figura 4-12 mostra um pipeline de implantação contínua que implanta em um cluster Kubernetes no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="92b4a-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Pipeline de implantação contínua de serviços de DevOps do Azure, implantar um cluster Kubernetes](./media/image12.png)

> <span data-ttu-id="92b4a-115">**Figura 4 a 12.**</span><span class="sxs-lookup"><span data-stu-id="92b4a-115">**Figure 4-12.**</span></span> <span data-ttu-id="92b4a-116">Pipeline de implantação contínua de serviços de DevOps do Azure, implantar um cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="92b4a-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="92b4a-117">[Anterior](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Próximo](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="92b4a-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
