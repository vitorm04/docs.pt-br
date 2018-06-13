---
title: Escolha as plataformas de computação do Azure para aplicativos baseados no contêiner
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Escolha as plataformas de computação do Azure para aplicativos baseados no contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958006"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Escolha as plataformas de computação do Azure para aplicativos baseados no contêiner

Como você pode ter observado depois de ler as seções anteriores, o Azure é uma nuvem aberta que oferece várias opções. Você pode usar o mais adequado às suas necessidades, no entanto, ele também dá superfície a perguntas sobre o que você deve usar para seus aplicativos em contêineres de produto/tecnologia.

Como um *por padrão* recomendação, o seguinte é o critério principal recomendado neste guia:

  - **Único aplicativo monolítico:** escolher serviço de aplicativo do Azure
  - **Aplicativo de N camadas:** escolha orchestrators como Azure Kubernetes serviço (AKS), serviço de malha (SF) ou do serviço de aplicativo, se você tiver uma única ou alguns serviços de back-end
  - **Linux microservices:** AKS/Kubernetes escolha
  - **Windows microservices:** escolha Service Fabric
  - **Funções sem servidor e manipuladores de eventos:** escolher funções do Azure
  - **Lotes em larga escala:** escolha lote do Azure

No entanto, essa recomendação deve ser usada com um pouco de sal, como a seleção do produto depende necessidades de seu aplicativo específico e características. Nem todos os aplicativos são as mesmas mesmo quando inicialmente tipos semelhantes podem ser exibidas.

Depois de uma análise mais profunda das necessidades do aplicativo, o produto selecionado pode ser diferente. Mas, como um ponto de partida, é recomendável diretrizes inicial da onde você pode iniciar a avaliação e teste com base em determinada prioridade.

A figura a seguir, você pode analisar mais global enquanto a tabela de decisões detalhadas.

![](./media/image8.5.png)

Observe como a base do sistema operacional (Windows vs. Linux) também pode ser um fator de decisão, assim como alguns orchestrators mais maduro em contêineres do Linux e outros em contêineres do Windows. Por exemplo, contêineres do Linux são maduros em Kubernetes (AKS no Azure) mas menos maduro na malha do serviço. Por outro lado, os contêineres do Windows são menos maduro em AKS e mais maduro na malha do serviço (lançado em maio de 2017).

No entanto, essas diferenças no vencimento do sistema operacional serão desaparecer no futuro e várias plataformas terá maturidade comparável do sistema operacional e a decisão será apresentar mais informações sobre preferências com base em recursos específicos do seu aplicativo, talvez seja necessário ou com base no ecossistema de cada plataforma motivos.


>[!div class="step-by-step"]
[Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
