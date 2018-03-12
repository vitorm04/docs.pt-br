---
title: "Quando não implantar contêineres do Windows"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Quando não implantar contêineres do Windows"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cb671ec88da7ff1aa5c960c210e0da5e9d753280
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Quando não implantar contêineres do Windows

Algumas tecnologias do Windows não são suportadas pelos contêineres do Windows. Nesses casos, você ainda precisa migrar para VMs de padrões, geralmente com apenas o Windows e o IIS.

Casos não tem suportados em contêineres do Windows, a partir de meados de 2017:

-   Serviço de enfileiramento de mensagens da Microsoft (MSMQ) atualmente não tem suporte em contêineres do Windows.

    -   [Fórum de solicitação do UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [Fórum de discussão](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft Distributed Transaction coordenador (MSDTC) atualmente não tem suporte em contêineres do Windows

    -   [Problema do GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office não oferece suporte a contêineres

    -   [Fórum de solicitação do UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

Para cenários adicionais não suportada e solicitações da comunidade, consulte o fórum do UserVoice para contêineres do Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Recursos adicionais

-   **Máquinas virtuais e contêineres no Azure**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[Anterior](deploy-existing-net-apps-as-windows-containers.md)
[Próximo](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
