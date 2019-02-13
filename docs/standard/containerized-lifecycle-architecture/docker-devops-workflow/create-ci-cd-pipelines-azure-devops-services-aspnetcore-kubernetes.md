---
title: Etapas no fluxo de trabalho de DevOps loop externo para um aplicativo do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 7a98c34bfdbbdc9b34a04c891ca031f454ac4396
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221455"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="93608-103">Criando pipelines de CI/CD nos serviços de DevOps do Azure para um aplicativo .NET Core 2.0 em contêineres e implantar um cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="93608-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="93608-104">Figura 5 a 12, você pode ver o cenário de DevOps de ponta a ponta que abrange o gerenciamento de código, compilação de código, compilação de imagens do Docker, imagens do Docker por push para um registro de Docker e, finalmente, a implantação em um cluster Kubernetes no Azure.</span><span class="sxs-lookup"><span data-stu-id="93608-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Fluxo de trabalho: É iniciado no computador de desenvolvimento.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="93608-107">**Figura 5-12**.</span><span class="sxs-lookup"><span data-stu-id="93608-107">**Figure 5-12**.</span></span> <span data-ttu-id="93608-108">Cenário de CI/CD, criação de imagens do Docker e implantar um cluster Kubernetes no Azure</span><span class="sxs-lookup"><span data-stu-id="93608-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="93608-109">É importante destacar que o dois pipelines e dos build/CI/CD do produto, são conectados por meio de registro do Docker (como o Hub do Docker ou registro de contêiner do Azure).</span><span class="sxs-lookup"><span data-stu-id="93608-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="93608-110">O registro do Docker é uma das principais diferenças em comparação comparadas um processo de CI/CD tradicional sem o Docker.</span><span class="sxs-lookup"><span data-stu-id="93608-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="93608-111">Conforme mostrado na Figura 5-13, a primeira fase é o pipeline de build/CI.</span><span class="sxs-lookup"><span data-stu-id="93608-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="93608-112">Nos serviços de DevOps do Azure, você pode criar pipelines de build/CD que compilar o código, criar as imagens do Docker e enviar por push para um registro de Docker, como o Hub do Docker ou registro de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="93608-112">In Azure DevOps Services you can create build/CD pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="93608-113">**Figura 5-13**.</span><span class="sxs-lookup"><span data-stu-id="93608-113">**Figure 5-13**.</span></span> <span data-ttu-id="93608-114">Pipeline de build/CI no DevOps do Azure criando imagens do Docker e enviar imagens por push para um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="93608-114">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="93608-115">A segunda fase é criar um pipeline de lançamento/implantação.</span><span class="sxs-lookup"><span data-stu-id="93608-115">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="93608-116">Nos serviços de DevOps do Azure, você pode facilmente criar um pipeline de implantação, direcionando um cluster Kubernetes usando as tarefas de Kubernetes para os serviços de DevOps do Azure, conforme mostrado na Figura 5-14.</span><span class="sxs-lookup"><span data-stu-id="93608-116">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Implantar o MVC](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="93608-118">**Figura 5-14**.</span><span class="sxs-lookup"><span data-stu-id="93608-118">**Figure 5-14**.</span></span> <span data-ttu-id="93608-119">Pipeline de lançamento/CD na implantação de serviços de DevOps do Azure para um cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="93608-119">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Instruções passo a passo]<span data-ttu-id="93608-120"> Implantando eShopModernized para Kubernetes:</span><span class="sxs-lookup"><span data-stu-id="93608-120"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="93608-121">Para obter uma explicação detalhada de pipelines do Azure DevOps CI/CD, implantação de Kubernetes, consulte esta postagem: \\</span><span class="sxs-lookup"><span data-stu-id="93608-121">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: \\</span></span>
>[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

>[!div class="step-by-step"]
><span data-ttu-id="93608-122">[Anterior](docker-application-outer-loop-devops-workflow.md)
>[Próximo](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="93608-122">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
