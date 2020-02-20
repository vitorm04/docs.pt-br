---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503865"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Escolher plataformas de computação do Azure para aplicativos baseados em contêiner

Como você observou depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções. No entanto, você pode usar a melhor opção para atender às suas necessidades. ele também mostra perguntas sobre qual produto/tecnologia você deve usar para seus aplicativos em contêineres.

Como uma recomendação *por padrão* , estes são os principais critérios recomendados nestas diretrizes:

- **Aplicativo monolítico único:** Escolher serviço de Azure App
- **Aplicativo de N camadas:** Escolha orquestradores como o AKS (serviço de kubernetes do Azure) ou serviço de aplicativo se você tiver um único ou alguns serviços de back-end
- **Microserviços:** Escolher AKS ou aplicativos Web do Azure para contêineres
- **Funções sem servidor & manipuladores de eventos:** Escolha Azure Functions
- **Lote em larga escala:** Escolher lote do Azure

No entanto, essa recomendação deve ser tomada com um pinça de Salt, pois a seleção do produto dependerá de suas necessidades e características específicas do seu aplicativo. Nem todos os aplicativos são os mesmos mesmo quando inicialmente podem parecer tipos semelhantes.

Após uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente. Mas, como ponto de partida, é bom ter diretrizes iniciais de onde você pode começar a avaliar e testar com base em determinada prioridade.

Na tabela a seguir, você pode ver uma análise de diferentes tipos de aplicativos e seus cenários de hospedagem do Azure possíveis e recomendados.

| Arquitetura de aplicativo | VMs-máquinas virtuais do Azure | ACI-instâncias de contêiner do Azure | Serviço de Azure App (contêineres w-w/o) | AKS – serviços Kubernetess do Azure | Funções do Azure | Lote do Azure |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Aplicativos Web (monolítico)**         | ![Possível com VMs](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recomendado com o serviço de aplicativo](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Possível com AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **Aplicativos de N camadas (serviços)**        | ![Possível com VMs](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recomendado com o serviço de aplicativo](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Possível com AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com o Azure fuctions](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Nativa na nuvem (microserviços)**  | | ![Possível com ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Recomendado com AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Contêineres de&nbsp;do Linux)| ![Recomendado com Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Controlado&#x2011;por evento) | |
| **Lote/trabalhos (tarefas em segundo plano)** | ![Possível com VMs](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com o serviço de aplicativo](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possível com AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recomendado com Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Tarefas de&nbsp;em segundo plano) | ![Recomendado com o lote do Azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Grande&#x2011;escala) |

**Legenda**

![Ícone recomendado](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Aconselhável
![Ícone possível](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Possível

> [!div class="step-by-step"]
> [Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
