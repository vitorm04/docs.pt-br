---
title: Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Modernizar o ciclo de vida de seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem
ms.date: 04/30/2018
ms.openlocfilehash: d1aa2e156e87cafe99fb994233786f67bf7a81a1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72396211"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="d9bc1-103">Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem</span><span class="sxs-lookup"><span data-stu-id="d9bc1-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="d9bc1-104">As empresas de hoje precisam inovar em um ritmo rápido para serem competitivas no Marketplace.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="d9bc1-105">O fornecimento de aplicativos modernos de alta qualidade exige ferramentas e processos de DevOps que são essenciais para implementar esse ciclo constante de inovação.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="d9bc1-106">Com as ferramentas DevOps certas, os desenvolvedores podem simplificar a implantação contínua e obter aplicativos inovadores para as mãos de usuários mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="d9bc1-107">Embora as práticas de integração e implantação contínuas sejam bem estabelecidas, a introdução dos contêineres apresenta novas considerações, especialmente quando você está trabalhando com aplicativos com vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="d9bc1-108">O Azure DevOps Services dá suporte à integração e à implantação contínuas de aplicativos de vários contêineres a uma variedade de ambientes por meio das tarefas oficiais de implantação de Azure DevOps Services:</span><span class="sxs-lookup"><span data-stu-id="d9bc1-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="d9bc1-109">Implantar em um Aplicativo Web para Contêineres do Azure</span><span class="sxs-lookup"><span data-stu-id="d9bc1-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="d9bc1-110">Implantar no serviço kubernetes do Azure</span><span class="sxs-lookup"><span data-stu-id="d9bc1-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="d9bc1-111">Mas você também pode implantar no [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS usando Azure DevOps Services tarefas baseadas em script.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="d9bc1-112">Para continuar a facilitar a agilidade da implantação, essas ferramentas fornecem excelentes experiências de implantação de desenvolvimento para teste para produção para cargas de trabalho de contêiner, com uma opção de desenvolvimento e soluções de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="d9bc1-113">A Figura 4-12 mostra um pipeline de implantação contínua que é implantado em um cluster kubernetes no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Captura de tela de Azure DevOps Services implantando em um cluster kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="d9bc1-115">**Figura 4-12.**</span><span class="sxs-lookup"><span data-stu-id="d9bc1-115">**Figure 4-12.**</span></span> <span data-ttu-id="d9bc1-116">Azure DevOps Services pipeline de implantação contínua, implantando em um cluster kubernetes</span><span class="sxs-lookup"><span data-stu-id="d9bc1-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d9bc1-117">[Anterior](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Próximo](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="d9bc1-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
