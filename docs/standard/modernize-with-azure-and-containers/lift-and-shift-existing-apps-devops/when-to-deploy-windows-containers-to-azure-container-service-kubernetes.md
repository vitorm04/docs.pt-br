---
title: Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)
description: Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: e9f99e8a325dda730b05656993ba2e4e1e74e9cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="54acf-103">Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="54acf-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="54acf-104">Serviço de contêiner do Azure otimiza a configuração de tecnologias e ferramentas de código aberto populares especificamente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="54acf-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="54acf-105">Você obtém uma solução aberta que oferece portabilidade para seus contêineres e sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="54acf-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="54acf-106">Você seleciona o tamanho, o número de hosts e as ferramentas do orchestrator.</span><span class="sxs-lookup"><span data-stu-id="54acf-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="54acf-107">Serviço de contêiner do Azure lida com a infraestrutura para você.</span><span class="sxs-lookup"><span data-stu-id="54acf-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="54acf-108">Se você já estiver trabalhando com código-fonte aberto orchestrators como Kubernetes, Docker Swarm ou DC/sistema operacional, você não precisa alterar suas práticas de gerenciamento existente para mover cargas de trabalho do contêiner para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="54acf-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="54acf-109">Use as ferramentas de gerenciamento de aplicativo que você já estiver familiarizado com e conectar-se por meio de pontos de extremidade de API padrão para o orquestrador de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="54acf-109">Use the application management tools that you're already familiar with, and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="54acf-110">Todos esses orchestrators são ambientes maduras se você estiver usando contêineres do Docker do Linux, mas eles também suporte contêineres do Windows de 2017 (alguns anteriormente, outros mais recentemente, dependendo do orchestrator).</span><span class="sxs-lookup"><span data-stu-id="54acf-110">All these orchestrators are mature environments if you are using Linux Docker containers, but they also support Windows Containers as of 2017 (some earlier, some more recently, depending on the orchestrator).</span></span>

<span data-ttu-id="54acf-111">Por exemplo, em Kubernetes, o suporte para contêineres é nativo (cidadão de primeira classe), portanto, usar contêineres do Windows em Kubernetes também é muito eficiente e confiável (em visualização até logo se enquadram 2017).</span><span class="sxs-lookup"><span data-stu-id="54acf-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also very effective and reliable (in preview until early fall 2017).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="54acf-112">[Anterior](when-to-deploy-windows-containers-to-service-fabric.md)
[Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="54acf-112">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
