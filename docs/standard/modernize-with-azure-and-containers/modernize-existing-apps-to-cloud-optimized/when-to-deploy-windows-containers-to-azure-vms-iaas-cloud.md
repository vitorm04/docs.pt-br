---
title: Quando implantar Contêineres do Windows para VMs do Azure (nuvem de IaaS)
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para VMs do Azure (nuvem de IaaS)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 51217e2c94fd9727c8f7907e791cdebaec98f14f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011951"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="867e7-103">Quando implantar Contêineres do Windows para VMs do Azure (nuvem de IaaS)</span><span class="sxs-lookup"><span data-stu-id="867e7-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="867e7-104">Se sua organização estiver usando VMs do Azure, mesmo se você também estiver usando contêineres do Windows, você ainda estiver lidando com IaaS.</span><span class="sxs-lookup"><span data-stu-id="867e7-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="867e7-105">Isso significa que lidar com operações de infraestrutura, patches de SO da VM e complexidade da infraestrutura para aplicativos altamente escalonáveis, quando você precisa implantar várias VMs em uma infraestrutura com balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="867e7-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="867e7-106">Os cenários principais para usar contêineres do Windows em uma VM do Azure são:</span><span class="sxs-lookup"><span data-stu-id="867e7-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

- <span data-ttu-id="867e7-107">**Ambiente de desenvolvimento/teste**: Uma VM na nuvem é perfeita para desenvolvimento e teste na nuvem.</span><span class="sxs-lookup"><span data-stu-id="867e7-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="867e7-108">Você pode rapidamente criar ou parar o ambiente, dependendo das suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="867e7-108">You can rapidly create or stop the environment depending on your needs.</span></span>

- <span data-ttu-id="867e7-109">**Precisa de escalabilidade de pequena e média**: Em cenários em que talvez sejam necessárias duas VMs para seu ambiente de produção, gerenciando uma pequena quantidade de VMs pode ser acessível até que você pode mover para ambientes de PaaS mais avançados, como orquestradores.</span><span class="sxs-lookup"><span data-stu-id="867e7-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

- <span data-ttu-id="867e7-110">**Ambiente de produção com as ferramentas de implantação existentes**: Você pode estar movendo de um ambiente local na qual você investiu nas ferramentas para fazer implantações complexas em VMs ou servidores bare-metal (como o Puppet ou ferramentas semelhantes).</span><span class="sxs-lookup"><span data-stu-id="867e7-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="867e7-111">Para mover para a nuvem com alterações mínimas aos procedimentos de implantação do ambiente de produção, você pode continuar a usar essas ferramentas para implantar em VMs do Azure.</span><span class="sxs-lookup"><span data-stu-id="867e7-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="867e7-112">No entanto, você desejará usar contêineres do Windows como a unidade de implantação para melhorar a experiência de implantação.</span><span class="sxs-lookup"><span data-stu-id="867e7-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="867e7-113">[Anterior](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[Próximo](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span><span class="sxs-lookup"><span data-stu-id="867e7-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)</span></span>