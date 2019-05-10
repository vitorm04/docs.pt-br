---
title: Quando não implantar Contêineres do Windows
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Quando não implantar para contêineres do Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: e06793065d1fd55bbef855576174b07dc9ace4c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751391"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="ab51f-103">Quando não implantar Contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="ab51f-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="ab51f-104">Algumas tecnologias do Windows não têm suporte pelos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="ab51f-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="ab51f-105">Nesses casos, você ainda precisará migrar para VMs de padrões, geralmente com apenas o Windows e o IIS.</span><span class="sxs-lookup"><span data-stu-id="ab51f-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="ab51f-106">Casos de não tem suportados em contêineres do Windows, a partir de maio de 2018:</span><span class="sxs-lookup"><span data-stu-id="ab51f-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="ab51f-107">Microsoft Message Queuing (MSMQ) atualmente só está disponível em contêineres do Windows com base na versão do Windows Server v1803, mas não em outras versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="ab51f-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="ab51f-108">Fórum de solicitação do UserVoice</span><span class="sxs-lookup"><span data-stu-id="ab51f-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="ab51f-109">Fórum de discussão</span><span class="sxs-lookup"><span data-stu-id="ab51f-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="ab51f-110">Microsoft Distributed Transaction coordenador (MSDTC) atualmente não tem suporte em contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="ab51f-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="ab51f-111">Problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="ab51f-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="ab51f-112">Microsoft Office atualmente não dão suporte a contêineres.</span><span class="sxs-lookup"><span data-stu-id="ab51f-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="ab51f-113">Fórum de solicitação do UserVoice</span><span class="sxs-lookup"><span data-stu-id="ab51f-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="ab51f-114">Aplicativos de interface do usuário (aplicativos de cliente com uma interface do usuário visual) não são cenários com suporte.</span><span class="sxs-lookup"><span data-stu-id="ab51f-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="ab51f-115">Funções de infraestrutura do Windows (DNS, DHCP, DC, NTP, impressão, servidor de arquivos, etc. IAM) não são os cenários com suporte.</span><span class="sxs-lookup"><span data-stu-id="ab51f-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="ab51f-116">Para solicitações da comunidade e outros cenários sem suporte, consulte o fórum do UserVoice para contêineres do Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="ab51f-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ab51f-117">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="ab51f-117">Additional resources</span></span>

- <span data-ttu-id="ab51f-118">**Máquinas virtuais e contêineres no Azure**</span><span class="sxs-lookup"><span data-stu-id="ab51f-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="ab51f-119">[Anterior](deploy-existing-net-apps-as-windows-containers.md)
> [Próximo](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="ab51f-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
