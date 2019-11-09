---
title: Quando não implantar Contêineres do Windows
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Quando não implantar em contêineres do Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2019
ms.locfileid: "69577949"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="2f80b-103">Quando não implantar Contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="2f80b-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="2f80b-104">Não há suporte para algumas tecnologias do Windows nos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="2f80b-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="2f80b-105">Nesses casos, você ainda precisa migrar para VMs de padrões, geralmente com apenas Windows e IIS.</span><span class="sxs-lookup"><span data-stu-id="2f80b-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="2f80b-106">Não há suporte para casos em contêineres do Windows, a partir de maio de 2018:</span><span class="sxs-lookup"><span data-stu-id="2f80b-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="2f80b-107">O serviço de enfileiramento de mensagens da Microsoft (MSMQ) atualmente só está disponível em contêineres do Windows com base na versão v1803 do Windows Server, mas não em outras versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="2f80b-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="2f80b-108">Fórum de solicitações do UserVoice</span><span class="sxs-lookup"><span data-stu-id="2f80b-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="2f80b-109">Fórum de discussão</span><span class="sxs-lookup"><span data-stu-id="2f80b-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="2f80b-110">No momento, não há suporte para o Microsoft Coordenador de Transações Distribuídas (MSDTC) em contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="2f80b-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="2f80b-111">Problema do GitHub</span><span class="sxs-lookup"><span data-stu-id="2f80b-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="2f80b-112">Microsoft Office atualmente não oferece suporte a contêineres.</span><span class="sxs-lookup"><span data-stu-id="2f80b-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="2f80b-113">Fórum de solicitações do UserVoice</span><span class="sxs-lookup"><span data-stu-id="2f80b-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="2f80b-114">Os aplicativos de IU (aplicativos cliente com uma interface do usuário Visual) não são cenários com suporte.</span><span class="sxs-lookup"><span data-stu-id="2f80b-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="2f80b-115">As funções de infraestrutura do Windows (DNS, DHCP, DC, NTP, PRINT, servidor de arquivos, IAM etc.) não são cenários com suporte.</span><span class="sxs-lookup"><span data-stu-id="2f80b-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="2f80b-116">Para cenários e solicitações adicionais sem suporte da Comunidade, consulte o fórum do UserVoice para contêineres do Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="2f80b-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2f80b-117">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2f80b-117">Additional resources</span></span>

- <span data-ttu-id="2f80b-118">**Máquinas virtuais e contêineres no Azure**</span><span class="sxs-lookup"><span data-stu-id="2f80b-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="2f80b-119">[Anterior](deploy-existing-net-apps-as-windows-containers.md)
> [Próximo](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="2f80b-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
