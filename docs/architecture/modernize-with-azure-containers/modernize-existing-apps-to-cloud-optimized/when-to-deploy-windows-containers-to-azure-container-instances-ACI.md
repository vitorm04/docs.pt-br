---
title: Quando implantar contêineres do Windows em ACI (instâncias de contêiner do Azure)
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Quando implantar contêineres do Windows em ACI (instâncias de contêiner do Azure)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577929"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Quando implantar contêineres do Windows em ACI (instâncias de contêiner do Azure)

A principal proposta de valor das instâncias de contêiner do Azure é que você pode imediatamente implantar contêineres nela e não precisa manter esse ambiente, você não precisa atualizar/aplicar patch ao sistema operacional ou às VMs subjacentes, tudo isso é transparente e apenas implantar contêineres em um ambiente pronto para uso.

Os motivos e cenários em que você desejaria usar o ACI são semelhantes aos principais cenários quando você usa VMs do Azure com contêineres, portanto, basicamente, os principais cenários para usar as instâncias de contêiner do Azure são:

- **Cenários de desenvolvimento/teste**
- **Automação de tarefas**
- **Agentes de CI/CD**
- **Processamento em lotes de pequena/escala**
- **Aplicativos Web simples**

O cenário de aplicativos Web simples é um cenário justo para ACI, mas leve em conta que, desde o ACI, você só pode ter uma única instância de contêiner por imagem de contêiner, não terá alta disponibilidade e terá apenas escalabilidade limitada.

No entanto, mesmo quando o ACI é considerado uma infraestrutura porque ele apenas fornece instâncias de contêiner único, há um grande benefício em comparação com as VMs regulares do Azure com o Windows Server. Com o ACI, você apenas implanta os contêineres em um ambiente automantido e só paga por esses contêineres. Você não precisa manter/atualizar/corrigir VMs, portanto é uma plataforma muito melhor para a maioria dos cenários em que você pode estar usando VMs com contêineres. Usar o ACI é um avanço direto, você simplesmente implanta um contêiner, não há necessidade de criar um ambiente de VM que você apenas implante contêineres.

Os principais benefícios das ACI (instâncias de contêiner do Azure) são:

- Executar contêineres sem gerenciar servidores
- Aumentar a agilidade com contêineres sob demanda
- Implante contêineres na nuvem com simplicidade e velocidade sem precedentes, com um único comando.
- Proteger aplicativos com isolamento de hipervisor

Em suma, com o ACI, você pode desenvolver aplicativos rapidamente sem gerenciar máquinas virtuais ou ter que aprender novas ferramentas. É apenas seu aplicativo, em um contêiner, em execução na nuvem.

> [!div class="step-by-step"]
> [Anterior](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [Próximo](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
