---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêineres
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503865"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Escolher plataformas de computação do Azure para aplicativos baseados em contêiner

Como você notou depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece múltiplas opções. Você pode usar o melhor ajuste para suas necessidades, no entanto, ele também surge questões sobre qual produto/tecnologia você deve usar para suas aplicações conteificadas.

Como recomendação *por padrão,* os principais critérios recomendados nesta orientação são:

- **Único aplicativo monolítico:** Escolha o serviço de aplicativos do Azure
- **Aplicativo N-Tier:** Escolha orquestradores como o Azure Kubernetes Service (AKS) ou o App Service se você tiver um único ou alguns serviços back-end
- **Microserviços:** Escolha aplicativos AKS ou Web do Azure para contêineres
- **Funções sem servidor & manipuladores de eventos:** Escolha funções do Azure
- **Lote em larga escala:** Escolha o lote azure

No entanto, essa recomendação deve ser tomada com uma pitada de sal, pois a seleção do produto dependerá das necessidades e características específicas da sua aplicação específica. Nem todos os aplicativos são iguais mesmo quando inicialmente podem parecer tipos semelhantes.

Após uma análise mais profunda das necessidades do aplicativo, o produto selecionado poderia ser diferente. Mas, como ponto de partida, é bom ter orientação inicial de onde você pode começar a avaliar e testar com base em determinada prioridade.

Na tabela a seguir, você pode ver um detalhamento de diferentes tipos de aplicativos e seus possíveis e recomendados cenários de hospedagem do Azure.

| Arquitetura de aplicativo | VMs - Azure Virtual Machines | ACI - Azure Container Instances | Serviço de aplicativo Azure (contêineres w-w/o) | AKS - Azure Kubernetes Services | Funções do Azure | Lote do Azure |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Aplicativos web (Monolíticos)**         | ![Possível com VMs](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recomendado com serviço de aplicativo](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Possível com AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **Aplicativos n-tier (Serviços)**        | ![Possível com VMs](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recomendado com serviço de aplicativo](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Possível com AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com Fuctions Azure](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Nativo da Nuvem (Microserviços)**  | | ![Possível com ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Recomendado com AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Contêineres Linux)&nbsp;| ![Recomendado com funções azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (&#x2011;de eventos) | |
| **Lote/Trabalhos (tarefas em segundo plano)** | ![Possível com VMs](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com serviço de aplicativo](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recomendado com funções azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Tarefas de fundo)&nbsp; | ![Recomendado com lote Azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Grande escala&#x2011;) |

**Lenda**

![Ícone recomendado](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Recomendado \
![Possível ícone](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Possível

> [!div class="step-by-step"]
> [Próximo](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [anterior](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
