---
title: Quando implantar Contêineres do Windows para VMs do Azure (nuvem de IaaS)
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para VMs do Azure (nuvem de IaaS)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 51217e2c94fd9727c8f7907e791cdebaec98f14f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011951"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Quando implantar Contêineres do Windows para VMs do Azure (nuvem de IaaS)

Se sua organização estiver usando VMs do Azure, mesmo se você também estiver usando contêineres do Windows, você ainda estiver lidando com IaaS. Isso significa que lidar com operações de infraestrutura, patches de SO da VM e complexidade da infraestrutura para aplicativos altamente escalonáveis, quando você precisa implantar várias VMs em uma infraestrutura com balanceamento de carga. Os cenários principais para usar contêineres do Windows em uma VM do Azure são:

- **Ambiente de desenvolvimento/teste**: Uma VM na nuvem é perfeita para desenvolvimento e teste na nuvem. Você pode rapidamente criar ou parar o ambiente, dependendo das suas necessidades.

- **Precisa de escalabilidade de pequena e média**: Em cenários em que talvez sejam necessárias duas VMs para seu ambiente de produção, gerenciando uma pequena quantidade de VMs pode ser acessível até que você pode mover para ambientes de PaaS mais avançados, como orquestradores.

- **Ambiente de produção com as ferramentas de implantação existentes**: Você pode estar movendo de um ambiente local na qual você investiu nas ferramentas para fazer implantações complexas em VMs ou servidores bare-metal (como o Puppet ou ferramentas semelhantes). Para mover para a nuvem com alterações mínimas aos procedimentos de implantação do ambiente de produção, você pode continuar a usar essas ferramentas para implantar em VMs do Azure. No entanto, você desejará usar contêineres do Windows como a unidade de implantação para melhorar a experiência de implantação.

>[!div class="step-by-step"]
>[Anterior](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[Próximo](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)