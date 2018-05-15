---
title: Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="9dd46-103">Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="9dd46-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="9dd46-104">Instâncias de contêiner do Azure proposta de valor principal é que você pode implantar imediatamente contêineres a ele e você não precisa manter o ambiente, você não precisa atualização/patch do sistema de operacional de subjacentes ou VMs, tudo isso é transparente e você acabou de implantar contêineres em um ambiente pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="9dd46-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlaying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="9dd46-105">As razões e os cenários nos quais você deseja usar ACI são semelhantes para os cenários principais ao usar máquinas virtuais do Azure com contêineres, basicamente, os cenários principais para usar instâncias de contêiner do Azure são:</span><span class="sxs-lookup"><span data-stu-id="9dd46-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

-   <span data-ttu-id="9dd46-106">**Cenários de desenvolvimento/teste**</span><span class="sxs-lookup"><span data-stu-id="9dd46-106">**Dev/Test scenarios**</span></span>
-   <span data-ttu-id="9dd46-107">**Automação de tarefas**</span><span class="sxs-lookup"><span data-stu-id="9dd46-107">**Task automation**</span></span>
-   <span data-ttu-id="9dd46-108">**Agentes de CI/CD**</span><span class="sxs-lookup"><span data-stu-id="9dd46-108">**CI/CD agents**</span></span>
-   <span data-ttu-id="9dd46-109">**Processamento em lotes de pequeno ou escala.**</span><span class="sxs-lookup"><span data-stu-id="9dd46-109">**Small/scale batch processing**</span></span>
-   <span data-ttu-id="9dd46-110">**Aplicativos da web simples**</span><span class="sxs-lookup"><span data-stu-id="9dd46-110">**Simple web apps**</span></span>

<span data-ttu-id="9dd46-111">O cenário de aplicativos da web simples é um cenário razoável para ACI mas levar em conta que desde ACI você só pode ter uma instância única de contêiner por imagem de contêiner, você não tem alta disponibilidade e só possui escalabilidade limitada.</span><span class="sxs-lookup"><span data-stu-id="9dd46-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="9dd46-112">No entanto, mesmo quando ACI é considerado infraestrutura porque ele fornece apenas instâncias de contêiner único, há um grande benefício comparado para regular VMs do Azure com o Windows Server.</span><span class="sxs-lookup"><span data-stu-id="9dd46-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="9dd46-113">Com ACI, implantar apenas os contêineres em um ambiente automantido e pague apenas esses contêineres.</span><span class="sxs-lookup"><span data-stu-id="9dd46-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="9dd46-114">Você não precisa manter/atualização/patch VMs, portanto, é uma plataforma melhor para a maioria dos cenários em que talvez você esteja usando máquinas virtuais com contêineres.</span><span class="sxs-lookup"><span data-stu-id="9dd46-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="9dd46-115">Usar ACI é simples e prático, você implantar apenas um contêiner, não é necessário para criar um ambiente de VM que você implanta apenas os contêineres.</span><span class="sxs-lookup"><span data-stu-id="9dd46-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="9dd46-116">Os principais benefícios de instâncias de contêiner do Azure (ACI) são:</span><span class="sxs-lookup"><span data-stu-id="9dd46-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

-   <span data-ttu-id="9dd46-117">Executar contêineres sem gerenciar servidores</span><span class="sxs-lookup"><span data-stu-id="9dd46-117">Run containers without managing servers</span></span>
-   <span data-ttu-id="9dd46-118">Aumentar a agilidade com contêineres sob demanda</span><span class="sxs-lookup"><span data-stu-id="9dd46-118">Increase agility with containers on demand</span></span>
-   <span data-ttu-id="9dd46-119">Implantar contêineres para a nuvem com simplicidade precedentes e velocidade, com um único comando.</span><span class="sxs-lookup"><span data-stu-id="9dd46-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span> 
-   <span data-ttu-id="9dd46-120">Proteger aplicativos com o isolamento do hipervisor</span><span class="sxs-lookup"><span data-stu-id="9dd46-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="9dd46-121">Em resumo, com ACI, você pode desenvolver aplicativos sem gerenciamento de máquinas virtuais ou a necessidade de aprender novas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="9dd46-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="9dd46-122">É apenas o aplicativo em um contêiner em execução na nuvem.</span><span class="sxs-lookup"><span data-stu-id="9dd46-122">It's just your application, in a container, running in the cloud.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="9dd46-123">[Anterior](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Próximo](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="9dd46-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
