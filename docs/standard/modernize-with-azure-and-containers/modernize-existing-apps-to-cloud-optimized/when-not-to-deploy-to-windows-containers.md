---
title: Quando não implantar contêineres do Windows
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Quando não implantar contêineres do Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 819f32955ff019414bef8820d17d272eddc11bf8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957956"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="ccfb0-103">Quando não implantar contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="ccfb0-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="ccfb0-104">Algumas tecnologias do Windows não são suportadas pelos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="ccfb0-105">Nesses casos, você ainda precisa migrar para VMs de padrões, geralmente com apenas o Windows e o IIS.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="ccfb0-106">Casos não tem suportados em contêineres do Windows, a partir de maio de 2018:</span><span class="sxs-lookup"><span data-stu-id="ccfb0-106">Cases not supported in Windows Containers, as of May 2018:</span></span> 

-   <span data-ttu-id="ccfb0-107">Serviço de enfileiramento de mensagens da Microsoft (MSMQ) atualmente está disponível apenas em contêineres do Windows com base na versão do Windows Server v1803, mas não em outras versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span> 

    -   [<span data-ttu-id="ccfb0-108">Fórum de solicitação do UserVoice</span><span class="sxs-lookup"><span data-stu-id="ccfb0-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="ccfb0-109">Fórum de discussão</span><span class="sxs-lookup"><span data-stu-id="ccfb0-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="ccfb0-110">Microsoft Distributed Transaction coordenador (MSDTC) atualmente não tem suporte em contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="ccfb0-111">Problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="ccfb0-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="ccfb0-112">Microsoft Office atualmente não dá suporte contêineres.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-112">Microsoft Office currently does not support containers.</span></span>

    -   [<span data-ttu-id="ccfb0-113">Fórum de solicitação do UserVoice</span><span class="sxs-lookup"><span data-stu-id="ccfb0-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   <span data-ttu-id="ccfb0-114">Aplicativos de interface do usuário (aplicativos de cliente com uma interface do usuário visual) não são cenários com suporte.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

-   <span data-ttu-id="ccfb0-115">Funções de infraestrutura do Windows (DNS, DHCP, DC, NTP, impressão, servidor de arquivos, etc. IAM) não são cenários com suporte.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>


<span data-ttu-id="ccfb0-116">Para cenários adicionais não suportada e solicitações da comunidade, consulte o fórum do UserVoice para contêineres do Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="ccfb0-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ccfb0-117">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="ccfb0-117">Additional resources</span></span>

-   <span data-ttu-id="ccfb0-118">**Máquinas virtuais e contêineres no Azure**</span><span class="sxs-lookup"><span data-stu-id="ccfb0-118">**Virtual machines and containers in Azure**</span></span>

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="ccfb0-119">[Anterior](deploy-existing-net-apps-as-windows-containers.md)
[Próximo](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="ccfb0-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
