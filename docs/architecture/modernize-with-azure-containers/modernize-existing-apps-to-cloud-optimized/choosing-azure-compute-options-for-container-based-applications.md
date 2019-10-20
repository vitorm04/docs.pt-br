---
title: Escolher plataformas de computação do Azure para aplicativos baseados em contêiner
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Escolhendo plataformas de computação do Azure para aplicativos baseados em contêiner
ms.date: 05/04/2018
ms.openlocfilehash: 2262d2cf4e69e19e8b78c07c239602dd5dccc3cd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318675"
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

Na Figura 1, você pode ver uma análise de diferentes tipos de aplicativos e seus cenários de hospedagem do Azure ideais.

![Figura 1](./media/image8.5.png)

> [!div class="step-by-step"]
> [Anterior](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Próximo](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
