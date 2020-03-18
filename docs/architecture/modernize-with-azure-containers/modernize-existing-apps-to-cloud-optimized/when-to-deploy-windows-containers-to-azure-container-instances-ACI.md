---
title: Quando implantar os contêineres do Windows em ACI (ACI)
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Quando implantar os contêineres do Windows em ACI (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577929"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Quando implantar os contêineres do Windows em ACI (ACI)

A principal proposta de valor do Azure Container Instances é que você pode implantar os contêineres imediatamente nele e não precisa manter esse ambiente, você não precisa atualizar/corrigir o sistema operacional ou VMs subjacentes, tudo isso é transparente e você simplesmente implanta contêineres em um ambiente pronto para uso.

As razões e cenários em que você gostaria de usar a ACI são semelhantes aos principais cenários quando você usa VMs do Azure com contêineres, então, basicamente, os principais cenários para usar o Azure Container Instances são:

- **Cenários de dev/teste**
- **Automação de tarefas**
- **Agentes de CI/CD**
- **Processamento de lotes em pequena escala**
- **Aplicativos web simples**

O cenário simples de aplicativos web é um cenário justo para a ACI, mas leve em conta que, como na ACI você só pode ter uma única instância de contêiner por imagem de contêiner, você não terá alta disponibilidade e só terá escalabilidade limitada.

No entanto, mesmo quando a ACI é considerada infra-estrutura porque apenas fornece instâncias de contêiner únicos, há um enorme benefício em comparação com as VMs azure regulares com o Windows Server. Com a ACI, basta implantar os contêineres em um ambiente auto-conservado e você só paga por esses contêineres. Você não precisa manter/atualizar/patch VMs, por isso é uma plataforma muito melhor para a maioria dos cenários onde você pode estar usando VMs com contêineres. O uso da ACI é direto, basta implantar um contêiner, não há necessidade de criar um ambiente de VM que você apenas implanta contêineres.

Os principais benefícios da Azure Container Instances (ACI) são:

- Executar contêineres sem gerenciar servidores
- Aumente a agilidade com contêineres demanda
- Implante contêineres na nuvem com simplicidade e velocidade sem precedentes — com um único comando.
- Aplicações seguras com isolamento de hipervisor

Em suma, com a ACI você pode desenvolver aplicativos rapidamente sem gerenciar máquinas virtuais ou ter que aprender novas ferramentas. É só sua aplicação, em um contêiner, correndo na nuvem.

> [!div class="step-by-step"]
> [Próximo](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
