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
# <a name="when-not-to-deploy-to-windows-containers"></a>Quando não implantar Contêineres do Windows

Algumas tecnologias do Windows não são suportadas pelo Windows Containers. Nesses casos, você ainda precisa migrar para os padrões de VMs, geralmente apenas com Windows e IIS.

Casos não suportados em contêineres windows, a partir de maio de 2018:

- Atualmente, o Microsoft Message Queuing (MSMQ) só está disponível em contêineres do Windows com base na versão v1803 do Windows Server, mas não em outras versões anteriores.

  - [Fórum de solicitação de uservoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Fórum de discussão](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- O Microsoft Distributed Transaction Coordinator (MSDTC) atualmente não é suportado em contêineres do Windows.

  - [Problema do GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Atualmente, o Microsoft Office não suporta contêineres.

  - [Fórum de solicitação de uservoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Aplicativos de interface do usuário (aplicativos clientes com interface de usuário visual) não são cenários suportados.

- As funções de infra-estrutura do Windows (DNS, DHCP, DC, NTP, PRINT, Servidor de arquivos, IAM etc.) não são cenários suportados.

Para obter cenários e solicitações adicionais não suportados da comunidade, <https://windowsserver.uservoice.com/forums/304624-containers>consulte o fórum UserVoice para contêineres windows: .

### <a name="additional-resources"></a>Recursos adicionais

- **Máquinas virtuais e contêineres no Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Próximo](deploy-existing-net-apps-as-windows-containers.md)
> [anterior](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
