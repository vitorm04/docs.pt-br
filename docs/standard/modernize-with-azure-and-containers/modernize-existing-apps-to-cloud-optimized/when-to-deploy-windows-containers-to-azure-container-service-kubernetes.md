---
title: Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958166"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="faef9-103">Quando implantar contêineres do Windows para serviço de contêiner do Azure (ou seja, Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="faef9-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="faef9-104">Serviço de contêiner do Azure otimiza a configuração de tecnologias e ferramentas de código aberto populares especificamente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="faef9-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="faef9-105">Você obtém uma solução aberta que oferece portabilidade para seus contêineres e sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="faef9-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="faef9-106">Você seleciona o tamanho, o número de hosts e as ferramentas do orchestrator.</span><span class="sxs-lookup"><span data-stu-id="faef9-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="faef9-107">Serviço de contêiner do Azure lida com a infraestrutura para você.</span><span class="sxs-lookup"><span data-stu-id="faef9-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="faef9-108">Se você já estiver trabalhando com código-fonte aberto orchestrators como Kubernetes, Docker Swarm ou DC/sistema operacional, você não precisa alterar suas práticas de gerenciamento existente para mover cargas de trabalho do contêiner para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="faef9-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="faef9-109">Use as ferramentas de gerenciamento de aplicativo que você já estiver familiarizado com e conectar-se por meio de pontos de extremidade de API padrão para o orquestrador de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="faef9-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="faef9-110">Todos esses orchestrators são ambientes maduras, se você estiver usando contêineres do Docker do Linux, mas só pode estar em estado de visualização para contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="faef9-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="faef9-111">Por exemplo, em Kubernetes, o suporte para contêineres é nativo (cidadão de primeira classe), portanto, usar contêineres do Windows em Kubernetes também é efetivo (em visualização no ACS a partir do início 2018).</span><span class="sxs-lookup"><span data-stu-id="faef9-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="faef9-112">Observação importante: O evoluído e "mais PaaS" versão do ACS (serviço de contêiner do Azure) para Kubernetes é AKS (serviço de Kubernetes do Azure), no entanto, os contêineres do Windows ainda não há suporte para a partir de Q2 2018, mas terá suporte em breve.</span><span class="sxs-lookup"><span data-stu-id="faef9-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="faef9-113">[Anterior](when-to-deploy-windows-containers-to-service-fabric.md)
[Próximo](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="faef9-113">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
