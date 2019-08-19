---
title: Quando implantar contêineres do Windows em ACI (instâncias de contêiner do Azure)
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Quando implantar contêineres do Windows em ACI (instâncias de contêiner do Azure)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577929"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a><span data-ttu-id="1a79a-103">Quando implantar contêineres do Windows em ACI (instâncias de contêiner do Azure)</span><span class="sxs-lookup"><span data-stu-id="1a79a-103">When to deploy Windows Containers to Azure Container Instances (ACI)</span></span>

<span data-ttu-id="1a79a-104">A principal proposta de valor das instâncias de contêiner do Azure é que você pode imediatamente implantar contêineres nela e não precisa manter esse ambiente, você não precisa atualizar/aplicar patch ao sistema operacional ou às VMs subjacentes, tudo isso é transparente e apenas implantar contêineres em um ambiente pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="1a79a-104">Azure Container Instances main value proposition is that you can right away deploy containers to it and you don’t need to maintain that environment, you don’t need to upgrade/patch the underlying operating system or VMs, all that is transparent and you just deploy containers into a ready-to-use environment.</span></span>

<span data-ttu-id="1a79a-105">Os motivos e cenários em que você desejaria usar o ACI são semelhantes aos principais cenários quando você usa VMs do Azure com contêineres, portanto, basicamente, os principais cenários para usar as instâncias de contêiner do Azure são:</span><span class="sxs-lookup"><span data-stu-id="1a79a-105">The reasons and scenarios when you would want to use ACI are similar to the main scenarios when you use Azure VMs with containers, so basically, the main scenarios for using Azure Container Instances are:</span></span>

- <span data-ttu-id="1a79a-106">**Cenários de desenvolvimento/teste**</span><span class="sxs-lookup"><span data-stu-id="1a79a-106">**Dev/Test scenarios**</span></span>
- <span data-ttu-id="1a79a-107">**Automação de tarefas**</span><span class="sxs-lookup"><span data-stu-id="1a79a-107">**Task automation**</span></span>
- <span data-ttu-id="1a79a-108">**Agentes de CI/CD**</span><span class="sxs-lookup"><span data-stu-id="1a79a-108">**CI/CD agents**</span></span>
- <span data-ttu-id="1a79a-109">**Processamento em lotes de pequena/escala**</span><span class="sxs-lookup"><span data-stu-id="1a79a-109">**Small/scale batch processing**</span></span>
- <span data-ttu-id="1a79a-110">**Aplicativos Web simples**</span><span class="sxs-lookup"><span data-stu-id="1a79a-110">**Simple web apps**</span></span>

<span data-ttu-id="1a79a-111">O cenário de aplicativos Web simples é um cenário justo para ACI, mas leve em conta que, desde o ACI, você só pode ter uma única instância de contêiner por imagem de contêiner, não terá alta disponibilidade e terá apenas escalabilidade limitada.</span><span class="sxs-lookup"><span data-stu-id="1a79a-111">The simple web apps scenario is a fair scenario for ACI but take into account that since in ACI you can only have a single container instance per container image, you won’t have high availability and only have limited scalability.</span></span>

<span data-ttu-id="1a79a-112">No entanto, mesmo quando o ACI é considerado uma infraestrutura porque ele apenas fornece instâncias de contêiner único, há um grande benefício em comparação com as VMs regulares do Azure com o Windows Server.</span><span class="sxs-lookup"><span data-stu-id="1a79a-112">However, even when ACI is considered infrastructure because it just provides single container instances, there is a huge benefit compared to regular Azure VMs with Windows Server.</span></span> <span data-ttu-id="1a79a-113">Com o ACI, você apenas implanta os contêineres em um ambiente automantido e só paga por esses contêineres.</span><span class="sxs-lookup"><span data-stu-id="1a79a-113">With ACI, you just deploy the containers into a self-maintained environment and you just pay for those containers.</span></span> <span data-ttu-id="1a79a-114">Você não precisa manter/atualizar/corrigir VMs, portanto é uma plataforma muito melhor para a maioria dos cenários em que você pode estar usando VMs com contêineres.</span><span class="sxs-lookup"><span data-stu-id="1a79a-114">You don’t need to maintain/update/patch VMs, so it is a much better platform for most scenarios where you might be using VMs with containers.</span></span> <span data-ttu-id="1a79a-115">Usar o ACI é um avanço direto, você simplesmente implanta um contêiner, não há necessidade de criar um ambiente de VM que você apenas implante contêineres.</span><span class="sxs-lookup"><span data-stu-id="1a79a-115">Using ACI is straight forward, you just deploy a container, there’s no need to create a VM environment you just deploy containers.</span></span>

<span data-ttu-id="1a79a-116">Os principais benefícios das ACI (instâncias de contêiner do Azure) são:</span><span class="sxs-lookup"><span data-stu-id="1a79a-116">The main benefits of Azure Container Instances (ACI) are:</span></span>

- <span data-ttu-id="1a79a-117">Executar contêineres sem gerenciar servidores</span><span class="sxs-lookup"><span data-stu-id="1a79a-117">Run containers without managing servers</span></span>
- <span data-ttu-id="1a79a-118">Aumentar a agilidade com contêineres sob demanda</span><span class="sxs-lookup"><span data-stu-id="1a79a-118">Increase agility with containers on demand</span></span>
- <span data-ttu-id="1a79a-119">Implante contêineres na nuvem com simplicidade e velocidade sem precedentes, com um único comando.</span><span class="sxs-lookup"><span data-stu-id="1a79a-119">Deploy containers to the cloud with unprecedented simplicity and speed—with a single command.</span></span>
- <span data-ttu-id="1a79a-120">Proteger aplicativos com isolamento de hipervisor</span><span class="sxs-lookup"><span data-stu-id="1a79a-120">Secure applications with hypervisor isolation</span></span>

<span data-ttu-id="1a79a-121">Em suma, com o ACI, você pode desenvolver aplicativos rapidamente sem gerenciar máquinas virtuais ou ter que aprender novas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="1a79a-121">In short, with ACI you can develop apps fast without managing virtual machines or having to learn new tools.</span></span> <span data-ttu-id="1a79a-122">É apenas seu aplicativo, em um contêiner, em execução na nuvem.</span><span class="sxs-lookup"><span data-stu-id="1a79a-122">It's just your application, in a container, running in the cloud.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="1a79a-123">[Anterior](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Próximo](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="1a79a-123">[Previous](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Next](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)</span></span>
