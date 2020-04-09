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
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="879d2-103">Modernizar o ciclo de vida do seu aplicativo com pipelines de CI/CD e ferramentas de DevOps na nuvem</span><span class="sxs-lookup"><span data-stu-id="879d2-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="879d2-104">As empresas de hoje precisam inovar em um ritmo rápido para serem competitivas no mercado.</span><span class="sxs-lookup"><span data-stu-id="879d2-104">Today's businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="879d2-105">Fornecer aplicações modernas e de alta qualidade requer ferramentas e processos DevOps que são fundamentais para implementar esse ciclo constante de inovação.</span><span class="sxs-lookup"><span data-stu-id="879d2-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="879d2-106">Com as ferramentas DevOps certas, os desenvolvedores podem simplificar a implantação contínua e colocar aplicativos inovadores nas mãos dos usuários mais rapidamente.</span><span class="sxs-lookup"><span data-stu-id="879d2-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="879d2-107">Embora as práticas de integração e implantação contínuas estejam bem estabelecidas, a introdução de contêineres introduz novas considerações, especialmente quando você está trabalhando com aplicações de vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="879d2-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="879d2-108">O Azure DevOps Services suporta integração contínua e implantação de aplicativos de vários contêineres para uma variedade de ambientes através das tarefas oficiais de implantação do Azure DevOps Services:</span><span class="sxs-lookup"><span data-stu-id="879d2-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="879d2-109">Implantar em um aplicativo web do Azure para contêineres</span><span class="sxs-lookup"><span data-stu-id="879d2-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="879d2-110">Implantar no Serviço Azure Kubernetes</span><span class="sxs-lookup"><span data-stu-id="879d2-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="879d2-111">Mas você também pode implantar no [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) ou DC/OS usando tarefas baseadas em script do Azure DevOps Services.</span><span class="sxs-lookup"><span data-stu-id="879d2-111">But you also can deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="879d2-112">Para continuar facilitando a agilidade de implantação, essas ferramentas fornecem excelentes experiências de implantação de desenvolvimento para teste-para-produção para cargas de trabalho de contêineres, com uma escolha de desenvolvimento e soluções de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="879d2-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="879d2-113">A Figura 4-12 mostra um pipeline de implantação contínua que é implantado em um cluster Kubernetes no Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="879d2-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Captura de tela dos Serviços Azure DevOps implantados em um cluster Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="879d2-115">**Figura 4-12.**</span><span class="sxs-lookup"><span data-stu-id="879d2-115">**Figure 4-12.**</span></span> <span data-ttu-id="879d2-116">Azure DevOps Services gasoduto de implantação contínua, implantando em um cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="879d2-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="879d2-117">[Próximo](modernize-your-apps-with-monitoring-and-telemetry.md)
>[anterior](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="879d2-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
