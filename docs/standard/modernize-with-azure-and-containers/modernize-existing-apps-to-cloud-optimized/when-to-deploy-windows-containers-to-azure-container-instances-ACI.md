---
title: Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957946"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Quando implantar contêineres do Windows para instâncias de contêiner do Azure (ACI)

Instâncias de contêiner do Azure proposta de valor principal é que você pode implantar imediatamente contêineres a ele e você não precisa manter o ambiente, você não precisa atualização/patch do sistema de operacional de subjacentes ou VMs, tudo isso é transparente e você acabou de implantar contêineres em um ambiente pronto para uso.

As razões e os cenários nos quais você deseja usar ACI são semelhantes para os cenários principais ao usar máquinas virtuais do Azure com contêineres, basicamente, os cenários principais para usar instâncias de contêiner do Azure são:

-   **Cenários de desenvolvimento/teste**
-   **Automação de tarefas**
-   **Agentes de CI/CD**
-   **Processamento em lotes de pequeno ou escala.**
-   **Aplicativos da web simples**

O cenário de aplicativos da web simples é um cenário razoável para ACI mas levar em conta que desde ACI você só pode ter uma instância única de contêiner por imagem de contêiner, você não tem alta disponibilidade e só possui escalabilidade limitada.

No entanto, mesmo quando ACI é considerado infraestrutura porque ele fornece apenas instâncias de contêiner único, há um grande benefício comparado para regular VMs do Azure com o Windows Server. Com ACI, implantar apenas os contêineres em um ambiente automantido e pague apenas esses contêineres. Você não precisa manter/atualização/patch VMs, portanto, é uma plataforma melhor para a maioria dos cenários em que talvez você esteja usando máquinas virtuais com contêineres. Usar ACI é simples e prático, você implantar apenas um contêiner, não é necessário para criar um ambiente de VM que você implanta apenas os contêineres.

Os principais benefícios de instâncias de contêiner do Azure (ACI) são:

-   Executar contêineres sem gerenciar servidores
-   Aumentar a agilidade com contêineres sob demanda
-   Implantar contêineres para a nuvem com simplicidade precedentes e velocidade, com um único comando. 
-   Proteger aplicativos com o isolamento do hipervisor

Em resumo, com ACI, você pode desenvolver aplicativos sem gerenciamento de máquinas virtuais ou a necessidade de aprender novas ferramentas. É apenas o aplicativo em um contêiner em execução na nuvem.

>[!div class="step-by-step"]
[Anterior](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Próximo](when-to-deploy-windows-containers-to-service-fabric.md)
