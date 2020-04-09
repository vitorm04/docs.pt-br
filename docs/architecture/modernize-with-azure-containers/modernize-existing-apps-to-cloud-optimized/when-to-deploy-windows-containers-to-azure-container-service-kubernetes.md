---
title: Quando implantar os contêineres do Windows no Azure Container Service (isto é, Kubernetes)
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Quando implantar os contêineres do Windows no Azure Container Service (isto é, Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 3ff51a70d4e158b831155ab4992ec32f5d98cedb
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987758"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="1e6a4-103">Quando implantar os contêineres do Windows no Azure Container Service (isto é, Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="1e6a4-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="1e6a4-104">O Azure Container Service otimiza a configuração de ferramentas e tecnologias de código aberto populares especificamente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="1e6a4-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="1e6a4-105">Você recebe uma solução aberta que oferece portabilidade tanto para seus contêineres quanto para a configuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1e6a4-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="1e6a4-106">Você seleciona o tamanho, o número de hosts e as ferramentas de orquestrador.</span><span class="sxs-lookup"><span data-stu-id="1e6a4-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="1e6a4-107">O Azure Container Service lida com a infra-estrutura para você.</span><span class="sxs-lookup"><span data-stu-id="1e6a4-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="1e6a4-108">Se você já está trabalhando com orquestradores de código aberto como Kubernetes, Docker Swarm ou DC/OS, você não precisa alterar suas práticas de gerenciamento existentes para mover cargas de trabalho de contêineres para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="1e6a4-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="1e6a4-109">Use as ferramentas de gerenciamento de aplicativos com as que você já está familiarizado e conecte-se através dos pontos finais padrão da API para o orquestrador de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1e6a4-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="1e6a4-110">Todos esses orquestradores são ambientes maduros se você estiver usando contêineres Linux Docker, mas pode estar apenas no estado de visualização para contêineres windows.</span><span class="sxs-lookup"><span data-stu-id="1e6a4-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="1e6a4-111">Por exemplo, em Kubernetes, o suporte para contêineres é nativo (cidadão de primeira classe), então usar o Windows Containers no Kubernetes também é eficaz (em visualização em ACS a partir do início de 2018).</span><span class="sxs-lookup"><span data-stu-id="1e6a4-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="1e6a4-112">Nota importante: A versão evoluída e "mais PaaS" do ACS (Azure Container Service) para Kubernetes é AKS (Azure Kubernetes Service), no entanto, os Contêineres Windows ainda não são suportados a partir do 2º trimestre de 2018, mas serão suportados em breve.</span><span class="sxs-lookup"><span data-stu-id="1e6a4-112">Important note: The evolved and "more PaaS" version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1e6a4-113">[Próximo](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[anterior](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="1e6a4-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
