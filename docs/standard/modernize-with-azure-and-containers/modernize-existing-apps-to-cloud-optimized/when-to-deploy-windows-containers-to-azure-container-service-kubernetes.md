---
title: Quando implantar contêineres do Windows para o serviço de contêiner do Azure (ou seja, Kubernetes)
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para o serviço de contêiner do Azure (ou seja, Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758572"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="a721a-103">Quando implantar contêineres do Windows para o serviço de contêiner do Azure (ou seja, Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="a721a-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="a721a-104">O serviço de contêiner do Azure otimiza a configuração de tecnologias e ferramentas de código-fonte aberto populares especialmente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="a721a-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="a721a-105">Você obtém uma solução aberta que oferece portabilidade para seus contêineres e sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a721a-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="a721a-106">Você selecionar o tamanho, o número de hosts e as ferramentas do orchestrator.</span><span class="sxs-lookup"><span data-stu-id="a721a-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="a721a-107">O serviço de contêiner do Azure lida com a infraestrutura para você.</span><span class="sxs-lookup"><span data-stu-id="a721a-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="a721a-108">Se você já estiver trabalhando com código-fonte aberto orquestradores como Kubernetes, Docker Swarm ou DC/SO, você não precisa alterar suas práticas de gerenciamento existente para mover cargas de trabalho de contêiner para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="a721a-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="a721a-109">Use as ferramentas de gerenciamento de aplicativo que você já conhece e conectar-se por meio de pontos de extremidade de API padrão para o orquestrador de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="a721a-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="a721a-110">Todos esses orquestradores são ambientes de maduros se você estiver usando contêineres do Docker do Linux, mas só pode estar em estado de visualização para contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="a721a-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="a721a-111">Por exemplo, no Kubernetes, suporte para contêineres é nativo (cidadão de primeira classe), portanto, usar contêineres do Windows no Kubernetes também é eficaz (em visualização no ACS a partir do início de 2018).</span><span class="sxs-lookup"><span data-stu-id="a721a-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="a721a-112">Observação importante: O evoluído e "mais PaaS" versão do ACS (serviço de contêiner do Azure) para o Kubernetes é AKS (serviço de Kubernetes do Azure), no entanto, contêineres do Windows ainda não há suporte para a partir do Q2 2018, mas terá suporte em breve.</span><span class="sxs-lookup"><span data-stu-id="a721a-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a721a-113">[Anterior](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Próximo](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="a721a-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
