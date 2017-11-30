---
title: "Quando não implantar contêineres do Windows"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Quando não implantar contêineres do Windows"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 538cb518cd169f42b3e8b7324ca108a1d366137a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="e5966-103">Quando não implantar contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="e5966-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="e5966-104">Algumas tecnologias do Windows não são suportadas pelos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="e5966-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="e5966-105">Nesses casos, você ainda precisa migrar para VMs de padrões, geralmente com apenas o Windows e o IIS.</span><span class="sxs-lookup"><span data-stu-id="e5966-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="e5966-106">Casos não tem suportados em contêineres do Windows, a partir de meados de 2017:</span><span class="sxs-lookup"><span data-stu-id="e5966-106">Cases not supported in Windows Containers, as of mid-2017:</span></span>

-   <span data-ttu-id="e5966-107">Serviço de enfileiramento de mensagens da Microsoft (MSMQ) atualmente não tem suporte em contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="e5966-107">Microsoft Message Queuing (MSMQ) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="e5966-108">Fórum de solicitação do UserVoice</span><span class="sxs-lookup"><span data-stu-id="e5966-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="e5966-109">Fórum de discussão</span><span class="sxs-lookup"><span data-stu-id="e5966-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="e5966-110">Microsoft Distributed Transaction coordenador (MSDTC) atualmente não tem suporte em contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="e5966-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers</span></span>

    -   [<span data-ttu-id="e5966-111">Problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="e5966-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="e5966-112">Microsoft Office não oferece suporte a contêineres</span><span class="sxs-lookup"><span data-stu-id="e5966-112">Microsoft Office currently does not support containers</span></span>

    -   [<span data-ttu-id="e5966-113">Fórum de solicitação do UserVoice</span><span class="sxs-lookup"><span data-stu-id="e5966-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

<span data-ttu-id="e5966-114">Para cenários adicionais não suportada e solicitações da comunidade, consulte o fórum do UserVoice para contêineres do Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="e5966-114">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e5966-115">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="e5966-115">Additional resources</span></span>

-   <span data-ttu-id="e5966-116">**Máquinas virtuais e contêineres no Azure**</span><span class="sxs-lookup"><span data-stu-id="e5966-116">**Virtual machines and containers in Azure**</span></span>

    [<span data-ttu-id="e5966-117">https://docs.microsoft.com/Azure/Virtual-Machines/Windows/Containers</span><span class="sxs-lookup"><span data-stu-id="e5966-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="e5966-118">[Anterior](deploy-existing-net-apps-as-windows-containers.md)
[Próximo](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="e5966-118">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
