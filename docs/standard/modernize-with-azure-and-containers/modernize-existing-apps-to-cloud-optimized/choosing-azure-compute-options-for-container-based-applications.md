---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
ms.date: 05/04/2018
ms.openlocfilehash: d91cd279402dc24beb5f766c06cb85ac8d74f482
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758813"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Escolher plataformas de computação do Azure para aplicativos baseados em contêiner

Como você pode ter notado depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções. Você pode usar o mais adequado para suas necessidades, no entanto, ele também dá superfície a perguntas sobre o que você deve usar para seus aplicativos em contêineres de produto/tecnologia.

Como uma *por padrão* recomendação, o seguinte é o critério principal recomendado neste guia:

- **Aplicativo monolítico único:** Escolha o serviço de aplicativo do Azure
- **Aplicativo de N camadas:** Escolha orquestradores, como o serviço de aplicativo ou serviço de Kubernetes do Azure (AKS) se você tiver uma única ou alguns serviços de back-end
- **Microsserviços do Linux:** Escolha o AKS/Kubernetes
- **Microsserviços do Windows:** Escolher aplicativos Web do Azure para contêineres
- **Funções sem servidor e manipuladores de eventos:** Escolha o Azure Functions
- **Em grande escala em lote:** Escolha o lote do Azure

No entanto, essa recomendação deve ser usada com uma situação de emergência de sal, como a seleção do produto depende necessidades de seu aplicativo específico e características. Nem todos os aplicativos são os mesmos, mesmo quando inicialmente, elas podem parecer similares.

Depois de uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente. Mas, como ponto de partida, é bom ter diretrizes iniciais de onde você pode começar a avaliar e teste com base na prioridade de determinados.

Na figura a seguir, você pode ver uma divisão dos diferentes tipos de aplicativos e seus ideal do Azure em cenários de hospedagem.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
