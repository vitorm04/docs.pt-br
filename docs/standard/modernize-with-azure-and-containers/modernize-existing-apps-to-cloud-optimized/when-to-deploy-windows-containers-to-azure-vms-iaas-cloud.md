---
title: Quando implantar contêineres do Windows para VMs do Azure (IaaS nuvem)
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para VMs do Azure (IaaS nuvem)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 7472745577f414062b460fd71ab45bae85d7a62e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958016"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="a921f-103">Quando implantar contêineres do Windows para VMs do Azure (IaaS nuvem)</span><span class="sxs-lookup"><span data-stu-id="a921f-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="a921f-104">Se sua organização estiver usando máquinas virtuais do Azure, mesmo se você também estiver usando contêineres do Windows, você ainda está lidando com IaaS.</span><span class="sxs-lookup"><span data-stu-id="a921f-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="a921f-105">Isso significa que lidar com operações de infra-estrutura, patches do sistema operacional da VM e a complexidade de infraestrutura para aplicativos altamente escalonáveis quando você precisa implantar várias VMs em uma infraestrutura com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="a921f-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="a921f-106">Os cenários principais para usar contêineres do Windows em uma VM do Azure são:</span><span class="sxs-lookup"><span data-stu-id="a921f-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="a921f-107">**Ambiente de desenvolvimento/teste**: uma VM na nuvem é perfeita para desenvolvimento e teste na nuvem.</span><span class="sxs-lookup"><span data-stu-id="a921f-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="a921f-108">Você pode rapidamente criar ou parar o ambiente dependendo de suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="a921f-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="a921f-109">**Precisa de escalabilidade de pequena e média**: em cenários onde você pode precisar apenas algumas das VMs de seu ambiente de produção, Gerenciando um pequeno número de VMs pode estar acessível até que você pode mover para ambientes de PaaS mais avançadas, como orchestrators.</span><span class="sxs-lookup"><span data-stu-id="a921f-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="a921f-110">**Ambiente de produção com as ferramentas de implantação existentes**: você pode mover de um ambiente local em que você investiu nas ferramentas de fazer implantações complexas VMs ou bare-metal servidores (como Puppet ou ferramentas semelhantes).</span><span class="sxs-lookup"><span data-stu-id="a921f-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="a921f-111">Para mover para a nuvem com mínimas alterações para procedimentos de implantação do ambiente de produção, você pode continuar a usar essas ferramentas para implantar máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="a921f-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="a921f-112">No entanto, você desejará usar contêineres do Windows como a unidade de implantação para melhorar a experiência de implantação.</span><span class="sxs-lookup"><span data-stu-id="a921f-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a921f-113">[Anterior](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Próximo](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="a921f-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>
