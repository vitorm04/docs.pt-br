---
title: Quando implantar Contêineres do Windows para VMs do Azure (nuvem de IaaS)
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Quando implantar os Contêineres do Windows em VMs do Azure (nuvem IaaS)
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577899"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Quando implantar Contêineres do Windows para VMs do Azure (nuvem de IaaS)

Se sua organização estiver usando VMs do Azure, mesmo que você também esteja usando o Windows Containers, você ainda está lidando com IaaS. Isso significa que lidar com operações de infra-estrutura, patches de SO VM e complexidade de infra-estrutura para aplicativos altamente escaláveis quando você precisa implantar em várias VMs em uma infra-estrutura equilibrada de carga. Os principais cenários para usar os contêineres do Windows em uma VM Azure são:

- **Ambiente de desenvolvimento/teste**: Um VM na nuvem é perfeito para desenvolvimento e testes na nuvem. Você pode criar ou parar rapidamente o ambiente dependendo de suas necessidades.

- **Pequenas e médias necessidades de escalabilidade**: Em cenários onde você pode precisar apenas de um par de VMs para o seu ambiente de produção, gerenciar um pequeno número de VMs pode ser acessível até que você possa se mover para ambientes PaaS mais avançados, como orquestradores.

- **Ambiente de produção com ferramentas de implantação existentes**: Você pode estar se movendo de um ambiente local no qual você investiu em ferramentas para fazer implantações complexas em VMs ou servidores de metal nu (como Puppet ou ferramentas similares). Para passar para a nuvem com alterações mínimas nos procedimentos de implantação do ambiente de produção, você pode continuar a usar essas ferramentas para implantar em VMs do Azure. No entanto, você vai querer usar o Windows Containers como a unidade de implantação para melhorar a experiência de implantação.

>[!div class="step-by-step"]
>[Próximo](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[anterior](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
