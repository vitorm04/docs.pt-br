---
title: Quando não implantar Contêineres do Windows
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Quando não implantar para contêineres do Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: c5d8f50c7b9967eba0ec01c9e864a02b6a3b201a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012003"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Quando não implantar Contêineres do Windows

Algumas tecnologias do Windows não têm suporte pelos contêineres do Windows. Nesses casos, você ainda precisará migrar para VMs de padrões, geralmente com apenas o Windows e o IIS.

Casos de não tem suportados em contêineres do Windows, a partir de maio de 2018:

- Microsoft Message Queuing (MSMQ) atualmente só está disponível em contêineres do Windows com base na versão do Windows Server v1803, mas não em outras versões anteriores.

  - [Fórum de solicitação do UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Fórum de discussão](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft Distributed Transaction coordenador (MSDTC) atualmente não tem suporte em contêineres do Windows.

  - [Problema do GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office atualmente não dão suporte a contêineres.

  - [Fórum de solicitação do UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Aplicativos de interface do usuário (aplicativos de cliente com uma interface do usuário visual) não são cenários com suporte.

- Funções de infraestrutura do Windows (DNS, DHCP, DC, NTP, impressão, servidor de arquivos, etc. IAM) não são os cenários com suporte.

Para solicitações da comunidade e outros cenários sem suporte, consulte o fórum do UserVoice para contêineres do Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Recursos adicionais

- **Máquinas virtuais e contêineres no Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Anterior](deploy-existing-net-apps-as-windows-containers.md)
> [Próximo](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
