---
title: Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 03ee7c8b65e1a92dcc7fd40b44e9ba081f571487
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674400"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="c74d6-103">Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="c74d6-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="c74d6-104">Instâncias de contêiner do Azure proposta de valor principal é que você pode imediatamente implantar contêineres para ele e você não precisa manter esse ambiente, você não precisa atualizar/aplicar patch do sistema operacional subjacente ou a máquinas virtuais, tudo isso é transparente e você acabou de implantar contêineres em um ambiente pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="c74d6-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="c74d6-105">As razões e os cenários nos quais você iria querer usar ACI são semelhantes às principais cenários quando você usa VMs do Azure com os contêineres, basicamente, os cenários principais para usar instâncias de contêiner do Azure são:</span><span class="sxs-lookup"><span data-stu-id="c74d6-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="c74d6-106">**Cenários de desenvolvimento/teste**</span><span class="sxs-lookup"><span data-stu-id="c74d6-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="c74d6-107">**Automação de tarefas**</span><span class="sxs-lookup"><span data-stu-id="c74d6-107">**Task automation**</span></span>
- <span data-ttu-id="c74d6-108">**Agentes de CI/CD**</span><span class="sxs-lookup"><span data-stu-id="c74d6-108">**CI/CD agents**</span></span>
- <span data-ttu-id="c74d6-109">**Processamento de lote pequeno/escala**</span><span class="sxs-lookup"><span data-stu-id="c74d6-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="c74d6-110">**Aplicativos web simples**</span><span class="sxs-lookup"><span data-stu-id="c74d6-110">**Simple web apps**</span></span>

<span data-ttu-id="c74d6-111">O cenário de aplicativos web simples é um cenário razoável para ACI, mas leve em consideração que, pois em ACI, você pode ter apenas uma instância única de contêiner por imagem de contêiner, você não terá a alta disponibilidade e só possui escalabilidade limitada.</span><span class="sxs-lookup"><span data-stu-id="c74d6-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="c74d6-112">No entanto, mesmo quando ACI é considerado infraestrutura porque ele fornece apenas instâncias de contêiner único, há um enorme benefício em comparação às VMs comuns do Azure com o Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c74d6-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="c74d6-113">Com o ACI, você implantar apenas os contêineres em um ambiente mantido automaticamente e você paga apenas por esses contêineres.</span><span class="sxs-lookup"><span data-stu-id="c74d6-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="c74d6-114">Você não precisa manter/atualização/patch VMs, portanto, é uma plataforma melhor na maioria dos cenários em que talvez você esteja usando VMs com contêineres.</span><span class="sxs-lookup"><span data-stu-id="c74d6-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="c74d6-115">Usar ACI é muito simples, basta você implanta um contêiner, não é necessário para criar um ambiente de VM que você implantar apenas os contêineres.</span><span class="sxs-lookup"><span data-stu-id="c74d6-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="c74d6-116">Os principais benefícios de instâncias de contêiner do Azure (ACI) são:</span><span class="sxs-lookup"><span data-stu-id="c74d6-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="c74d6-117">Execute contêineres sem gerenciar servidores</span><span class="sxs-lookup"><span data-stu-id="c74d6-117">Run containers without managing servers</span></span>
- <span data-ttu-id="c74d6-118">Aumente a agilidade com contêineres sob demanda</span><span class="sxs-lookup"><span data-stu-id="c74d6-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="c74d6-119">Implantar contêineres para a nuvem com sem precedentes simplicidade e agilidade — com um único comando.</span><span class="sxs-lookup"><span data-stu-id="c74d6-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="c74d6-120">Proteger aplicativos com isolamento de hipervisor</span><span class="sxs-lookup"><span data-stu-id="c74d6-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="c74d6-121">Em resumo, com o ACI, você pode desenvolver aplicativos rapidamente sem gerenciar máquinas virtuais ou precisar aprender novas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="c74d6-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="c74d6-122">Ele é simplesmente o aplicativo em um contêiner em execução na nuvem.</span><span class="sxs-lookup"><span data-stu-id="c74d6-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="c74d6-123">[Anterior](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Próximo](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="c74d6-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
