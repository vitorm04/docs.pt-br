---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
ms.date: 05/04/2018
ms.openlocfilehash: 28e103c67f47d63582384c9ab468a5f631b5ce9e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638990"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Escolher plataformas de computação do Azure para aplicativos baseados em contêiner

Como você pode ter notado depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções. Você pode usar o mais adequado para suas necessidades, no entanto, ele também dá superfície a perguntas sobre o que você deve usar para seus aplicativos em contêineres de produto/tecnologia.

Como uma *por padrão* recomendação, o seguinte é o critério principal recomendado neste guia:

- **Aplicativo monolítico único:** Escolha o serviço de aplicativo do Azure
- **Aplicativo de N camadas:** Escolha orquestradores como serviço de Kubernetes do Azure (AKS), o Service Fabric (SF) ou o serviço de aplicativo, se você tiver uma única ou alguns serviços de back-end
- **Microsserviços do Linux:** Escolha o AKS/Kubernetes
- **Microsserviços do Windows:** Escolha Service Fabric
- **Funções sem servidor e manipuladores de eventos:** Escolha o Azure Functions
- **Em grande escala em lote:** Escolha o lote do Azure

No entanto, essa recomendação deve ser usada com uma situação de emergência de sal, como a seleção do produto depende necessidades de seu aplicativo específico e características. Nem todos os aplicativos são os mesmos, mesmo quando inicialmente, elas podem parecer similares.

Depois de uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente. Mas, como ponto de partida, é bom ter diretrizes iniciais de onde você pode começar a avaliar e teste com base na prioridade de determinados.

Na figura a seguir, você pode analisar mais global enquanto a tabela de decisões detalhadas.

![](./media/image8.5.png)

Observe como a base do sistema operacional (Windows vs. Linux) também pode ser um fator de decisão conforme alguns orquestradores são mais maduro em contêineres do Linux e outros em contêineres do Windows. Por exemplo, os contêineres do Linux são muito maduros no Kubernetes (AKS no Azure), mas menos maduro no Service Fabric. Por outro lado, contêineres do Windows são mais maduro no Service Fabric (lançado em maio de 2017) e menos maduro no AKS.

No entanto, essas diferenças em maturidade do sistema operacional serão fade in no futuro e várias plataformas terão comparáveis maturidade do sistema operacional e a decisão definirá o layout mais nas preferências com base em recursos específicos do seu aplicativo, talvez seja necessário ou com base no ecossistema de cada plataforma motivos.

> [!div class="step-by-step"]
> [Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
