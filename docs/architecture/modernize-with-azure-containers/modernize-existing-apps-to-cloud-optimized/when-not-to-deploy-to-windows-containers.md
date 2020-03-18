---
title: Quando não implantar Contêineres do Windows
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Quando não implantar em contêineres do Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577949"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="a30cb-103">Quando não implantar Contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="a30cb-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="a30cb-104">Algumas tecnologias do Windows não são suportadas pelo Windows Containers.</span><span class="sxs-lookup"><span data-stu-id="a30cb-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="a30cb-105">Nesses casos, você ainda precisa migrar para os padrões de VMs, geralmente apenas com Windows e IIS.</span><span class="sxs-lookup"><span data-stu-id="a30cb-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="a30cb-106">Casos não suportados em contêineres windows, a partir de maio de 2018:</span><span class="sxs-lookup"><span data-stu-id="a30cb-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="a30cb-107">Atualmente, o Microsoft Message Queuing (MSMQ) só está disponível em contêineres do Windows com base na versão v1803 do Windows Server, mas não em outras versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="a30cb-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="a30cb-108">Fórum de solicitação de uservoice</span><span class="sxs-lookup"><span data-stu-id="a30cb-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="a30cb-109">Fórum de discussão</span><span class="sxs-lookup"><span data-stu-id="a30cb-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="a30cb-110">O Microsoft Distributed Transaction Coordinator (MSDTC) atualmente não é suportado em contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="a30cb-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="a30cb-111">Problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="a30cb-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="a30cb-112">Atualmente, o Microsoft Office não suporta contêineres.</span><span class="sxs-lookup"><span data-stu-id="a30cb-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="a30cb-113">Fórum de solicitação de uservoice</span><span class="sxs-lookup"><span data-stu-id="a30cb-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="a30cb-114">Aplicativos de interface do usuário (aplicativos clientes com interface de usuário visual) não são cenários suportados.</span><span class="sxs-lookup"><span data-stu-id="a30cb-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="a30cb-115">As funções de infra-estrutura do Windows (DNS, DHCP, DC, NTP, PRINT, Servidor de arquivos, IAM etc.) não são cenários suportados.</span><span class="sxs-lookup"><span data-stu-id="a30cb-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="a30cb-116">Para obter cenários e solicitações adicionais não suportados da comunidade, <https://windowsserver.uservoice.com/forums/304624-containers>consulte o fórum UserVoice para contêineres windows: .</span><span class="sxs-lookup"><span data-stu-id="a30cb-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a30cb-117">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="a30cb-117">Additional resources</span></span>

- <span data-ttu-id="a30cb-118">**Máquinas virtuais e contêineres no Azure**</span><span class="sxs-lookup"><span data-stu-id="a30cb-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="a30cb-119">[Próximo](deploy-existing-net-apps-as-windows-containers.md)
> [anterior](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="a30cb-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
