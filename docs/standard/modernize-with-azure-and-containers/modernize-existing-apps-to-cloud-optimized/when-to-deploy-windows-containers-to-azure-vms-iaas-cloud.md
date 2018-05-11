---
title: Quando implantar contêineres do Windows para VMs do Azure (IaaS nuvem)
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para VMs do Azure (IaaS nuvem)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 7472745577f414062b460fd71ab45bae85d7a62e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Quando implantar contêineres do Windows para VMs do Azure (IaaS nuvem)

Se sua organização estiver usando máquinas virtuais do Azure, mesmo se você também estiver usando contêineres do Windows, você ainda está lidando com IaaS. Isso significa que lidar com operações de infra-estrutura, patches do sistema operacional da VM e a complexidade de infraestrutura para aplicativos altamente escalonáveis quando você precisa implantar várias VMs em uma infraestrutura com balanceamento de carga. Os cenários principais para usar contêineres do Windows em uma VM do Azure são:

-   **Ambiente de desenvolvimento/teste**: uma VM na nuvem é perfeita para desenvolvimento e teste na nuvem. Você pode rapidamente criar ou parar o ambiente dependendo de suas necessidades.

-   **Precisa de escalabilidade de pequena e média**: em cenários onde você pode precisar apenas algumas das VMs de seu ambiente de produção, Gerenciando um pequeno número de VMs pode estar acessível até que você pode mover para ambientes de PaaS mais avançadas, como orchestrators.

-   **Ambiente de produção com as ferramentas de implantação existentes**: você pode mover de um ambiente local em que você investiu nas ferramentas de fazer implantações complexas VMs ou bare-metal servidores (como Puppet ou ferramentas semelhantes). Para mover para a nuvem com mínimas alterações para procedimentos de implantação do ambiente de produção, você pode continuar a usar essas ferramentas para implantar máquinas virtuais do Azure. No entanto, você desejará usar contêineres do Windows como a unidade de implantação para melhorar a experiência de implantação.

>[!div class="step-by-step"]
[Anterior](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Próximo](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
