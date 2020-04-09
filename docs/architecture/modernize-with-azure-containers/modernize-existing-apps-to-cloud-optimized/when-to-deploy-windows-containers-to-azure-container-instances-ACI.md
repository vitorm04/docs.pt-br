---
title: Quando implantar os contêineres do Windows em ACI (ACI)
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Quando implantar os contêineres do Windows em ACI (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 6c889db6f0475f24a196144c7fb62faec4c173ed
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989149"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="6c8ae-103">Quando implantar os contêineres do Windows em ACI (ACI)</span><span class="sxs-lookup"><span data-stu-id="6c8ae-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="6c8ae-104">A principal proposta de valor do Azure Container Instances é que você pode implantar os contêineres imediatamente nele e não precisa manter esse ambiente, você não precisa atualizar/corrigir o sistema operacional ou VMs subjacentes, tudo isso é transparente e você simplesmente implanta contêineres em um ambiente pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don't need to maintain that environment, you don't need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="6c8ae-105">As razões e cenários em que você gostaria de usar a ACI são semelhantes aos principais cenários quando você usa VMs do Azure com contêineres, então, basicamente, os principais cenários para usar o Azure Container Instances são:</span><span class="sxs-lookup"><span data-stu-id="6c8ae-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="6c8ae-106">**Cenários de dev/teste**</span><span class="sxs-lookup"><span data-stu-id="6c8ae-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="6c8ae-107">**Automação de tarefas**</span><span class="sxs-lookup"><span data-stu-id="6c8ae-107">**Task automation**</span></span>
- <span data-ttu-id="6c8ae-108">**Agentes de CI/CD**</span><span class="sxs-lookup"><span data-stu-id="6c8ae-108">**CI/CD agents**</span></span>
- <span data-ttu-id="6c8ae-109">**Processamento de lotes em pequena escala**</span><span class="sxs-lookup"><span data-stu-id="6c8ae-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="6c8ae-110">**Aplicativos web simples**</span><span class="sxs-lookup"><span data-stu-id="6c8ae-110">**Simple web apps**</span></span>

<span data-ttu-id="6c8ae-111">O cenário simples de aplicativos web é um cenário justo para a ACI, mas leve em conta que, como na ACI você só pode ter uma única instância de contêiner por imagem de contêiner, você não terá alta disponibilidade e só terá escalabilidade limitada.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won't have high availability and only have limited scalability.</span></span>

<span data-ttu-id="6c8ae-112">No entanto, mesmo quando a ACI é considerada infra-estrutura porque apenas fornece instâncias de contêiner únicos, há um enorme benefício em comparação com as VMs azure regulares com o Windows Server.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="6c8ae-113">Com a ACI, basta implantar os contêineres em um ambiente auto-conservado e você só paga por esses contêineres.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="6c8ae-114">Você não precisa manter/atualizar/patch VMs, por isso é uma plataforma muito melhor para a maioria dos cenários onde você pode estar usando VMs com contêineres.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-114">You don't need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="6c8ae-115">O uso da ACI é direto, basta implantar um contêiner, não há necessidade de criar um ambiente de VM que você apenas implanta contêineres.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-115">Using ACI is straight forward, you just deploy a container, there's no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="6c8ae-116">Os principais benefícios da Azure Container Instances (ACI) são:</span><span class="sxs-lookup"><span data-stu-id="6c8ae-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="6c8ae-117">Executar contêineres sem gerenciar servidores</span><span class="sxs-lookup"><span data-stu-id="6c8ae-117">Run containers without managing servers</span></span>
- <span data-ttu-id="6c8ae-118">Aumente a agilidade com contêineres sob demanda</span><span class="sxs-lookup"><span data-stu-id="6c8ae-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="6c8ae-119">Implante contêineres na nuvem com simplicidade e velocidade sem precedentes — com um único comando.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="6c8ae-120">Aplicações seguras com isolamento de hipervisor</span><span class="sxs-lookup"><span data-stu-id="6c8ae-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="6c8ae-121">Em suma, com a ACI você pode desenvolver aplicativos rapidamente sem gerenciar máquinas virtuais ou ter que aprender novas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="6c8ae-122">É só sua aplicação, em um contêiner, correndo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="6c8ae-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="6c8ae-123">[Próximo](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="6c8ae-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
