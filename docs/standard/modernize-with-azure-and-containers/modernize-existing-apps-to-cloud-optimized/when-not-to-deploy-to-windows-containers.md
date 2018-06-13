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
# <a name="when-not-to-deploy-to-windows-containers"></a>Quando não implantar contêineres do Windows

Algumas tecnologias do Windows não são suportadas pelos contêineres do Windows. Nesses casos, você ainda precisa migrar para VMs de padrões, geralmente com apenas o Windows e o IIS.

Casos não tem suportados em contêineres do Windows, a partir de maio de 2018: 

-   Serviço de enfileiramento de mensagens da Microsoft (MSMQ) atualmente está disponível apenas em contêineres do Windows com base na versão do Windows Server v1803, mas não em outras versões anteriores. 

    -   [Fórum de solicitação do UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [Fórum de discussão](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft Distributed Transaction coordenador (MSDTC) atualmente não tem suporte em contêineres do Windows.

    -   [Problema do GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office atualmente não dá suporte contêineres.

    -   [Fórum de solicitação do UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   Aplicativos de interface do usuário (aplicativos de cliente com uma interface do usuário visual) não são cenários com suporte.

-   Funções de infraestrutura do Windows (DNS, DHCP, DC, NTP, impressão, servidor de arquivos, etc. IAM) não são cenários com suporte.


Para cenários adicionais não suportada e solicitações da comunidade, consulte o fórum do UserVoice para contêineres do Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Recursos adicionais

-   **Máquinas virtuais e contêineres no Azure**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[Anterior](deploy-existing-net-apps-as-windows-containers.md)
[Próximo](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
