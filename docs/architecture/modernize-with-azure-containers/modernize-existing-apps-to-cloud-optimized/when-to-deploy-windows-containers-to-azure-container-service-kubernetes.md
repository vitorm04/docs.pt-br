---
title: Quando implantar contêineres do Windows no serviço de contêiner do Azure (ou seja, kubernetes)
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Quando implantar contêineres do Windows no serviço de contêiner do Azure (ou seja, kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577939"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="22ff8-103">Quando implantar contêineres do Windows no serviço de contêiner do Azure (ou seja, kubernetes)</span><span class="sxs-lookup"><span data-stu-id="22ff8-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="22ff8-104">O serviço de contêiner do Azure otimiza a configuração de ferramentas e tecnologias populares de software livre especificamente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="22ff8-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="22ff8-105">Você Obtém uma solução aberta que oferece portabilidade para seus contêineres e para a configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="22ff8-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="22ff8-106">Você seleciona o tamanho, o número de hosts e as ferramentas do Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="22ff8-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="22ff8-107">O serviço de contêiner do Azure lida com a infraestrutura para você.</span><span class="sxs-lookup"><span data-stu-id="22ff8-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="22ff8-108">Se você já estiver trabalhando com orquestradores de software livre como kubernetes, Docker Swarm ou DC/so, não será necessário alterar suas práticas de gerenciamento existentes para mover cargas de trabalho de contêiner para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="22ff8-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="22ff8-109">Use as ferramentas de gerenciamento de aplicativos com as quais você já está familiarizado e conecte-se por meio dos pontos de extremidade da API padrão para o orquestrador de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="22ff8-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="22ff8-110">Todos esses orquestradores são ambientes maduros se você estiver usando contêineres do Docker do Linux, mas só poderá estar em estado de visualização para contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="22ff8-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="22ff8-111">Por exemplo, no kubernetes, o suporte para contêineres é nativo (cidadão de primeira classe). portanto, usar contêineres do Windows no kubernetes também é eficaz (em versão prévia no ACS a partir do início 2018).</span><span class="sxs-lookup"><span data-stu-id="22ff8-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="22ff8-112">Observação importante: A versão evoluida e "mais PaaS" do ACS (serviço de contêiner do Azure) para kubernetes é AKS (serviço kubernetes do Azure). no entanto, os contêineres do Windows ainda não têm suporte a partir do segundo trimestre 2018, mas haverá suporte em breve.</span><span class="sxs-lookup"><span data-stu-id="22ff8-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="22ff8-113">[Anterior](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Próximo](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="22ff8-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
